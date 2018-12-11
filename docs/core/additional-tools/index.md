---
title: .NET core ek CLI araçları
description: Genel Bakış destekleyen ve .NET Core işlevselliğini genişleten ek araçlar yükleyebilirsiniz.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: seodec18
ms.openlocfilehash: 0fb04b65efa26de3f0db9b7f7c28cce01ad9df97
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169202"
---
# <a name="net-core-additional-tools-overview"></a>.NET core ek araçlar genel bakış

Bu bölümde destekler ve ek olarak .NET Core işlevselliğini genişleten araçları listesini derler [.NET Core komut satırı arabirimi (CLI)](../tools/index.md) araçları.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web Service Reference aracı](wcf-web-service-reference-guide.md)

Kendi etkinliğinde içinde yapılan bir Visual Studio bağlı hizmet sağlayıcısı (Windows Communication Foundation) WCF Web servisi başvurusu olduğu [Visual Studio 2017 sürüm 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools). Bu araç, bir ağ konumu üzerinde mevcut çözümde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve web hizmet işlemlerini erişmek için kullanabileceğiniz yöntemleri ile WCF proxy sınıfı tanımlayan .NET Core ile uyumlu bir kaynak dosyası oluşturur.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet svcutil aracı](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) dotnet svcutil aracı, bir ağ konumu üzerinde bir web hizmetinden veya bir WSDL dosyasından meta verilerini alır ve bir WCF proxy sınıf yöntemleriyle tanımlama, .NET Core ile uyumlu bir kaynak dosyası oluşturur bir .NET Core CLI araçtır web hizmeti işlemleri erişmek için kullanabileceğiniz. **Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web Service Reference** ](wcf-web-service-reference-guide.md) Visual Studio bağlı hizmet sağlayıcısı hangi ilk sevk edilen Visual Studio ile 2017 v15.5. **Dotnet svcutil** aracı bir .NET Core CLI aracı, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF dotnet svcutil.xmlserializer aracı](dotnet-svcutil.xmlserializer-guide.md)

.NET Framework üzerinde svcutil Aracı'nı kullanarak bir serileştirme bütünleştirilmiş kodu önceden de oluşturabilirsiniz. Dotnet svcutil.xmlserializer NuGet paketi üzerinde .NET Core benzer bir işlevsellik sağlar. Başına-ürettiği C# WCF sözleşmesi tarafından kullanılır ve bu seri hale getirilemiyor tarafından türleri istemci uygulamasındaki için serileştirme kodu <xref:System.Xml.Serialization.XmlSerializer>. Bu seri hale getirme veya bu türden nesneler seri durumdan çıkarılırken zaman XML serileştirme başlangıç performansını artırır.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serileştirici Oluşturucusu](xml-serializer-generator.md)

Gibi [Xml seri hale getirici oluşturucunun (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketini](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET standart kitaplıkları çözümüdür. Bir XML serileştirme derleme türleri serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede yer alan oluşturur <xref:System.Xml.Serialization.XmlSerializer>.