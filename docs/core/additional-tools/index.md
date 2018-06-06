---
title: .NET core ek araçlar
description: Destekleyen ve .NET çekirdek işlevselliğini genişleten ek araçlar genel bakış.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
ms.openlocfilehash: a842224a76962a9d6db820149a75f1255204e9b7
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728569"
---
# <a name="net-core-additional-tools"></a>.NET core ek araçlar

Bu bölümde destekleyen ve ek olarak .NET çekirdek işlevselliğini genişleten Araçlar listesini derler [.NET Core komut satırı arabirimi (CLI)](..\tools\index.md) araçları.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web hizmeti başvuru aracı](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web hizmeti, ilk kez içinde yapılan bir Visual Studio bağlı hizmet sağlayıcısı başvurudur [Visual Studio 2017 sürüm 15,5](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes#WCFTools). Bu araç, bir web hizmeti geçerli çözümdeki bir ağ konumu veya WSDL dosya meta verileri alır ve .NET Core, web hizmeti işlemleri erişmek için kullanabileceğiniz yöntemleri ile WCF proxy sınıfı tanımlayan ile uyumlu bir kaynak dosyası oluşturur.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF dotnet svcutil aracı](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) dotnet svcutil aracı, bir ağ konumu üzerinde bir web hizmetinden veya WSDL dosya meta verileri alır ve .NET Core, WCF proxy sınıfı yöntemleri tanımlama ile uyumlu bir kaynak dosyası oluşturur bir .NET Core CLI araçtır web hizmeti işlemleri erişmek için kullanabileceğiniz. **Dotnet svcutil** araçtır için alternatif bir seçenek [ **WCF Web hizmeti başvuru** ](/dotnet/core/additional-tools/wcf-web-service-reference-guide) Visual Studio, Visual Studio ile hangi ilk sevk hizmet sağlayıcısı bağlı 2017 v15.5. **Dotnet svcutil** aracı .NET Core CLI aracı olarak, Linux, macOS ve Windows üzerinde kullanılabilir çapraz platform eklentisidir.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serileştirici Oluşturucusu](xml-serializer-generator.md)

Gibi [Xml seri hale getirici Oluşturucu (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) .NET Framework için [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET standart kitaplıkları için çözümüdür. XML serileştirme bütünleştirilmiş serileştirmek veya seri durumundan kullanarak bu tür nesneler XML serileştirme başlangıç performansını artırmak için bir derlemede bulunan türleri için oluşturduğu <xref:System.Xml.Serialization.XmlSerializer>.