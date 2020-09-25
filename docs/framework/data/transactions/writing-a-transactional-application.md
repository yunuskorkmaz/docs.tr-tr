---
title: İşlem Uygulaması Yazma
description: .NET ' te bir işlemsel uygulama yazın. Sırasıyla Transaction Class veya TransactionScope sınıfıyla açık veya örtük bir programlama modeli kullanın.
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: b4cc33939128e61a69db319491a7d2d60ab9a819
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186684"
---
# <a name="writing-a-transactional-application"></a>İşlem Uygulaması Yazma

Bir işlem uygulaması programlayıcı olarak, <xref:System.Transactions> bir işlem oluşturmak için ad alanı tarafından sunulan iki programlama modelinden yararlanabilirsiniz. Sınıfını kullanarak açık programlama modelini <xref:System.Transactions.Transaction> ya da işlem altyapısı tarafından otomatik olarak yönetilecek örtük programlama modelini kullanabilirsiniz <xref:System.Transactions.TransactionScope> . Geliştirme için örtük işlem modelini kullanmanızı öneririz. İşlem kapsamı [kullanarak örtük bir Işlem uygulama](implementing-an-implicit-transaction-using-transaction-scope.md) konusunda bir işlem kapsamının nasıl kullanılacağına ilişkin daha fazla bilgi edinebilirsiniz.  
  
 Her iki model de program tutarlı bir duruma ulaştığında işlem yürütmeyi destekler. Yürütme başarılı olursa, işlem durda işlenir. İşleme başarısız olursa, işlem iptal edilir. Uygulama programı işlemi başarıyla tamamlayamadıysanız, işlemin etkilerini durdurmayı ve geri almayı dener.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
### <a name="creating-a-transaction"></a>Işlem oluşturma  

 <xref:System.Transactions>Ad alanı, işlem oluşturmak için iki model sağlar. Bu modelleri aşağıdaki konulara değinilmektedir.  
  
 [İşlem Kapsamı Kullanarak Örtük İşlem Uygulama](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <xref:System.Transactions>Ad alanının sınıfını kullanarak örtük işlemler oluşturmayı nasıl desteklediğini açıklar <xref:System.Transactions.TransactionScope> .  
  
 [CommittableTransaction Kullanarak Belirtik İşlem Uygulama](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <xref:System.Transactions>Ad alanının sınıfını kullanarak açık işlemler oluşturmayı nasıl desteklediğini açıklar <xref:System.Transactions.CommittableTransaction> .  
  
### <a name="escalating-transaction-management"></a>Işlem yönetimini ilerleme  

 Bir işlemin başka bir uygulama etki alanındaki bir kaynağa erişmesi gerektiğinde veya başka bir dayanıklı Resource Manager 'da listeleme yapmak istiyorsanız, işlem otomatik olarak MSDTC tarafından yönetilmek üzere ilerletildi. İşlem yükseltme, [Işlem yönetimi yükseltme](transaction-management-escalation.md) konusunda ele alınmıştır.  
  
### <a name="concurrency"></a>Eşzamanlılık  

 [DependentTransaction Ile eşzamanlılık yönetme](managing-concurrency-with-dependenttransaction.md) konusu, sınıfı kullanılarak zaman uyumsuz görevler arasında eşzamanlılık elde edilebileceğinizi gösterir <xref:System.Transactions.DependentTransaction> .  
  
### <a name="com-interop"></a>COM + birlikte çalışma  

 [Kurumsal Hizmetler ve com+ işlemleri Ile birlikte çalışabilirlik](interoperability-with-enterprise-services-and-com-transactions.md) konusu, dağıtılmış işlemlerinizi com+ işlemleriyle nasıl etkileşime girecağınızı gösterir.  
  
### <a name="diagnostics"></a>Tanılama  

 [Tanılama izlemeleri](diagnostic-traces.md) , <xref:System.Transactions> uygulamalarınızda hata gidermek için altyapı tarafından oluşturulan izleme kodlarını nasıl kullanabileceğinizi açıklar.  
  
### <a name="working-within-aspnet"></a>ASP.NET içinde çalışma  

 [ASP.net ' de using System. Transactions](using-system-transactions-in-aspnet.md) , <xref:System.Transactions> bir ASP.NET uygulamasının içinde nasıl başarıyla kullanabileceğinizi açıklar.
