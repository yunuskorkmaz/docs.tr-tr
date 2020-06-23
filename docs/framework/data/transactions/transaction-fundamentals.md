---
title: İşlem Temelleri
description: .NET 'teki işlem temellerini gözden geçirin. Tüm işlemler temel ACID özelliklerine sahip olmalıdır (Atomik, tutarlı, yalıtılmış ve dayanıklı).
ms.date: 03/30/2017
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
ms.openlocfilehash: 49292172b07985d379bfa5d520798d7d97af5749
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141945"
---
# <a name="transaction-fundamentals"></a>İşlem Temelleri
İşlemler birden çok görevi birbirine bağlar. Örneğin, bir uygulama iki görevleri gerçekleştirir düşünün. İlk olarak, bir veritabanında yeni bir tablo oluşturur. Ardından, Topla, biçimlendirme ve yeni tabloya veri eklemek için özel bir nesne çağırır. Yeni bir tablo ile veri doldurun sürece oluşturmamaya özen gösterin istediğiniz şekilde bu iki görevleri ilgili ve hatta bağımlı. Tek bir işlemin kapsamı içinde her iki görevin de yürütülmesi aralarında bağlantıyı zorlar. İkinci görev başarısız olursa, yeni bir tablo oluşturulmadan önce ilk görev bir noktaya geri alınır.  
  
 Öngörülebilir davranışı sağlamak için tüm işlemlerin temel ACID özelliklerine sahip olması gerekir (Atomik, tutarlı, yalıtılmış ve dayanıklı). Bu özellikler, görev açısından kritik işlemlerin rolünü tamamen veya-yok propositions olarak zorlar. ACID hakkında daha fazla bilgi için lütfen bkz. [ACID özellikleri](/windows/win32/cossdk/acid-properties). Özet olarak, ACID kümesini görevleri başarılı veya başarısız bir birim olarak ilgili güvence altına alır. İşlem işleme terminolojisinde işlem, işleme ya da iptal eder. Bir işlemin kaydedilmesi için tüm katılımcılar, verilerde yapılan değişikliklerin kalıcı olacağını garanti etmelidir. Sistem kilitlenme veya diğer öngörülemeyen olayları rağmen değişiklikleri kalıcı gerekir. Tek bir katılımcı bu garantisi verse de başarısız olursa, tüm işlem başarısız olur. İşlemin kapsamındaki verilerde yapılan tüm değişiklikler belirli bir küme noktasına geri alınır.  
  
 Bir işlem, veritabanı veya ileti kuyruğu gibi tek bir veri kaynağına göre sınırlandırılan olabilir. Bu senaryoda, yerel işlem tarafından tarafından sunulan Işlem yöneticisi tarafından yönetilir ve bu, <xref:System.Transactions> performans kazancı oluşturur. Veri kaynağı tarafından denetleniyorsa, bu işlemler etkili ve kolayca yönetilebilir.  
  
 İşlemler ayrıca birden çok veri kaynağına yayılabilir. Dağıtılmış işlemler, farklı sistemlerde gerçekleşen çeşitli farklı işlemleri tek bir pass veya fail eylemine dahil etmenize olanak sağlar. Bu senaryoda, işlemler her sistemde bulunan Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından düzenlenir.  
  
 Tarafından sunulan sınıfları kullanarak bir işlem uygulaması geliştirirken <xref:System.Transactions> , ihtiyacınız olan işlem türleri veya işlem yöneticisi ile ilgili endişelenmeniz gerekmez. <xref:System.Transactions>Altyapı bunları sizin için otomatik olarak yönetir.  
  
 Bir işlem oluşturduğunuzda, işlem için geçerli olan yalıtım düzeyini belirtebilirsiniz. Sabit listesi tarafından tanımlanan yalıtım düzeyi <xref:System.Transactions.IsolationLevel> , diğer işlemlerin hareketten etkilenen verilere ne kadar erişim düzeyi olacağını belirler.  
  
 ADO.NET, <xref:System.EnterpriseServices> veya ad alanı tarafından sunulan işlem programlama modelini kullanarak işlemler oluşturabilirsiniz <xref:System.Transactions> . [System. Transactions konusunun sunduğu özellikler](features-provided-by-system-transactions.md) , ad alanını kullanarak bir işlem uygulaması yazmak için kullanabileceğiniz özellikleri tartışır <xref:System.Transactions> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [System.Transactions Tarafından Sağlanan Özellikler](features-provided-by-system-transactions.md)
