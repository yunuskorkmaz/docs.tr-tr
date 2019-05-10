---
title: COM Birlikte Çalışma ile Verileri Sıralama
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 807e514fac7d33cdacac3a48a37c7aa8dd92ef9c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648638"
---
# <a name="marshaling-data-with-com-interop"></a>COM Birlikte Çalışma ile Verileri Sıralama
COM birlikte çalışma COM nesnelerine yönetilen COM nesneleri yönetilen kod kullanarak hem de kullanıma sunmak için destek sağlar. COM veri hazırlama için destek kapsamlı ve neredeyse her zaman doğru sıralama davranışını sağlar.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Aşağıdaki COM birlikte çalışma araçları içerir:  
  
- [Tür kitaplığı alma programı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), birlikte çalışma derlemesi için bir COM tür kitaplığı dönüştürür. Bu derleme, birlikte çalışma hazırlama hizmeti veri arasında yönetilen ve yönetilmeyen bellek hazırlama gerçekleştirmek sarmalayıcıları oluşturur.  
  
- [Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), bir derlemeden bir COM tür kitaplığı üretir ve yöntem çağrıları sırasında hazırlama gerçekleştiren bir sarmalayıcı oluşturur.  
  
 Aşağıdaki bölümlerde, ek türü bilgilerini ile Sıralayıcı sağladığınız olabilir veya gerekir, birlikte çalışma sarmalayıcılarını özelleştirme işlemleri açıklayan konulara bağlayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
[Nasıl yapılır: Sarmalayıcıları elle oluşturma](how-to-create-wrappers-manually.md)   
Bir COM sarmalayıcı yönetilen kaynak kodunda el ile oluşturmayı açıklar. 
 
 [Nasıl yapılır: Yönetilen kodu DCOM'dan WCF'ye geçirme](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 DCOM yönetilen kod için en güvenli çözümü için WCF geçişi işlemi açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [COM veri türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Karşılık gelen yönetilen ve yönetilmeyen veri türleri sağlar.  
  
 [COM aranabilir sarmalayıcılarını özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 Veri türleri kullanılarak açıkça hazırlanacağını açıklar <xref:System.Runtime.InteropServices.MarshalAsAttribute> tasarım zamanında özniteliği.  
  
 [Çalışma zamanı aranabilir sarmalayıcılarını özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Bir birlikte çalışma bütünleştirilmiş kodundaki türler sıralama davranışını ayarlama ve COM türlerini manuel olarak tanımlamak nasıl açıklar.  
  
 [Gelişmiş COM birlikte çalışabilirliği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 COM bileşenlerini .NET Framework'te uygulamanıza ekleme hakkında daha fazla bilgi için bağlantılar sağlar.  
  
 [Derlemeden tür kitaplığına dönüştürme özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Derleme, tür kitaplığı dışarı aktarma dönüştürme işlemi için açıklar.  
  
 [Tür kitaplığını derlemeye dönüştürme özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Tür kitaplığını derleme içeri aktarma dönüştürme işlemi için açıklar.  
  
 [Genel türleri kullanarak birlikte çalışma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 Hangi eylemler genel türler COM birlikte çalışabilirlik için kullanılırken desteklenen açıklar.
