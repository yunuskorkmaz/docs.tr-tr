---
title: İşlem Uygulaması Yazma
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 318771c83a5b7ebc0f3fb2bb8c59240269a2dea9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205816"
---
# <a name="writing-a-transactional-application"></a>İşlem Uygulaması Yazma
Bir işlem uygulaması programlayıcı olarak, bir işlem oluşturmak için <xref:System.Transactions> ad alanı tarafından sunulan iki programlama modelinden yararlanabilirsiniz. Sınıfını kullanarak açık programlama modelini <xref:System.Transactions.Transaction> ya da işlem altyapısı <xref:System.Transactions.TransactionScope> tarafından otomatik olarak yönetilecek örtük programlama modelini kullanabilirsiniz. Geliştirme için örtük işlem modelini kullanmanızı öneririz. İşlem kapsamı [kullanarak örtük bir Işlem uygulama](implementing-an-implicit-transaction-using-transaction-scope.md) konusunda bir işlem kapsamının nasıl kullanılacağına ilişkin daha fazla bilgi edinebilirsiniz.  
  
 Her iki model de program tutarlı bir duruma ulaştığında işlem yürütmeyi destekler. Yürütme başarılı olursa, işlem durda işlenir. İşleme başarısız olursa, işlem iptal edilir. Uygulama programı işlemi başarıyla tamamlayamadıysanız, işlemin etkilerini durdurmayı ve geri almayı dener.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
### <a name="creating-a-transaction"></a>Işlem oluşturma  
 Ad <xref:System.Transactions> alanı, işlem oluşturmak için iki model sağlar. Bu modelleri aşağıdaki konulara değinilmektedir.  
  
 [İşlem Kapsamı Kullanarak Örtük İşlem Uygulama](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <xref:System.Transactions> Ad alanının <xref:System.Transactions.TransactionScope> sınıfını kullanarak örtük işlemler oluşturmayı nasıl desteklediğini açıklar.  
  
 [CommittableTransaction Kullanarak Belirtik İşlem Uygulama](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <xref:System.Transactions> Ad alanının <xref:System.Transactions.CommittableTransaction> sınıfını kullanarak açık işlemler oluşturmayı nasıl desteklediğini açıklar.  
  
### <a name="escalating-transaction-management"></a>Işlem yönetimini ilerleme  
 Bir işlemin başka bir uygulama etki alanındaki bir kaynağa erişmesi gerektiğinde veya başka bir dayanıklı Resource Manager 'da listeleme yapmak istiyorsanız, işlem otomatik olarak MSDTC tarafından yönetilmek üzere ilerletildi. İşlem yükseltme, [Işlem yönetimi yükseltme](transaction-management-escalation.md) konusunda ele alınmıştır.  
  
### <a name="concurrency"></a>Eşzamanlılık  
 [DependentTransaction ile eşzamanlılık yönetme](managing-concurrency-with-dependenttransaction.md) konusu, <xref:System.Transactions.DependentTransaction> sınıfı kullanılarak zaman uyumsuz görevler arasında eşzamanlılık elde edilebileceğinizi gösterir.  
  
### <a name="com-interop"></a>COM + birlikte çalışma  
 [Kurumsal Hizmetler ve com+ işlemleri Ile birlikte çalışabilirlik](interoperability-with-enterprise-services-and-com-transactions.md) konusu, dağıtılmış işlemlerinizi com+ işlemleriyle nasıl etkileşime girecağınızı gösterir.  
  
### <a name="diagnostics"></a>Tanılamalar  
 [Tanılama izlemeleri](diagnostic-traces.md) , <xref:System.Transactions> uygulamalarınızda hata gidermek için altyapı tarafından oluşturulan izleme kodlarını nasıl kullanabileceğinizi açıklar.  
  
### <a name="working-within-aspnet"></a>ASP.NET içinde çalışma  
 [ASP.net ' de using System. Transactions](using-system-transactions-in-aspnet.md) , bir ASP.NET uygulamasının içinde nasıl başarıyla <xref:System.Transactions> kullanabileceğinizi açıklar.
