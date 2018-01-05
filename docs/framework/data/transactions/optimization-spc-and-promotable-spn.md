---
title: "Tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f85dabc8a447db13173a672db37b327ba4a9fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme
Bu konu, tarafından sağlanan mekanizmaları açıklar <xref:System.Transactions> performansını iyileştirmek için altyapı.  
  
## <a name="promotable-single-phase-enlistment"></a>Liste promotable tek aşaması  
 <xref:System.Transactions> Altyapısı, bir işlem içinde en çok tek dayanıklı kaynak veya birden çok volatile kaynakları içerir tek bir uygulama etki alanı tarafından yönetilen sayfalara. Bu yana <xref:System.Transactions> altyapısını kullanan yalnızca içi uygulama etki alanı çağrıları, en iyi verimlilik ve performans sağlar.  
  
 Ancak, işlem (işlem ve makine sınırları içinde dahil) başka bir uygulama etki alanında aynı bilgisayarda başka bir nesneye sağlanıyorsa veya başka bir sağlam Kaynak Yöneticisi, listeleme olsaydı <xref:System.Transactions> altyapısı MSDTC tarafından yönetilmek üzere işlem otomatik olarak iletir. MSDTC tarafından yönetilen bir işlem tarafından yönetilen olarak performance-wise değil <xref:System.Transactions> altyapı.  
  
 Performansı iyileştirmek için <xref:System.Transactions> altyapı yükseltilebilir tek aşaması kaydı (farklı uygulama etki alanı, işlem veya katılmayı makine bulunan tek bir uzaktan dayanıklı kaynağı, veren PSPE) sağlayan bir <xref:System.Transactions> bir MSDTC işleminde ilerletilen için bunu neden olmadan işlem.  Bu kaynak yöneticisi (RM), konak ve "daha sonra bir dağıtılmış işlem (veya MSDTC işleminde) gerekirse ilerletilen bir işlem kendi". Bu MSDTC kullanarak olasılığı azaltır.  
  
 Bu belirli Kaynak Yöneticisi'ni genellikle kendi iç olmayan dağıtılmış işlemler vardır ve bu işlem çalışma zamanında dağıtılmış işlemler dönüştürme desteklemek gerekir. Örneğin, SQL Server 2005 böyle bir kaynak yöneticisidir. Böyle bir durumda <xref:System.Transactions> altyapı yükseltme gereksinimini işlem izleme tarafından pasif yönetim rolü alır. Arasındaki etkileşimi desteklemek için <xref:System.Transactions> altyapı ve Kaynak Yöneticisi, ikinci arabirimini uygulaması gerekiyor <xref:System.Transactions.IPromotableSinglePhaseNotification>.  
  
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Yöntemi daha sonra ilerletilmiş tek bir kalıcı kaynak listeleme için kullanılır. Liste gerektiği gibi ilerletilmiş, bu yöntem sağlar. RM kaydı başarılı olursa, kendi iç işlem oluşturur ve bunu ile ilişkilendirir <xref:System.Transactions> işlem. PSPE liste başarısız olursa, RM bunun yerine kullanarak listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> yöntemi. İşlem zaten dağıtılmış bir işlem olduğunda ya da başka bir RM PSPE kaydı zaten gerçekleştirdiği PSPE içinde listeleme hataları oluşabilir  
  
 Kayıtlı sonra yürütün veya durdurmak için istemciler tarafından çağırır <xref:System.Transactions> işlem dönüştürülür çağrıları Resource Manager'daki çağırarak <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> yöntemini veya <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> sırasıyla.  
  
 Varsa <xref:System.Transactions> hareket hiçbir zaman gerektirir yükseltme, işlem tamamlandığında RM alır bir <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> bildirim. Ardından, ilk olarak oluşturulduğundan iç işlem de onaylayabilirsiniz.  
  
 Varsa <xref:System.Transactions> işlem ilerletilen gerekir (örn., birden çok RMs desteklemek için), <xref:System.Transactions> çağırarak Kaynak Yöneticisi'ni bildirir <xref:System.Transactions.ITransactionPromoter.Promote%2A> yöntemi <xref:System.Transactions.ITransactionPromoter> içinden arabirimi <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi türer. Kaynak Yöneticisi'ni sonra işlem dahili olarak (Bu, günlük gerektirmeyen) yerel bir işlem DTC işlemde katılan işleyebilir ve zaten çalışmanın ile ilişkilendiren bir işlem nesnesi dönüştürür. İşlem gerçekleştirmeyi sorulduğunda, işlem yöneticisi hala gönderir <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> yükseltme sırasında oluşturulan dağıtılmış işlem tamamlar Kaynak Yöneticisi bildirimi.  
  
> [!NOTE]
>  **TransactionCommitted** (bir yürütme ilerletilen işlem çalıştırıldığında oluşturulan) izlemeler DTC işlem etkinlik Kimliğini içerir.  
  
 Yönetim yükseltme hakkında daha fazla bilgi için bkz: [işlem yönetimi yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md).  
  
## <a name="transaction-management-escalation-scenario"></a>İşlem yönetimi yükseltme senaryosu  
 Aşağıdaki senaryoyu kullanarak bir dağıtılmış işlem için bir yükseltme gösteren <xref:System.Data> kaynak yöneticisi için 'proxy'si' olarak ad alanı. Bu senaryo zaten bir tane olduğunu varsayar <xref:System.Data> CN1, veritabanı bağlantısı dahil işlemde ve başka kapsayacak şekilde uygulamanın istediği <xref:System.Data> bağlantı, CN2. İşlem bir tam dağıtılmış iki aşamalı kaydetme işlemi, DTC ilerletilen gerekir.  
  
 Bu senaryoda  
  
1.  CN1 çağrıları <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> işleminde listelenmeyi yöntemi. Daha sonra hala yerel bir işlemdir ve işlem üzerinde yükseltilebilir diğer kayıtlar vardır böylece <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> çağrı başarılı olur.  
  
2.  İkinci bağlantı CN2 çağırır olduğunda <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, ilgili başka bir promotable liste olduğundan çağrı başarısız olur. Bu nedenle, CN2 DTC işlemini SQL geçirmek için almanız gerekir. Bunu yapmak için onu tarafından sağlanan yöntemlerden birini kullanır <xref:System.Transactions.TransactionInterop> SQL verilebilir işlem biçiminin üretmek için sınıf.  
  
3.  <xref:System.Transactions>çağrıları <xref:System.Transactions.ITransactionPromoter.Promote%2A> yöntemi <xref:System.Transactions.ITransactionPromoter> CN1 tarafından uygulanan arabirimi.  
  
4.  Bu noktada, SQL 2005'e belirli bazı mekanizmasını kullanarak CN1 işlem iletir ve <xref:System.Data>.  
  
5.  Dönüş değerini <xref:System.Transactions.ITransactionPromoter.Promote%2A> yöntemdir işlem için bir yayma belirteci içeren bayt dizisi. <xref:System.Transactions>Yerel harekete dahil edebilirsiniz DTC işlem oluşturmak için bu propagaition belirtecini kullanır.  
  
6.  Bu noktada, CN2 tarafından yöntemlerden birini çağırma alınan verileri kullanabilirsiniz <xref:System.Transactions.TransactionInterop> SQL işlem geçirmek için.  
  
7.  Şimdi, hem de bir dağıtılmış DTC işlem içinde kayıtlıdır.  
  
## <a name="single-phase-commit-optimization"></a>Tek aşaması yürütme en iyi hale getirme  
 Tek aşaması yürütme protokol tüm güncelleştirmeleri herhangi bir açık işbirliği tamamlanır olarak çalışma zamanında daha etkilidir. Bu iyileştirme yararlanmak için bir Kaynak Yöneticisi'ni kullanarak uygulamalıdır <xref:System.Transactions.ISinglePhaseNotification> arabirim için kaynak ve kullanarak bir işlem listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> yöntemi. Özellikle, *EnlistmentOptions* parametre eşit <xref:System.Transactions.EnlistmentOptions.None> tek aşamalı yürütme gerçekleştirilen emin olmak için.  
  
 Bu yana <xref:System.Transactions.ISinglePhaseNotification> arabirimi türetilir <xref:System.Transactions.IEnlistmentNotification> arabirim, RM tek aşaması yürütme için uygun değilse, bunu iki aşaması yürütme bildirimleri almaya devam.  RM alırsa bir <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> TM bildirimden, deneyin kaydetmek ve işlem yürütülmeli veya geri çağırarak için ise işlem yöneticisi gelenlere bildirmek için gerekli iş yapmak <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>, veya <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> yöntemi <xref:System.Transactions.SinglePhaseEnlistment> parametresi. Yanıtın <xref:System.Transactions.Enlistment.Done%2A> liste bu aşamada üzerinde salt okunur semantiği anlamına gelir. Bu nedenle, değil yanıt <xref:System.Transactions.Enlistment.Done%2A> ek olarak diğer yöntemleri.  
  
 Yalnızca bir geçici kaydı ve dayanıklı kaydı ise volatile kaydı SPC bildirimi alır.  Volatile tüm kayıtlar ve yalnızca bir dayanıklı kaydı varsa volatile kayıtlar 2PC alırsınız. Tamamlandığında, kalıcı liste SPC alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
 [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
