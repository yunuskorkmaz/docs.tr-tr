---
title: .NET core ek araçlar
description: Destekleyen ve .NET Core işlevselliğini genişleten ek araçlar genel bakış.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: c64dddbe36b789a695c2603e78b29b38d8718f95
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208389"
---
# <a name="net-core-additional-tools"></a>.NET core ek araçlar

Bu bölümde destekler ve ek olarak .NET Core işlevselliğini genişleten araçları listesini derler [.NET Core komut satırı arabirimi (CLI)](../tools/index.md) araçları.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web Service Reference aracı](wcf-web-service-reference-guide.md)

Kendi etkinliğinde içinde yapılan bir Visual Studio bağlı hizmet sağlayıcısı (Windows Communication Foundation) WCF Web servisi başvurusu olduğu [Visual Studio 2017 sürüm 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools). Bu araç, bir ağ konumu üzerinde mevcut çözümde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve web hizmet işlemlerini erişmek için kullanabileceğiniz yöntemleri ile WCF proxy sınıfı tanımlayan .NET Core ile uyumlu bir kaynak dosyası oluşturur.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet svcutil aracı](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) dotnet svcutil aracı, bir ağ konumu üzerinde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve bir WCF proxy sınıf yöntemleriyle tanımlama, .NET Core ile uyumlu bir kaynak dosyası oluşturur bir .NET Core CLI araçtır web hizmeti işlemleri erişmek için kullanabileceğiniz. **Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) Visual Studio bağlı hizmet sağlayıcısı hangi ilk sevk edilen Visual Studio ile 2017 v15.5. **Dotnet svcutil** aracı bir .NET Core CLI aracı, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serileştirici Oluşturucusu](xml-serializer-generator.md)

Gibi [Xml seri hale getirici oluşturucunun (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketini](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET standart kitaplıkları çözümüdür. Bir XML serileştirme derleme türleri serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede yer alan oluşturur <xref:System.Xml.Serialization.XmlSerializer>.