---
title: Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme
description: Tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak performansı iyileştirin. .NET ' te System. Transactions altyapısı hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
ms.openlocfilehash: 89ce82e673340c93254983c078f78a2501129383
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141984"
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme

Bu konuda, <xref:System.Transactions> performansı iyileştirmek için altyapı tarafından sunulan mekanizmalar açıklanmaktadır.

## <a name="promotable-single-phase-enlistment"></a>Liste promotable tek aşaması

Altyapı, tek bir <xref:System.Transactions> sürekli kaynak veya birden çok geçici kaynakla ilgili olan tek bir uygulama etki alanı içinde bir işlem yönetmekte. <xref:System.Transactions>Altyapı yalnızca uygulama içi etki alanı çağrılarını kullandığından, en iyi verimi ve performansı verir.

Ancak, işlem aynı bilgisayardaki başka bir uygulama etki alanındaki başka bir nesneye (işlem ve makine sınırları dahil) sağlanmışsa ya da başka bir dayanıklı Kaynak Yöneticisi 'ne kaydolunamadı, <xref:System.Transactions> ALTYAPı MSDTC tarafından yönetilmek üzere işlemi otomatik olarak ilerletir. MSDTC tarafından yönetilen bir işlem, altyapı tarafından yönetilen bir performans temelinde değildir <xref:System.Transactions> .

Altyapı, performansı iyileştirmek için, <xref:System.Transactions> farklı bir uygulama etki alanında, işlemde veya makinede bulunan tek bir uzak dayanıklı kaynağın BIR <xref:System.Transactions> MSDTC işlemine ilerlemesine neden olmadan bir işleme katılmasını sağlayan promotable tek aşaması kaydı (PSPE) sağlar. Bu Kaynak Yöneticisi (RM), daha sonra dağıtılmış bir işleme (veya MSDTC işlem) daha sonra ilerletilen bir işlem barındırabilir ve "sahip" olur. Bu MSDTC kullanarak olasılığı azaltır.

Bu belirli kaynak yöneticisi genellikle kendi iç dağıtılmış olmayan işlemlerine sahiptir ve bu işlemleri çalışma zamanında dağıtılmış işlemlere dönüştürmeyi desteklemelidir. Örneğin, SQL Server 2005 böyle bir kaynak yöneticisidir. Böyle bir durumda, <xref:System.Transactions> altyapı bir pasif yönetim rolü sunarak yalnızca bir yükseltme ihtiyacı için işlemi izler. <xref:System.Transactions>Altyapı ve kaynak yöneticisi arasındaki etkileşimi desteklemek için, ikinconun arabirimi uygulaması gerekir <xref:System.Transactions.IPromotableSinglePhaseNotification> .

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Yöntemi daha sonra ilerletilmiş tek bir kalıcı kaynak listeleme için kullanılır. Liste gerektiği gibi ilerletilmiş, bu yöntem sağlar. Kayıt başarılı olursa, RM kendi iç işlemini oluşturur ve <xref:System.Transactions> işlemle ilişkilendirir. PSPE liste başarısız olursa, RM bunun yerine kullanarak listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> yöntemi. PSPE içinde listeleme sorunları, işlem zaten dağıtılmış bir işlem olduğunda ya da başka bir RM zaten bir PSPE kaydı gerçekleştirdiyse oluşabilir

Listeye kaydedildikten sonra, işlem yürütmek veya durdurmak için istemciler tarafından yapılan çağrılar, <xref:System.Transactions> yöntemini çağırarak veya sırasıyla Kaynak Yöneticisi çağrılara dönüştürülür <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> .

<xref:System.Transactions>İşlem hiçbir zaman yükseltme gerektirmez, işlem tamamlandığında, RM bir <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> bildirim alır. Daha sonra başlangıçta oluşturulan iç işlemi gerçekleştirebilir.

<xref:System.Transactions>İşlemin ilerlemesi gerekiyorsa (örneğin, birden çok RMs 'yi desteklemek için), <xref:System.Transactions> <xref:System.Transactions.ITransactionPromoter.Promote%2A> <xref:System.Transactions.ITransactionPromoter> arabirimin türetildiği arabirim üzerinde yöntemini çağırarak Resource Manager 'ı bilgilendirir <xref:System.Transactions.IPromotableSinglePhaseNotification> . Kaynak Yöneticisi daha sonra işlemi bir yerel işlemden (günlüğe kaydetme gerektirmeyen) bir DTC işlemine katılan bir işlem nesnesine dönüştürür ve bunu zaten yapılmış olan iş ile ilişkilendirir. İşlemin kaydedilmesi istendiğinde, işlem yöneticisi, <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> bildirim, yükseltme sırasında oluşturduğu dağıtılmış işlemi kaydeden Kaynak Yöneticisi 'ne hala gönderilir.

> [!NOTE]
> İşlem için **işlenen** izlemeler (ilerletilen Işlemde bir işleme çağrıldığında oluşturulur), DTC IŞLEMININ etkinlik kimliğini içerir.

Yönetim ilerletme hakkında daha fazla bilgi için bkz. [Işlem yönetimi yükseltme](transaction-management-escalation.md).

## <a name="transaction-management-escalation-scenario"></a>İşlem yönetimi Ilerletme senaryosu

Aşağıdaki senaryoda, <xref:System.Data> Resource Manager için ' Proxy ' olarak ad alanı kullanılarak dağıtılmış bir işlem için bir yükseltme gösterilmektedir. Bu senaryoda, <xref:System.Data> CN1 veritabanına zaten bir bağlantı olduğunu ve uygulamanın başka bir bağlantıyı (CN2) dahil etmek istediğini varsayar <xref:System.Data> . İşlem, tam dağıtılmış iki aşamalı işleme işlemi olarak DTC 'ye ilerletilmiş olmalıdır.

Bu senaryoda

1. CN1 işlemi, <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> işlem içine Enlist yöntemine çağrı yapıyor. Sonra, işlem hala yereldir ve işlemde başka bir promotable konusu yok, bu nedenle <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> çağrı başarılı olur.

2. İkinci bağlantı CN2 çağırır olduğunda <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, ilgili başka bir promotable liste olduğundan çağrı başarısız olur. Bu nedenle CN2 'in SQL 'e geçebilmesi için bir DTC işlemi alması gerekir. Bunu yapmak için, <xref:System.Transactions.TransactionInterop> SQL 'e verilen işlem biçimini oluşturmak için sınıfı tarafından sağlanan yöntemlerden birini kullanır.

3. <xref:System.Transactions>çağrıları <xref:System.Transactions.ITransactionPromoter.Promote%2A> yöntemi <xref:System.Transactions.ITransactionPromoter> CN1 tarafından uygulanan arabirimi.

4. Bu noktada, CN1, SQL 2005 ve 'e özgü bazı mekanizmayı kullanarak işlemi ilerletir <xref:System.Data> .

5. Yönteminden dönüş değeri, <xref:System.Transactions.ITransactionPromoter.Promote%2A> işlem için bir yayma belirteci içeren bir bayt dizisidir. <xref:System.Transactions>Bu yayma belirtecini, yerel işlem ile birleştirebilmesi için bir DTC işlemi oluşturmak için kullanır.

6. Bu noktada, CN2 <xref:System.Transactions.TransactionInterop> IŞLEMINI SQL 'e geçirmek için yöntemlerinden birini çağırmadan alınan verileri kullanabilirsiniz.

7. Artık, her ikisi de bir DTC dağıtılmış işleminde kaydedilir.

## <a name="single-phase-commit-optimization"></a>Tek aşaması yürütme en iyi hale getirme

Tek aşaması yürütme protokol tüm güncelleştirmeleri herhangi bir açık işbirliği tamamlanır olarak çalışma zamanında daha etkilidir. Bu iyileştirmeden yararlanmak için, <xref:System.Transactions.ISinglePhaseNotification> veya yöntemini kullanarak bir işlemde kaynak ve listeleme arabirimini kullanarak bir Resource Manager uygulamanız gerekir <xref:System.Transactions.Transaction.EnlistDurable%2A> <xref:System.Transactions.Transaction.EnlistVolatile%2A> . Özellikle, tek bir aşama işlemenin gerçekleştirildiğinden emin olmak için *EnlistmentOptions* parametresi değerine eşit olmalıdır <xref:System.Transactions.EnlistmentOptions.None> .

Bu yana <xref:System.Transactions.ISinglePhaseNotification> arabirimi türetilir <xref:System.Transactions.IEnlistmentNotification> arabirim, RM tek aşaması yürütme için uygun değilse, bunu iki aşaması yürütme bildirimleri almaya devam. RM, <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> TM 'den bir bildirim alırsa, işlem için gerekli olan çalışmayı gerçekleştirmeyi denemeli ve işlem,, <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A> ya da <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A> <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> yöntemi <xref:System.Transactions.SinglePhaseEnlistment> parametre üzerinde çağırarak işlem yöneticisini kendisine bilgilendirmelidir. Yanıtın <xref:System.Transactions.Enlistment.Done%2A> liste bu aşamada üzerinde salt okunur semantiği anlamına gelir. Bu nedenle, değil yanıt <xref:System.Transactions.Enlistment.Done%2A> ek olarak diğer yöntemleri.

Yalnızca bir geçici kayıt varsa ve dayanıklı bir kayıt yoksa, geçici liste SPC bildirimini alır. Geçici kayıtlar ve yalnızca bir dayanıklı kayıt varsa, geçici kayıtlar 2PC 'yi alır. Tamamlandığında, kalıcı liste SPC alır.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](enlisting-resources-as-participants-in-a-transaction.md)
- [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](committing-a-transaction-in-single-phase-and-multi-phase.md)
