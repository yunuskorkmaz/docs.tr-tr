---
title: Ek araçlar
description: .NET Core işlevselliğini desteklemek ve genişletmek için yükleyebileceğiniz ek araçlara genel bakış.
author: mlacouture
ms.date: 12/02/2019
ms.custom: mvc
ms.openlocfilehash: 23b94ceef729cdc3d83032e3897312eb1d1afd79
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920929"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core ek araçlara genel bakış

Bu bölüm, .NET Core CLI ek olarak .NET Core işlevselliğini destekleyen ve genişleten araçların listesini derler.

## <a name="net-core-uninstall-tooluninstall-toolmd"></a>[.NET Core kaldırma aracı](uninstall-tool.md)

[.NET Core kaldırma aracı](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`), sistemde yalnızca belirtilen sürümlerin kalması gibi .NET Core SDK 'larını ve çalışma zamanlarını temizlemenizi sağlar. Hangi sürümlerin kaldırılacağını belirlemek için bir seçenek koleksiyonu kullanılabilir.

## <a name="wcf-web-service-reference-toolwcf-web-service-reference-guidemd"></a>[WCF Web hizmeti başvuru aracı](wcf-web-service-reference-guide.md)

WCF (Windows Communication Foundation) Web hizmeti başvurusu, {1 & gt; [Visual studio 2017 sürüm 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)' de yaptığı, Visual Studio bağlı bir hizmet sağlayıcıdır. Bu araç, geçerli çözümdeki bir Web hizmetinden, bir ağ konumunda veya bir WSDL dosyasından meta verileri alır. .NET Core ile uyumlu bir kaynak dosyası oluşturur ve Web hizmeti işlemlerine erişmek için kullanabileceğiniz yöntemlerle bir WCF proxy sınıfı tanımlar.

## <a name="wcf-dotnet-svcutil-tooldotnet-svcutil-guidemd"></a>[WCF DotNet-Svcutil aracı](dotnet-svcutil-guide.md)

WCF (Windows Communication Foundation) DotNet-Svcutil Aracı, bir ağ konumundaki veya bir WSDL dosyasından bir Web hizmetinden meta verileri alan bir .NET aracıdır. .NET Core ile uyumlu bir kaynak dosyası oluşturur ve Web hizmeti işlemlerine erişmek için kullanabileceğiniz yöntemlerle bir WCF proxy sınıfı tanımlar.

**DotNet-Svcutil** Aracı, Ilk olarak visual Studio 2017 sürüm 15,5 ile birlikte sunulan [**WCF Web hizmeti başvurusu**](wcf-web-service-reference-guide.md) Visual Studio bağlı hizmet sağlayıcısına alternatif bir seçenektir. .NET aracı olarak **DotNet-Svcutil** Aracı, Linux, MacOS ve Windows üzerinde platformlar arası kullanıma sunulmuştur.

## <a name="wcf-dotnet-svcutilxmlserializer-tooldotnet-svcutilxmlserializer-guidemd"></a>[WCF DotNet-Svcutil. XmlSerializer aracı](dotnet-svcutil.xmlserializer-guide.md)

.NET Framework, Svcutil aracını kullanarak bir serileştirme derlemesini önceden oluşturabilirsiniz. DotNet-Svcutil. XmlSerializer NuGet paketi .NET Core 'da benzer işlevsellik sağlar. WCF hizmet sözleşmesi tarafından C# kullanılan ve <xref:System.Xml.Serialization.XmlSerializer>tarafından seri hale getirilebilen istemci uygulamasındaki türler için serileştirme kodu önceden oluşturulur. Bu, bu türlerin nesneleri serileştirilirken veya seri durumdan çıkarılırken XML serileştirmesinin başlangıç performansını geliştirir.

## <a name="xml-serializer-generatorxml-serializer-generatormd"></a>[XML Serileştirici Oluşturucusu](xml-serializer-generator.md)

.NET Framework için [XML serileştirici Oluşturucu (SGen. exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) gibi, [Microsoft. XmlSerializer. Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET Standard kitaplıkları çözümüdür. <xref:System.Xml.Serialization.XmlSerializer>kullanarak bu türlerin nesnelerini serileştirmek veya seri hale getirmede XML serileştirmesinin başlangıç performansını geliştirmek için bir derlemede bulunan türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur.
