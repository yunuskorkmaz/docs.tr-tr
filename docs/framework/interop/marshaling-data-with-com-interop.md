---
title: "COM Birlikte Çalışma ile Verileri Hazırlama"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 649936abfe149371445c77802bda2e72f558a41d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-data-with-com-interop"></a>COM Birlikte Çalışma ile Verileri Hazırlama
COM birlikte çalışma COM nesnelerine yönetilen COM nesneleri yönetilen koddan kullanarak hem gösterme desteği sağlar Verileri için ve COM hazırlama desteği kapsamlı ve neredeyse her zaman doğru hazırlama davranışı sağlar.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Aşağıdaki COM birlikte çalışma araçları içerir:  
  
-   [Tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), birlikte çalışabilirlik bütünleştirilmiş COM tür kitaplığı dönüştürür. Bu derlemedeki, hizmet hazırlama birlikte çalışabilirliği veri yönetilen ve yönetilmeyen bellek arasında sıralama gerçekleştirmek sarmalayıcılar oluşturur.  
  
-   [Tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), COM tür kitaplığından derleme üretir ve yöntem çağrılarını sırasında hazırlama gerçekleştiren bir sarmalayıcı oluşturur.  
  
 Aşağıdaki bölümlerde ek türü bilgilerle Sıralayıcı sağlayın ya da gerekir, birlikte çalışabilirlik sarmalayıcıları özelleştirme işlemleri açıklayan konulara bağlayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
[Nasıl yapılır: sarmalayıcıları elle oluşturma](how-to-create-wrappers-manually.md)   
Bir COM sarmalayıcı elle yönetilen kaynak kodunda nasıl oluşturulacağını açıklar. 
 
 [Nasıl yapılır: Yönetilen Kodu DCOM’dan WCF’ye Geçirme](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 WCF için en güvenli çözüm için yönetilen DCOM kod geçirmeyi açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [COM veri türleri](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)  
 Karşılık gelen yönetilen ve yönetilmeyen veri türleri sağlar.  
  
 [COM aranabilir sarmalayıcılar özelleştirme](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)  
 Veri türleri kullanılarak açıkça hazırlanacağını açıklar <xref:System.Runtime.InteropServices.MarshalAsAttribute> tasarım zamanında özniteliği.  
  
 [Çalışma zamanı aranabilir sarmalayıcıları özelleştirme](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)  
 Birlikte çalışma derlemedeki türleri hazırlama davranışı ayarlamak ve COM türlerini manuel olarak tanımlamak açıklar.  
  
 [Gelişmiş COM birlikte çalışabilirliği](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)  
 COM bileşenlerini .NET Framework uygulamasına ekleme hakkında daha fazla bilgi için bağlantılar sağlar.  
  
 [Derleme Kitaplığı dönüştürme özeti yazın](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)  
 Kitaplık dışarı aktarma dönüştürme işlemini yazmak için derlemeyi açıklar.  
  
 [Derleme dönüştürme özeti için tür kitaplığı](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)  
 Tür kitaplığını derleme alma dönüştürme işlemi için açıklar.  
  
 [Genel türler kullanma birlikte çalışma](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)  
 Genel türler COM birlikte çalışabilirlik için kullanılırken hangi eylemleri desteklenen açıklar.
