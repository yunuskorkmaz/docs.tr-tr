---
title: "İşlem temelleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 353f4ee2-e6bf-4b1c-b1c8-385fc8a486c0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa26531b1d2573b4bef49ec93f4205716227e25b
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="transaction-fundamentals"></a>İşlem temelleri
İşlemleri birden çok görev birbirine bağlayın. Örneğin, bir uygulama iki görevleri gerçekleştirir düşünün. İlk olarak, bir veritabanında yeni bir tablo oluşturur. Ardından, Topla, biçimlendirme ve yeni tabloya veri eklemek için özel bir nesne çağırır. Yeni bir tablo ile veri doldurun sürece oluşturmamaya özen gösterin istediğiniz şekilde bu iki görevleri ilgili ve hatta bağımlı. Tek bir işlem kapsamı içinde her iki görevi yürütme aralarındaki bağlantıyı zorlar. İkinci görev başarısız olursa, yeni bir tablo oluşturulmadan önce ilk görev bir noktaya geri alınır.  
  
 Tahmin edilebilir bir davranış emin olmak için tüm işlemleri temel ACID özelliklerini (atomik, tutarlı, yalıtılmış ve dayanıklı) sahip olması gerekir. Bu özelliklerin tümü veya hiçbiri işlemini önermeleri kritik işlemleri rolünü pekiştirmek. ACID hakkında daha fazla bilgi için lütfen bkz [ACID özellikleri](http://go.microsoft.com/fwlink/?LinkId=98791). Özet olarak, ACID kümesini görevleri başarılı veya başarısız bir birim olarak ilgili güvence altına alır. Terminoloji, işlem ya da işlem içinde tamamlar veya iptal eder. Bir işlem gerçekleştirmeyi tüm katılımcılar veri herhangi bir değişiklik kalıcı olacağını garanti gerekir. Sistem kilitlenme veya diğer öngörülemeyen olayları rağmen değişiklikleri kalıcı gerekir. Bu garantisi yapmak tek bir katılımcı başarısız olursa, tüm işlem başarısız olur. Veri işlem kapsamı içinde yapılan tüm değişiklikler, belirli bir kümesi noktasına geri alınır.  
  
 Bir veritabanı ya da ileti sırası gibi bir tek veri kaynağı için bir işlem sınırlı. Bu senaryoda, yerel işlem işlem tarafından sağlanan Yöneticisi tarafından yönetilen <xref:System.Transactions> , performans kazancı oluşturur. Veri kaynağı tarafından denetlenen, bu işlemler, verimli ve yönetilmesi kolay.  
  
 İşlemler birden fazla veri kaynakları da yayılabilir. Dağıtılmış işlemler farklı sistemlerde tek bir geçiş yürütülen birkaç farklı işlem birleştirmek veya eylem başarısız olanağı verir. Bu senaryoda, işlemler tarafından Microsoft Dağıtılmış İşlem Düzenleyicisi (her sistem bulunan MSDTC) düzenlenir.  
  
 Tarafından sağlanan sınıflarını kullanarak işlem bir uygulama geliştirirken <xref:System.Transactions>ne tür işlemler ihtiyacınız hakkında endişelenmeniz gerekmez veya işlem yöneticisi dahil. <xref:System.Transactions> Altyapı otomatik olarak yönetir, bu.  
  
 Bir işlem oluşturduğunuzda, harekete uygulanan yalıtım düzeyini belirtebilirsiniz. Tarafından tanımlanan yalıtım düzeyi <xref:System.Transactions.IsolationLevel> enum, diğer işlemleri verileri etkilenen işlem tarafından erişim düzeyini belirler.  
  
 ADO.NET kullanarak işlemleri oluşturabilirsiniz <xref:System.EnterpriseServices>, veya tarafından sağlanan işlem programlama modeli <xref:System.Transactions> ad alanı. [System.Transactions tarafından sağlanan özellikleri](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md) konuda ele alınmıştır kullanarak bir işlemle ilgili uygulama yazmak için kullanabileceğiniz özellikler <xref:System.Transactions> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [System.Transactions Tarafından Sağlanan Özellikler](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)
