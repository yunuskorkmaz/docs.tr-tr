---
title: İşlem Temelleri
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: 49e44ce1112a44c105f47560017331afe4454a0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793524"
---
# <a name="transaction-fundamentals"></a>İşlem Temelleri
İşlemler birden çok görevleri birbirine bağlayın. Örneğin, bir uygulama iki görevleri gerçekleştirir düşünün. İlk olarak, bir veritabanında yeni bir tablo oluşturur. Ardından, Topla, biçimlendirme ve yeni tabloya veri eklemek için özel bir nesne çağırır. Yeni bir tablo ile veri doldurun sürece oluşturmamaya özen gösterin istediğiniz şekilde bu iki görevleri ilgili ve hatta bağımlı. Her iki görevlerini tek bir işlem kapsamında yürütüyor onların arasındaki bağlantıyı zorlar. İkinci görev başarısız olursa, yeni bir tablo oluşturulmadan önce ilk görev bir noktaya geri alınır.  
  
 Tahmin edilebilir davranış sağlamak için tüm işlemler temel ACID özelliklerini (atomik, tutarlı, yalıtılmış ve kalıcı) sahip olması gerekir. Bu özellikler önermeler kritik işlemleri rolünü güçlendirmek. ACID hakkında daha fazla bilgi için lütfen bkz [ACID özellikleri](https://go.microsoft.com/fwlink/?LinkId=98791). Özet olarak, ACID kümesini görevleri başarılı veya başarısız bir birim olarak ilgili güvence altına alır. Terimleri, işlem ya da işleme işlemde tamamlar veya durdurur. Bir işlem teslim tüm katılımcıları veri herhangi bir değişiklik kalıcı olmasını garanti gerekir. Sistem kilitlenme veya diğer öngörülemeyen olayları rağmen değişiklikleri kalıcı gerekir. Bu garanti yapmak tek bir katılımcı başarısız olursa, tüm işlemi başarısız olur. İşlem kapsamında veri yapılan tüm değişiklikler, belirli bir kümesi noktaya geri alınır.  
  
 Bir veritabanı veya ileti sırası gibi bir tek veri kaynağı için bir işlem sýnýrlandýrýlmasýna. Bu senaryoda yerel işlem işlem tarafından sağlanan Yöneticisi tarafından yönetilen <xref:System.Transactions> , performans kazanç oluşturur. Bu işlem, veri kaynağı tarafından denetlenen, verimli ve yönetmek kolay.  
  
 İşlemler birden fazla veri kaynağı de kapsayabilir. Dağıtılmış işlemler tek bir geçişinde farklı sistemlerde gerçekleşen birden fazla ayrı operasyon dahil veya eylemi başarısız olanağı verir. Bu senaryoda işlemler tarafından Microsoft Dağıtılmış İşlem Düzenleyicisi (her sisteminde bulunan MSDTC) düzenlenir.  
  
 Tarafından sağlanan sınıfları kullanarak bir işlem uygulama geliştirirken <xref:System.Transactions>, ne tür işlemleri ihtiyacınız hakkında merak gerekmez veya hareket yöneticisi dahil. <xref:System.Transactions> Altyapı otomatik olarak yönetir bunlar sizin için.  
  
 Bir işlem oluşturduğunuzda, harekete uygulanan yalıtım düzeyi belirtebilirsiniz. Tarafından tanımlanan yalıtım düzeyi <xref:System.Transactions.IsolationLevel> enum, diğer işlemleri verileri etkilenen, işlem tarafından erişim düzeyini belirler.  
  
 ADO.NET, kullanarak işlemleri oluşturabilirsiniz <xref:System.EnterpriseServices>, ya da tarafından sağlanan işlem programlama modeli <xref:System.Transactions> ad alanı. [System.Transactions tarafından sağlanan özellikler](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) konu anlatır kullanarak bir işlem uygulama yazmak için kullanabileceğiniz özellikler <xref:System.Transactions> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [System.Transactions Tarafından Sağlanan Özellikler](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)
