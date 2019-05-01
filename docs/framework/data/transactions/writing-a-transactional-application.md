---
title: İşlem Uygulaması Yazma
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 048df434ff0ada2ab5f8c7473913f6c34c05d1a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793497"
---
# <a name="writing-a-transactional-application"></a>İşlem Uygulaması Yazma
Bir işlem uygulama programcısı tarafından sağlanan iki programlama modeli yararlanabilirsiniz <xref:System.Transactions> bir işlem oluşturmak için ad alanı. Açık bir programlama modeli kullanarak kullanabilir <xref:System.Transactions.Transaction> sınıf veya içinde işlemleri otomatik olarak yönetilir altyapısı tarafından kullanarak örtük programlama modeli <xref:System.Transactions.TransactionScope> sınıfı. Geliştirme için örtük işlem model kullanmanızı öneririz. Bir işlem kapsamda kullanma hakkında daha fazla bilgi bulabilirsiniz [işlem kapsamı kullanarak örtük işlem uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) konu.  
  
 Her iki modelleri program tutarlı bir duruma ulaştığında bir işlem Sistemi'ne destekler. Kaydetme başarılı olursa, işlem getirilir. Yürütme başarısız olursa işlem durdurur. Uygulama programı başarıyla işlem tamamlanamıyor, durdurma ve hareketin etkileri geri almak çalışır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
### <a name="creating-a-transaction"></a>Bir işlem oluşturma  
 <xref:System.Transactions> Ad alanı, bir işlem oluşturmak için iki modeli sağlar. Bu modelleri aşağıdaki konulara değinilmektedir.  
  
 [İşlem Kapsamı Kullanarak Örtük İşlem Uygulama](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Açıklayan nasıl <xref:System.Transactions> ad alanı destekler kullanarak örtük işlemleri oluşturma <xref:System.Transactions.TransactionScope> sınıfı.  
  
 [CommittableTransaction Kullanarak Belirtik İşlem Uygulama](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Açıklayan nasıl <xref:System.Transactions> ad alanı destekler kullanarak açık işlemleri oluşturma <xref:System.Transactions.CommittableTransaction> sınıfı.  
  
### <a name="escalating-transaction-management"></a>İşlem Yönetim Etkinleºmesini  
 Başka bir uygulama etki alanındaki bir kaynağa erişmek bir işlem ihtiyacı olduğunda veya başka bir kalıcı Kaynak Yöneticisi'nde listeleme istiyorsanız, işlem otomatik olarak MSDTC tarafından yönetilmek üzere ilerletilmiş. İşlem yükseltme kapsanan [işlem yönetim yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md) konu.  
  
### <a name="concurrency"></a>Eşzamanlılık  
 Konu [DependentTransaction ile eşzamanlılığı yönetme](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) kullanarak zaman uyumsuz görevler arasında eşzamanlılık nasıl sağlanabilir gösterir <xref:System.Transactions.DependentTransaction> sınıfı.  
  
### <a name="com-interop"></a>COM + birlikte çalışma  
 Konu [Kurumsal Hizmetler ve COM + işlemleri ile birlikte çalışabilirlik](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) COM + işlemleri ile etkileşime, dağıtılmış işlemler nasıl yapabileceğiniz gösterir.  
  
### <a name="diagnostics"></a>Tanılamalar  
 [Tanılama izlemeleri](../../../../docs/framework/data/transactions/diagnostic-traces.md) tarafından oluşturulan izleme kodları nasıl kullanabileceğinizi açıklar <xref:System.Transactions> uygulamanızdaki hataları gidermek için altyapı.  
  
### <a name="working-within-aspnet"></a>ASP.NET içinde çalışma  
 [ASP.NET'te System.Transactions kullanma](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) konu açıklar nasıl başarıyla kullanabileceğiniz <xref:System.Transactions> içinde bir ASP.NET uygulaması.
