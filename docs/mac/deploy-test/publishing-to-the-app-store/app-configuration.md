---
title: Configuración de aplicaciones de Mac
description: En este documento se describe el proceso de configuración de una aplicación Xamarin.Mac para su publicación. Se trata también la configuración de la aplicación, de la firma y de la compilación.
ms.prod: xamarin
ms.assetid: fea66a34-1581-4cd6-b714-3fbff215a542
ms.technology: xamarin-mac
author: bradumbaugh
ms.author: brumbaug
ms.date: 04/12/2017
ms.openlocfilehash: 3d62cd0c5391393773ba32146f576e12a144bac9
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34791789"
---
# <a name="mac-app-configuration"></a>Configuración de aplicaciones de Mac

## <a name="mac-app-configuration"></a>Configuración de aplicaciones de Mac

Haga doble clic en el proyecto de la aplicación de Mac en Visual Studio para Mac y elija **Opciones**.

### <a name="application-settings"></a>Configuración de la aplicación

Para cambiar la configuración de la aplicación de una aplicación de Xamarin.Mac, haga doble clic en el archivo **Info.plist** en el **Panel de solución**:

![Seleccionar el archivo info.plist](app-configuration-images/config04.png "Seleccionar el archivo info.plist")

Esto mostrará las opciones disponibles para la aplicación:

 [![Modificar el archivo info.plist](app-configuration-images/config01.png "Modificar el archivo info.plist")](app-configuration-images/config01-large.png#lightbox)

La ejecución de aplicaciones de Mac creadas con Xamarin.Mac tiene los siguientes requisitos del sistema:

- Un equipo Mac que ejecute Mac OS X 10.7 o una versión posterior.

### <a name="signing-settings"></a>Configuración de firma

La sección **Firma de Mac** del cuadro de diálogo **Opciones de proyecto** permite al desarrollador firmar una aplicación de Xamarin.Mac para las pruebas, para autopublicación o para publicación a través del App Store de Apple:

[![El editor de la firma de Mac](app-configuration-images/config02.png "El editor de la firma de Mac")](app-configuration-images/config02-large.png#lightbox)

Desde aquí seleccione la identidad, el perfil de aprovisionamiento y cualquier derecho personalizado utilizado para firmar la aplicación cuando se compila. Opcionalmente, el desarrollador puede firmar el instalador usado para instalar la aplicación en otro equipo Mac.

### <a name="build-settings"></a>Configuración de compilación

La sección **Compilación de Mac** del cuadro de diálogo **Opciones de proyecto** permite al desarrollador seleccionar la arquitectura para una aplicación de Xamarin.Mac, para controlar qué versión de macOS será compatible con la aplicación y crear un paquete de instalación si la aplicación se compila correctamente:

 [![Modificar la configuración de compilación](app-configuration-images/config03.png "Modificar la configuración de compilación")](app-configuration-images/config03-large.png#lightbox)

## <a name="related-links"></a>Vínculos relacionados

- [Instalación](/visualstudio/mac/installation/)
- [Ejemplo de Hello, Mac](~/mac/get-started/hello-mac.md)
- [Distribuir las aplicaciones en Mac App Store](https://developer.apple.com/devcenter/mac/checklist/)
- [Identificador del desarrollador y equipo selector](https://developer.apple.com/resources/developer-id/)
