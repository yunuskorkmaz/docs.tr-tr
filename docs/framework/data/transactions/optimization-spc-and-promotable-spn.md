---
title: Tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme
ms.date: 03/30/2017
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
ms.openlocfilehash: 73340f5f65de1d743e046cf669258ab5f6c66298
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371209"
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>Tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme

Bu konu tarafından sağlanan mekanizmaları açıklayan <xref:System.Transactions> performansını iyileştirmek için altyapı.

## <a name="promotable-single-phase-enlistment"></a>Liste promotable tek aşaması

<xref:System.Transactions> Altyapı administrates bir işlem en çok tek bir kalıcı kaynak veya birden çok geçici kaynakları içerir tek bir uygulama etki alanı. Bu yana <xref:System.Transactions> altyapısını kullanan yalnızca içi uygulama etki alanı çağrıları, en iyi performans ve performans verir.

Ancak, başka bir nesneye (işlem ve makine sınırlarında dahil) başka bir uygulama etki alanında aynı bilgisayarda işlem sağlanırsa veya başka bir kalıcı Kaynak Yöneticisi, listeleme olsaydı <xref:System.Transactions> altyapı MSDTC tarafından yönetilmek üzere işlem otomatik olarak iletir. MSDTC tarafından yönetilen bir işlem tarafından yönetilen bir olarak performance-wise değil <xref:System.Transactions> altyapı.

Performansı iyileştirmek için <xref:System.Transactions> altyapı sağlar Promotable tek aşaması liste (farklı uygulama etki alanı, işlem veya'na katılmak için makine, bulunan tek bir uzak kalıcı kaynağı, izin veren PSPE) bir <xref:System.Transactions> bir MSDTC işlem ilerletilmiş için bu neden olmadan işlem. Bu kaynak yöneticisi (RM), barındırma ve "daha sonra bir dağıtılmış işlem (veya MSDTC işlem) gerekirse ilerletilmiş bir işlem sahibi". Bu MSDTC kullanarak olasılığı azaltır.

Bu belirli kaynak yöneticisi genellikle kendi iç olmayan dağıtılmış işlemler var ve çalışma zamanında dağıtılmış işlemler için bu işlemleri dönüştürme desteği gerektirir. Örneğin, SQL Server 2005 böyle bir kaynak yöneticisidir. Böyle bir durumda <xref:System.Transactions> altyapı yalnızca izleme işlemi için bir yükseltme gereksinimini tarafından edilgen yönetim rolü alır. Arasındaki etkileşimi desteklemek için <xref:System.Transactions> altyapı ve Kaynak Yöneticisi, arabirim uygulamak için ikinci gereksinimlerini <xref:System.Transactions.IPromotableSinglePhaseNotification>.

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Yöntemi daha sonra ilerletilmiş tek bir kalıcı kaynak listeleme için kullanılır. Liste gerektiği gibi ilerletilmiş, bu yöntem sağlar. Liste başarılı olursa, RM kendi iç işlem oluşturur ve bunu ile ilişkilendirir <xref:System.Transactions> işlem. PSPE liste başarısız olursa, RM bunun yerine kullanarak listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> yöntemi. PSPE listeleme hataları işlem dağıtılmış bir işlem olduğunda veya başka bir RM zaten bir PSPE liste gerçekleştirdiğinde meydana gelir

İstemciler tarafından tamamlama veya iptal için kayıtlı sonra çağıran <xref:System.Transactions> işlem dönüştürülür çağrılarına üzerinde Kaynak Yöneticisi çağırarak <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> yöntemi veya <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A> sırasıyla.

Varsa <xref:System.Transactions> işlem yükseltme, hiçbir zaman gerekiyor işlem tamamlandığında RM alır bir <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> bildirim. Ayrıca, başlangıçta oluşturulmuş iç işlem sonra onaylayabilirsiniz.

Varsa <xref:System.Transactions> işlem ilerletilmiş gerekir (örn, birden çok RMs desteklemek için), <xref:System.Transactions> çağırarak Kaynak Yöneticisi bildiren <xref:System.Transactions.ITransactionPromoter.Promote%2A> metodunda <xref:System.Transactions.ITransactionPromoter> arabirim <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi türer. Kaynak Yöneticisi sonra işlem dahili (, günlük gerektirmeyen) yerel bir hareketi DTC işlemde katılan uyumlu olan ve önceden çalışmanın ile ilişkilendirir işlem nesnesi için dönüştürür. İşlem işleme sorulduğunda, hareket yöneticisi yine de gönderir <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> yükseltme sırasında oluşturulan dağıtılmış işlem yürütmeleri kaynak yöneticisi için bildirim.

> [!NOTE]
> **TransactionCommitted** DTC işlem etkinlik kimliği (bir tamamlama ilerletilmiş işlem çağrıldığında, oluşturulan) izlemeleri içerir.

Yönetim yükseltme hakkında daha fazla bilgi için bkz. [işlem yönetim yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md).

## <a name="transaction-management-escalation-scenario"></a>İşlem yönetimi yükseltme senaryosu

Bir yükseltme kullanarak bir dağıtılmış işlem aşağıdaki senaryoyu gösterir <xref:System.Data> ad alanı 'proxy' için kaynak yöneticisi olarak. Bu senaryoyu olduğunu zaten bir varsayar <xref:System.Data> CN1, veritabanı bağlantısı dahil işlemde ve başka ilgili uygulama istediği <xref:System.Data> bağlantı, CN2. İşlem bir tam dağıtılmış iki aşamalı tamamlama işlem DTC için ilerletilmiş gerekir.

Bu senaryoda

1. CN1 çağrıları <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> işleme için yöntemi. Daha sonra hala yerel bir işlemdir ve işlem promotable diğer liste vardır. Bu nedenle <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> araması başarılı.

2. İkinci bağlantı CN2 çağırır olduğunda <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>, ilgili başka bir promotable liste olduğundan çağrı başarısız olur. Bu nedenle, CN2 DTC işlem SQL iletmek için almanız gerekir. Bunu yapmak için bunu tarafından sağlanan yöntemlerden birini kullanır <xref:System.Transactions.TransactionInterop> SQL için belirtilen işlem bir biçimde üretmek için sınıf.

3. <xref:System.Transactions>çağrıları <xref:System.Transactions.ITransactionPromoter.Promote%2A> yöntemi <xref:System.Transactions.ITransactionPromoter> CN1 tarafından uygulanan arabirimi.

4. Bu noktada, SQL 2005 belirli bazı mekanizmayı kullanarak CN1 işlem kuşkulandığı ve <xref:System.Data>.

5. Dönüş değeri <xref:System.Transactions.ITransactionPromoter.Promote%2A> yöntemdir işlem için bir yayma belirteci içeren bayt dizisi. <xref:System.Transactions> yerel işlem dahil edebilirsiniz bir DTC hareket oluşturmak için bu yayma belirteci kullanır.

6. Bu noktada, CN2 tarafından yöntemlerden birini çağırma alınan veri kullanabilirsiniz <xref:System.Transactions.TransactionInterop> SQL işlem geçirilecek.

7. Şimdi, hem bir dağıtılmış DTC işlemde kayıtlıdır.

## <a name="single-phase-commit-optimization"></a>Tek aşaması yürütme en iyi hale getirme

Tek aşaması yürütme protokol tüm güncelleştirmeleri herhangi bir açık işbirliği tamamlanır olarak çalışma zamanında daha etkilidir. Bu en iyi duruma getirme yararlanmak için bir Kaynak Yöneticisi kullanarak uygulamalıdır <xref:System.Transactions.ISinglePhaseNotification> arabirim için kaynak ve hareket kullanarak listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> yöntemi. Özellikle, *EnlistmentOptions* parametresi eşit <xref:System.Transactions.EnlistmentOptions.None> tek aşaması yürütme gerçekleştirilen emin olmak için.

Bu yana <xref:System.Transactions.ISinglePhaseNotification> arabirimi türetilir <xref:System.Transactions.IEnlistmentNotification> arabirim, RM tek aşaması yürütme için uygun değilse, bunu iki aşaması yürütme bildirimleri almaya devam. RM alırsa bir <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> TM alınan bildirim, denemek için Kaydet ve işlem kaydedilmiş veya çağırarak döndürülmesine ise hareket yöneticisi gelenlere bilgilendirmek için gerekli iş yapmak <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A>, <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>, veya <xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A> metodunda <xref:System.Transactions.SinglePhaseEnlistment> parametresi. Yanıtın <xref:System.Transactions.Enlistment.Done%2A> liste bu aşamada üzerinde salt okunur semantiği anlamına gelir. Bu nedenle, değil yanıt <xref:System.Transactions.Enlistment.Done%2A> ek olarak diğer yöntemleri.

Yalnızca bir geçici liste ve kalıcı hiçbir liste ise, geçici liste SPC bildirim alır. Herhangi bir geçici listeler ve yalnızca bir kalıcı liste varsa, geçici listeler 2PC alırsınız. Tamamlandığında, kalıcı liste SPC alır.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
- [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
