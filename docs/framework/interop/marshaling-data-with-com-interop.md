---
title: COM Birlikte Çalışma ile Verileri Sıralama
description: COM birlikte çalışabilirliğine sahip verilerin sıralamasını kapsayan makalelere göz atın. Tlbimp.exe ve Tlbexp.exe araçları bir COM tür kitaplığı ve birlikte çalışma derlemesi arasında dönüştürülür.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: 94149e0c444cad7e32f959eaedd55bf14acb1ecb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547850"
---
# <a name="marshaling-data-with-com-interop"></a>COM Birlikte Çalışma ile Verileri Sıralama
COM birlikte çalışma, yönetilen koddan COM nesnelerini kullanarak ve yönetilen nesneleri COM 'a açığa çıkarmak için destek sağlar. COM 'a ve sürümünden veri sıralama desteği kapsamlıdır ve neredeyse her zaman doğru sıralama davranışını sağlar.  
  
 Windows SDK aşağıdaki COM birlikte çalışma araçlarını içerir:  
  
- COM tür kitaplığını birlikte çalışma derlemesine dönüştüren [tür kitaplığı alma programı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Bu derlemeden birlikte çalışma hazırlama hizmeti yönetilen ve yönetilmeyen bellek arasında veri hazırlama işlemi gerçekleştiren sarmalayıcılar oluşturur.  
  
- Bir derlemeden COM tür kitaplığı üreten ve Yöntem çağrıları sırasında sıralama gerçekleştiren bir sarmalayıcı oluşturan [tür kitaplığı verme programı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
 Aşağıdaki bölümler, ek tür bilgileri ile Sıralayıcı sağlamanız (veya yapmanız gerektiğinde) birlikte çalışma sarmalayıcılarını özelleştirmek için süreçler tanımlayan konuların bağlantısını ele vermektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
[Nasıl yapılır: sarmalayıcıları El Ile oluşturma](how-to-create-wrappers-manually.md) Yönetilen kaynak kodunda el ile bir COM sarmalayıcı oluşturmayı açıklar.

 [Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme](how-to-migrate-managed-code-dcom-to-wcf.md)  
 En güvenli çözüm için yönetilen DCOM kodunun WCF 'ye nasıl geçirileceğiyle ilgili açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [COM veri türleri](/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Karşılık gelen yönetilen ve yönetilmeyen veri türlerini sağlar.  
  
 [COM çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Tasarım zamanında özniteliği kullanılarak veri türlerinin açıkça nasıl hazırlanacağını açıklar <xref:System.Runtime.InteropServices.MarshalAsAttribute> .  
  
 [Çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Birlikte çalışma derlemesindeki türlerin sıralama davranışının nasıl ayarlanacağını ve COM türlerinin el ile nasıl tanımlanacağını açıklar.  
  
 [Gelişmiş COM birlikte çalışabilirlik](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 .NET Framework uygulamanıza COM bileşenlerini ekleme hakkında daha fazla bilgi için bağlantılar sağlar.  
  
 [Derlemeden tür kitaplığına dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Kitaplık dışarı aktarma dönüştürme işlemini yazmak için bütünleştirilmiş kodu açıklar.  
  
 [Tür kitaplığını derlemeye dönüştürme Özeti](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Derleme içeri aktarma dönüştürme işlemine tür kitaplığını tanımlar.  
  
 [Genel türler kullanılarak birlikte çalışma](/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 COM birlikte çalışabilirlik için genel türler kullanılırken hangi eylemlerin desteklendiğini açıklar.
