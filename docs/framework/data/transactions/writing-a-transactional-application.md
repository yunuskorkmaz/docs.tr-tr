---
title: "İşlem uygulaması yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fab355da61ea7445e429cfc4e336a14b588e30c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-transactional-application"></a>İşlem uygulaması yazma
İşlem Uygulaması Programcı olarak tarafından sağlanan iki programlama modeli özelliklerden yararlanabilirsiniz <xref:System.Transactions> bir işlem oluşturmak için ad alanı. Açık programlama modeli kullanarak kullanabilir <xref:System.Transactions.Transaction> sınıfı ya da hangi işlemleri otomatik olarak yönetilir altyapısı tarafından kullanarak örtük programlama modeli <xref:System.Transactions.TransactionScope> sınıfı. Geliştirme için örtük işlem modeli kullanmanızı öneririz. Bir işlem kapsamı içinde kullanma hakkında daha fazla bilgi bulabilirsiniz [örtük bir işlem kapsamı kullanarak işlem uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) konu.  
  
 Her iki modelleri program tutarlı bir duruma ulaştığında bir işlem gerçekleştirmeden destekler. Yürütme başarılı olursa, işlem getirilir. Yürütme başarısız olursa, işlem durdurur. Uygulama programı işlem başarılı bir şekilde tamamlanamazsa, iptal etmek ve hareket etkilerinin geri almak çalışır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
### <a name="creating-a-transaction"></a>Bir işlem oluşturma  
 <xref:System.Transactions> Ad alanı, bir işlem oluşturmak için iki modeli sağlar. Bu modelleri aşağıdaki konulara değinilmektedir.  
  
 [İşlem Kapsamı Kullanarak Örtük İşlem Uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Açıklar nasıl <xref:System.Transactions> ad alanı destekleyen kullanarak örtük hareketleri oluşturma <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [CommittableTransaction Kullanarak Belirtik İşlem Uygulama](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Açıklar nasıl <xref:System.Transactions> ad alanı destekleyen açık işlemleri kullanarak oluşturma <xref:System.Transactions.CommittableTransaction> sınıfı.  
  
### <a name="escalating-transaction-management"></a>İşlem yönetimi yükselen  
 Bir işlem başka bir uygulama etki alanındaki bir kaynağa erişmek gerektiğinde veya başka bir sağlam Kaynak Yöneticisi'nde listeleme istiyorsanız işlem otomatik olarak MSDTC tarafından yönetilecek ilerletilen. İşlem yükseltme kapsanan [işlem yönetimi yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md) konu.  
  
### <a name="concurrency"></a>Eşzamanlılık  
 Konu [yönetme eşzamanlılık DependentTransaction ile](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) eşzamanlılık kullanarak zaman uyumsuz görevler arasında nasıl sağlanabilir gösteren <xref:System.Transactions.DependentTransaction> sınıfı.  
  
### <a name="com-interop"></a>COM + birlikte çalışma  
 Konu [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) COM + hareketlerle etkileşimde, dağıtılmış işlemlerin nasıl yapabileceğiniz gösterilmektedir.  
  
### <a name="diagnostics"></a>Tanılamalar  
 [Tanılama izlemeleri](../../../../docs/framework/data/transactions/diagnostic-traces.md) tarafından oluşturulan izleme kodları nasıl kullanabileceğinizi açıklar <xref:System.Transactions> uygulamalarınızda hatalarında sorun giderme için altyapı.  
  
### <a name="working-within-aspnet"></a>ASP.NET içinde çalışma  
 [Kullanarak System.Transactions ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) konu açıklar, başarılı bir şekilde nasıl kullanabileceğinizi <xref:System.Transactions> bir ASP.NET uygulaması içinde.
