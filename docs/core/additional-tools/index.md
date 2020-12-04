---
title: Ek araçlar
description: .NET Core işlevselliğini desteklemek ve genişletmek için yükleyebileceğiniz ek araçlara genel bakış.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: 6aa8b62f02c4325664ffeccc0c0d4a0635a96f2d
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599225"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core ek araçlara genel bakış

Bu bölüm, .NET Core CLI ek olarak .NET Core işlevselliğini destekleyen ve genişleten araçların listesini derler.

## <a name="net-core-uninstall-tool"></a>.NET Core Kaldırma Aracı

[.NET Core kaldırma aracı](https://github.com/dotnet/cli-lab/releases) ( `dotnet-core-uninstall` ), sistemde yalnızca belirtilen sürümlerin kalması gibi .NET Core SDK 'Larını ve çalışma zamanlarını temizlemenizi sağlar. Hangi sürümlerin kaldırılacağını belirlemek için bir seçenek koleksiyonu kullanılabilir.

## <a name="net-core-diagnostic-tools"></a>.NET Core tanılama araçları

[DotNet sayaçları](../diagnostics/dotnet-counters.md) , ilk düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.

[DotNet-dump](../diagnostics/dotnet-dump.md) , yerel bir hata ayıklayıcı olmadan Windows ve Linux temel dökümlerinin toplanması ve çözümlenmesi için bir yol sağlar.

[DotNet-gcdump](../diagnostics/dotnet-gcdump.md) , canlı .net işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamanın bir yolunu sunar.

[DotNet-Trace](../diagnostics/dotnet-trace.md) , bir uygulamanın yavaş çalışmasına neden olduğunu bulmanız gereken senaryolarda yardımcı olabilecek, uygulamanızdan profil oluşturma verileri toplar.

## <a name="net-install-tool-for-extension-authors"></a>Uzantı yazarları için .NET yüklemesi aracı

[Uzantı yazarları için .net Install aracı](https://github.com/dotnet/vscode-dotnet-runtime) , .NET Core çalışma zamanının özellikle vs Code uzantısı yazarları için alım almasına izin veren bir Visual Studio Code uzantısıdır. Bu aracın .NET dilinde yazılmış ve uzantının (örneğin, bir dil sunucusu) önyüklemesinde .NET gerektiren uzantılar için yararlanılabilir olması amaçlanmıştır. Uzantı, kullanıcıların geliştirme için .NET yüklemesi tarafından doğrudan kullanılmaya yönelik değildir.

## <a name="wcf-web-service-reference-tool"></a>WCF Web hizmeti başvuru aracı

WCF (Windows Communication Foundation) [Web hizmeti başvuru aracı](wcf-web-service-reference-guide.md) , de, [Visual studio 2017 sürüm 15,5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)' de gerçekleştirilen bir Visual Studio bağlı hizmet sağlayıcısıdır. Bu araç, geçerli çözümdeki bir Web hizmetinden, bir ağ konumunda veya bir WSDL dosyasından meta verileri alır. .NET Core ile uyumlu bir kaynak dosyası oluşturur ve Web hizmeti işlemlerine erişmek için kullanabileceğiniz yöntemlerle bir WCF proxy sınıfı tanımlar.

## <a name="wcf-dotnet-svcutil-tool"></a>WCF DotNet-Svcutil aracı

WCF [DotNet-Svcutil aracı](dotnet-svcutil-guide.md) , bir ağ konumundaki veya bir wsdl dosyasından bir Web hizmetinden meta veri alan bir .net aracıdır. .NET Core ile uyumlu bir kaynak dosyası oluşturur ve Web hizmeti işlemlerine erişmek için kullanabileceğiniz yöntemlerle bir WCF proxy sınıfı tanımlar.

**DotNet-Svcutil** Aracı, Ilk olarak visual Studio 2017 sürüm 15,5 ile birlikte sunulan [**WCF Web hizmeti başvurusu**](wcf-web-service-reference-guide.md) Visual Studio bağlı hizmet sağlayıcısına bir alternatiftir. .NET aracı olarak **DotNet-Svcutil** Aracı, Linux, MacOS ve Windows üzerinde kullanılabilir.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet-svcutil.xmlserileştirici aracı

.NET Framework, Svcutil aracını kullanarak bir serileştirme derlemesini önceden oluşturabilirsiniz. WCF [dotnet-svcutil.xmlserileştirici aracı](dotnet-svcutil.xmlserializer-guide.md) .NET Core üzerinde benzer işlevsellik sağlar. WCF hizmet sözleşmesi tarafından kullanılan ve tarafından seri hale getirileceden istemci uygulamasındaki türler için C# serileştirme kodu önceden oluşturulur <xref:System.Xml.Serialization.XmlSerializer> . Bu, bu türlerin nesneleri serileştirilirken veya seri durumdan çıkarılırken XML serileştirmesinin başlangıç performansını geliştirir.

## <a name="xml-serializer-generator"></a>XML Serileştirici Oluşturucusu

.NET Framework için [XML serileştirici Oluşturucu (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) gibi, [Microsoft.Xmlserileştirici. Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET Standard kitaplıkları için çözümdür. Kullanarak bu türlerin nesnelerini serileştirmek veya serileştirmek durumunda XML serileştirmesinin başlangıç performansını geliştirmek için bir derlemede bulunan türler için bir XML serileştirme bütünleştirilmiş kodu oluşturur <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="generating-self-signed-certificates"></a>Self-Signed sertifikaları oluşturma

Geliştirme ve test senaryoları için otomatik olarak imzalanan sertifikalar oluşturmak üzere [DotNet dev-CERT](self-signed-certificates-guide.md) ' yi kullanabilirsiniz.
