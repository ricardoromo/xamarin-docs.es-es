---
title: Perfil de usuario
ms.prod: xamarin
ms.assetid: 6BB01F75-5E98-49A1-BBA0-C2680905C59D
ms.technology: xamarin-android
author: mgmclemore
ms.author: mamcle
ms.date: 03/22/2018
ms.openlocfilehash: 1eaae86ab9eacf007eca792d96e889db6f367922
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2018
ms.locfileid: "30765511"
---
# <a name="user-profile"></a>Perfil de usuario

Android admitió enumerar contactos con la [ContactsContract](https://developer.xamarin.com/api/type/Android.Provider.ContactsContract/) proveedor desde el 5 de nivel de API. Por ejemplo, la lista de contactos es tan simple como utilizar el [ContactContracts.Contacts](https://developer.xamarin.com/api/type/Android.Provider.ContactsContract+Contacts/) clase tal como se muestra en el ejemplo de código siguiente:

```csharp
// Get the URI for the user's contacts:
var uri = ContactsContract.Contacts.ContentUri;

// Setup the "projection" (columns we want) for only the ID and display name:
string[] projection = {
    ContactsContract.Contacts.InterfaceConsts.Id, 
    ContactsContract.Contacts.InterfaceConsts.DisplayName };

// Use a CursorLoader to retrieve the user's contacts data:
CursorLoader loader = new CursorLoader(this, uri, projection, null, null, null);
ICursor cursor = (ICursor)loader.LoadInBackground();

// Print the contact data to the console if reading back succeeds:
if (cursor != null)
{
    if (cursor.MoveToFirst())
    {
        do
        {
            Console.WriteLine("Contact ID: {0}, Contact Name: {1}",
                               cursor.GetString(cursor.GetColumnIndex(projection[0])),
                               cursor.GetString(cursor.GetColumnIndex(projection[1])));
        } while (cursor.MoveToNext());
    }
}
```

Android 4 (API nivel 14), a partir del [ContactsContact.Profile](https://developer.xamarin.com/api/type/Android.Provider.ContactsContract+Profile/) clase está disponible a través de la `ContactsContract` proveedor. El `ContactsContact.Profile` proporciona acceso al perfil personal para el propietario de un dispositivo, lo que incluye datos de contacto, como del propietario del dispositivo nombre y número de teléfono.


## <a name="required-permissions"></a>Permisos necesarios

Para leer y escribir datos de contacto, las aplicaciones deben solicitar la `READ_CONTACTS` y `WRITE_CONTACTS` permisos, respectivamente.
Además, para leer y editar el perfil de usuario, las aplicaciones deben solicitar la `READ_PROFILE` y `WRITE_PROFILE` permisos.


## <a name="updating-profile-data"></a>Actualización de datos de perfil

Una vez que estos permisos se han establecido, una aplicación puede usar técnicas de Android normales para interactuar con los datos del perfil de usuario. Por ejemplo, para actualizar el nombre para mostrar del perfil, llame a [ContentResolver.Update](https://developer.xamarin.com/api/member/Android.Content.ContentResolver.Update) con un `Uri` recuperados a través de la [ContactsContract.Profile.ContentRawContactsUri](https://developer.xamarin.com/api/property/Android.Provider.ContactsContract+Profile.ContentRawContactsUri/) propiedad, como se muestra a continuación:

```csharp
var values = new ContentValues ();
values.Put (ContactsContract.Contacts.InterfaceConsts.DisplayName, "John Doe");

// Update the user profile with the name "John Doe":
ContentResolver.Update (ContactsContract.Profile.ContentRawContactsUri, values, null, null);
```

## <a name="reading-profile-data"></a>Leer datos de perfil

Emitir una consulta a la [ContactsContact.Profile.ContentUri](https://developer.xamarin.com/api/property/Android.Provider.ContactsContract+Profile.ContentUri/) lecturas realizar copias de los datos de perfil. Por ejemplo, el siguiente código leerá el nombre para mostrar del perfil de usuario:

```csharp
// Read the profile
var uri = ContactsContract.Profile.ContentUri;

// Setup the "projection" (column we want) for only the display name:
string[] projection = {
    ContactsContract.Contacts.InterfaceConsts.DisplayName };

// Use a CursorLoader to retrieve the data:
CursorLoader loader = new CursorLoader(this, uri, projection, null, null, null);
ICursor cursor = (ICursor)loader.LoadInBackground();
if (cursor != null)
{
    if (cursor.MoveToFirst ())
    {
        Console.WriteLine(cursor.GetString (cursor.GetColumnIndex (projection [0])));
    }
}
```

## <a name="navigating-to-the-user-profile"></a>Desplácese hasta el perfil de usuario

Por último, para navegar hasta el perfil de usuario, cree un intento con un `ActionView` acción y un `ContactsContract.Profile.ContentUri` , a continuación, páselo a la `StartActivity` método similar al siguiente:

```csharp
var intent = new Intent (Intent.ActionView,
    ContactsContract.Profile.ContentUri);           
StartActivity (intent);
```

Cuando se ejecuta el código anterior, se muestra el perfil de usuario, como se muestra en la siguiente captura de pantalla:

[![Captura de pantalla de perfil de mostrar el perfil de usuario de Juan García](user-profile-images/01-profile-screen-sml.png)](user-profile-images/01-profile-screen.png#lightbox)

Trabajar con el perfil de usuario es similar a la interacción con otros datos en Android, y ofrece un nivel adicional de personalización del dispositivo.



## <a name="related-links"></a>Vínculos relacionados

- [ContactsProviderDemo (ejemplo)](https://developer.xamarin.com/samples/monodroid/ContactsProviderDemo/)
- [Introducción a helado Sandwich](http://www.android.com/about/ice-cream-sandwich/)
- [Plataforma 4.0 Android](http://developer.android.com/sdk/android-4.0.html)
