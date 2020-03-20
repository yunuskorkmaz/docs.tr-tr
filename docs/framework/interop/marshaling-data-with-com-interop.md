---
title: COM Birlikte Çalışma ile Verileri Sıralama
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: ae41713d5349321725599c0c38d7c6fc515c374b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181379"
---
# <a name="marshaling-data-with-com-interop"></a>COM Birlikte Çalışma ile Verileri Sıralama
COM interop, yönetilen koddaki COM nesnelerini kullanmak ve yönetilen nesneleri COM'a teşhir etmek için destek sağlar. Com'a ve COM'dan veri mareşallik desteği kapsamlıdır ve hemen hemen her zaman doğru mareşaldavranışını sağlar.  
  
 Windows SDK aşağıdaki COM interop araçlarını içerir:  
  
- Com türü kitaplığını interop derlemesine dönüştüren [Kitaplık İthalatçısı (Tlbimp.exe) türü.](../tools/tlbimp-exe-type-library-importer.md) Bu derlemeden, interop mareşallik hizmeti, yönetilen ve yönetilmeyen bellek arasında veri mareşalleme gerçekleştiren sarmalayıcılar oluşturur.  
  
- Bir derlemeden COM türü kitaplığı üreten ve yöntem aramaları sırasında mareşallik gerçekleştiren bir sarmalayıcı üreten [Tip Kitaplık İhracatçısı (Tlbexp.exe).](../tools/tlbexp-exe-type-library-exporter.md)  
  
 Aşağıdaki bölümler, mareşale ek tür bilgileri sağlayabildiğinizde (veya sağlamanız gerektiğinde) interop sarmalayıcılarını özelleştirme süreçlerini açıklayan konulara bağlantı eder.  
  
## <a name="in-this-section"></a>Bu Bölümde  
[Nasıl yapılır: Sarmalayıcıları El ile Oluştur](how-to-create-wrappers-manually.md) Yönetilen kaynak kodunda el ile com sarıcı nın nasıl oluşturuluruz açıklanır.

 [Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme](how-to-migrate-managed-code-dcom-to-wcf.md)  
 Yönetilen DCOM kodunun en güvenli çözüm için WCF'ye nasıl geçirilen bir şekilde geçirilen açıklanır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [COM Veri Türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Karşılık gelen yönetilen ve yönetilmeyen veri türleri sağlar.  
  
 [COM Çağrılabilir Sarmalayıcıları Özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Tasarım zamanında özniteliği kullanarak veri <xref:System.Runtime.InteropServices.MarshalAsAttribute> türlerini açıkça nasıl keşe edilebildiğini açıklar.  
  
 [Runtime Çağrılanabilir Sarmalayıcıları Özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Bir interop derlemesindeki türlerin mareşaldavranışını nasıl ayarlayacaklarını ve COM türlerini el ile nasıl tanımlayacaklarını açıklar.  
  
 [Gelişmiş COM Birlikte Çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 COM bileşenlerini .NET Framework uygulamanıza dahil etme hakkında daha fazla bilgiye bağlantılar sağlar.  
  
 [Derleme den Türe Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Kitaplık dışa aktarma dönüşüm işlemini yazmak için derlemeyi açıklar.  
  
 [Tür Kitaplığı ndan Montaja Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Derleme alma dönüştürme işlemine tür kitaplığını açıklar.  
  
 [Genel Türleri Kullanarak Ara Çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 COM birlikte çalışabilirliği için genel türleri kullanırken hangi eylemlerin desteklenir açıklar.
