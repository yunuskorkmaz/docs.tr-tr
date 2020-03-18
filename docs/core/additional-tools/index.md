---
title: Ek araçlar
description: .NET Core işlevini destekleyebilir ve genişletebilirsiniz ek araçlara genel bakış.
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: c0224a1cc6cbb9ae6fa88e5f869c47a1e84289e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77451531"
---
# <a name="net-core-additional-tools-overview"></a>.NET Core ek araçlara genel bakış

Bu bölümde,.NET Core CLI'ye ek olarak .NET Core işlevini destekleyen ve genişleten araçların bir listesi derlenmiştir.

## <a name="net-core-uninstall-tool"></a>.NET Core Kaldırma Aracı

[.NET Çekirdek Kaldırma](https://github.com/dotnet/cli-lab/releases) Aracı`dotnet-core-uninstall`( ) .NET Core SDK'ları ve Runtimes'ı yalnızca belirtilen sürümlerin kaldığı bir sistemde temizlemenizi sağlar. Hangi sürümlerin kaldırılımını belirtmek için seçenekler topluluğu kullanılabilir.

## <a name="net-core-diagnostic-tools"></a>.NET Çekirdek tanı lama araçları

[dotnet sayaçları](../diagnostics/dotnet-counters.md) birinci düzey sistem durumu izleme ve performans araştırması için bir performans izleme aracıdır.

[dotnet-dump,](../diagnostics/dotnet-dump.md) windows ve Linux çekirdek dökümlerini yerel bir hata ayıklama olmadan toplamak ve analiz etmek için bir yol sağlar.

[dotnet-trace,](../diagnostics/dotnet-trace.md) uygulamanızın yavaş çalışmasına neyin neden olduğunu bulmanız gereken senaryolarda yardımcı olabilecek uygulamanızdan profil oluşturma verileri toplar.

## <a name="wcf-web-service-reference-tool"></a>WCF Web Hizmeti Başvuru aracı

WCF (Windows Communication Foundation) [Web Service Reference aracı](wcf-web-service-reference-guide.md) Visual Studio [2017 sürümü 15.5'te](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools)ilk kez sahneye çıkan Visual Studio bağlantılı bir servis sağlayıcısıdır. Bu araç, geçerli çözümdeki bir web hizmetinden, ağ konumundan veya WSDL dosyasından meta verileri alır. .NET Core ile uyumlu bir kaynak dosyası oluşturur ve web hizmeti işlemlerine erişmek için kullanabileceğiniz yöntemlerle bir WCF proxy sınıfı tanımlar.

## <a name="wcf-dotnet-svcutil-tool"></a>WCF dotnet-svcutil aracı

WCF [dotnet-svcutil aracı,](dotnet-svcutil-guide.md) ağ konumundaki bir web hizmetinden veya WSDL dosyasından meta verileri alan bir .NET aracıdır. .NET Core ile uyumlu bir kaynak dosyası oluşturur ve web hizmeti işlemlerine erişmek için kullanabileceğiniz yöntemlerle bir WCF proxy sınıfı tanımlar.

**Dotnet-svcutil** aracı, ilk olarak Visual Studio 2017 sürüm 15.5 ile gönderilen [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio bağlantılı servis sağlayıcısına bir alternatiftir. **Dotnet-svcutil** aracı, bir .NET aracı olarak, Linux, macOS ve Windows'da kullanılabilir.

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a>WCF dotnet-svcutil.xmlserializer aracı

.NET Framework'de, svcutil aracını kullanarak bir serileştirme derlemesi önceden oluşturabilirsiniz. WCF [dotnet-svcutil.xmlserializer aracı](dotnet-svcutil.xmlserializer-guide.md) .NET Core'da benzer işlevsellik sağlar. WCF Hizmet Sözleşmesi tarafından kullanılan ve <xref:System.Xml.Serialization.XmlSerializer>'nin serihale getirebileceği istemci uygulamasındaki türler için C# serileştirme kodunu önceden oluşturur. Bu, bu tür nesneleri serihale veya deserializing xml serileştirme başlangıç performansını artırır.

## <a name="xml-serializer-generator"></a>XML Serileştirici Oluşturucusu

.NET Framework için [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) gibi, [Microsoft.XmlSerializer.Generator NuGet paketi](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) .NET Core ve .NET Standart kitaplıklar için çözümdür. Bu, bu tür nesneleri serihale veya de-serializing nesneleri kullanırken XML serileştirme başlangıç performansını artırmak için bir <xref:System.Xml.Serialization.XmlSerializer>derleme de bulunan türleri için bir XML serileştirme derlemesi oluşturur.
