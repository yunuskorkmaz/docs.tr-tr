---
title: Katılımcı bir işlemde kaynakları kaydetme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
ms.openlocfilehash: 98872bd3ccddb1696b37eace0e28156cdbe002dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366107"
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>Katılımcı bir işlemde kaynakları kaydetme

Bir işlemde katılan her kaynak eylemlerini bir işlem yöneticisi tarafından düzenlenir bir kaynak yöneticisi tarafından yönetilir. İşbirliği İşlem Yöneticisi aracılığıyla bir işlemde kayıtlı aboneleri için verilen bildirimleri üzerinden yapılır.

Bu konu nasıl bir kaynak (veya birden fazla kaynak) bir işlem, yanı sıra liste farklı türde kaydedilebilir kapsar. [Tek aşamalı ve çok aşamalı bir işlem Sistemi'ne](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md) konuyu kapsayan nasıl işlem taahhüt kayıtlı kaynakları arasında Eşgüdümlü olabilir.

## <a name="enlisting-resources-in-a-transaction"></a>Bir işlemde kaynakları kaydetme

Bir işlemde bir kaynak için sırada bu işleme gerekir. <xref:System.Transactions.Transaction> Sınıfı tanımlayan bir dizi yöntem adları ile başlayan **Enlist** bu işlevselliği sağlar. Farklı **Enlist** yöntemleri karşılık farklı türde bir kaynak yöneticisi olabilir liste için. Özellikle, kullandığınız <xref:System.Transactions.Transaction.EnlistVolatile%2A> geçici kaynaklar için yöntemleri ve <xref:System.Transactions.Transaction.EnlistDurable%2A> kalıcı kaynaklar için yöntem. Süreklilik (veya tersine volatility) kaynak yöneticisi kaynak yöneticisi hatası kurtarma destekleyip başvuruyor. Bir kaynak yöneticisi hatası kurtarma destekliyorsa, aşama 1 sırasında veri kalıcı depolama devam (Hazırla) sağlayacak şekilde kaynak yöneticisi kalırsa, onu kurtarma sonra işlemi yeniden listeleme ve bildirimlere dayalı uygun eylemleri gerçekleştirin TM alınan. Genel olarak, geçici kaynak yöneticileri bir bellek içi veri yapısı (örneğin, bir bellek içi hareket gerçekleşti-karma tablosu) gibi geçici kaynaklarını yönetmek ve kalıcı kaynak yöneticileri daha kalıcı bir yedekleme deposu sahip kaynakları yönetin (örneğin, bir Veritabanı) yedekleme deposu ayarlanmış olan bir disktir.

Kullanılacak karar sonra kolaylık <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> , kaynağın süreklilik desteğini tabanlı yöntemi, iki aşaması yürütme içinde (2PC) uygulayarak katılmak için kaynak listeleme <xref:System.Transactions.IEnlistmentNotification> , kaynak yöneticisi için arabirim. 2PC hakkında daha fazla bilgi için bkz. [tek aşamalı ve çok aşamalı bir işlem Sistemi'ne](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md).

Tek bir katılımcı çağırarak birden fazla bu iletişim kuralları için listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> ve <xref:System.Transactions.Transaction.EnlistVolatile%2A> birden çok kez.

### <a name="durable-enlistment"></a>Kalıcı liste

<xref:System.Transactions.Transaction.EnlistDurable%2A> Yöntemleri kalıcı bir kaynak olarak işlem katılım için bir kaynak yöneticisi listeleme için kullanılır.  Kalıcı Kaynak Yöneticisi ortasında bir işlem alınırsa, reenlisting tarafından tekrar çevrimiçi olana sonra onu kurtarma gerçekleştirebileceğiniz beklenir (kullanarak <xref:System.Transactions.TransactionManager.Reenlist%2A> yöntemi), bu katılımcı oluştu ve belirtmiyor tüm işlemlerde 2. Aşama tamamlandı ve çağrı <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> kurtarma işlemini tamamladıktan sonra. Kurtarma hakkında daha fazla bilgi için bkz. [kurtarma gerçekleştirme](../../../../docs/framework/data/transactions/performing-recovery.md).


  <xref:System.Transactions.Transaction.EnlistDurable%2A> Tüm getirin yöntemleri bir <xref:System.Guid> kendi ilk parameTRe olarak nesne. <xref:System.Guid> Hareket yöneticisi tarafından kalıcı bir liste belirli kaynak yöneticisi ile ilişkilendirmek için kullanılır. Bu nedenle, bu kaynak yöneticisi tutarlı bir şekilde aynı kullandığını zorunludur <xref:System.Guid> kendisi arasında bile yeniden başlatıldığında farklı kaynak yöneticileri belirlemek için Aksi takdirde kurtarma başarısız olabilir.

İkinci parametresi <xref:System.Transactions.Transaction.EnlistDurable%2A> için işlem bildirimi almak için kaynak yöneticisi uygulayan nesnenin bir başvuru yöntemdir. Kullandığınız aşırı yüklemesi, kaynak yöneticisi tek aşaması yürütme (SPC) en iyi duruma getirme destekleyip desteklemediğini hareket yöneticisi bildirir. Çoğu zaman uygulamak <xref:System.Transactions.IEnlistmentNotification> Two-Phase (2PC) içinde yürütme katılmak için arabirim. Kaydetme işlemi iyileştirmek istiyorsanız, ancak, uygulama düşünebilirsiniz <xref:System.Transactions.ISinglePhaseNotification> SPC için arabirim. SPC hakkında daha fazla bilgi için bkz. [tek aşamalı ve çok aşamalı bir işlem Sistemi'ne](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md) ve [tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).

Üçüncü parameTRe bir <xref:System.Transactions.EnlistmentOptions> numaralandırma değeri ya da olabilir, <xref:System.Transactions.EnlistmentOptions.None> veya <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>. Değer ayarlanmışsa <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>, liste hazırla bildirim alma İşlem Yöneticisi'nden sonra ek kaynak yöneticileri listeleyebilir. Ancak, bu liste türü tek aşaması yürütme en iyi hale getirme için uygun değil bilmeniz gerekir.

### <a name="volatile-enlistment"></a>Geçici liste

Gibi bir önbellek kullanarak listeleme geçici kaynaklarını yönetme katılımcıları <xref:System.Transactions.Transaction.EnlistVolatile%2A> yöntemleri. Bu tür nesneler bir işlem sonucunu elde veya bunlar sonra bir sistem hatası katılmak herhangi bir işlem durumunu kurtarma mümkün olmayabilir.

Bir bellek içi, geçici kaynak yönettiği, yukarıda belirtildiği gibi bir kaynak yöneticisi geçici bir liste hale getireceği. Kullanmanın faydaları birini <xref:System.Transactions.Transaction.EnlistVolatile%2A> olan işlemin gereksiz bir yükseltme zorlamaz. İşlem yükseltme hakkında daha fazla bilgi için bkz. [işlem yönetim yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md) konu. Liste işlem yöneticisi tarafından nasıl işlendiğini içinde her iki fark gelir geçiciliğine kaydetme hareket yöneticisi tarafından Kaynak Yöneticisi'nin beklenen yanı sıra. Geçici Kaynak Yöneticisi kurtarma gerçekleştirmez olmasıdır. 
  <xref:System.Transactions.Transaction.EnlistVolatile%2A> Yöntemleri olması değil bir <xref:System.Guid> parameTResi, çünkü geçici Kaynak Yöneticisi kurtarma gerçekleştirmez ve değil çağırırsınız <xref:System.Transactions.TransactionManager.Reenlist%2A> gereken yöntemi bir <xref:System.Guid>.

Kalıcı kayıtlar gibi ile hareket yöneticisi ile listeleme için kullandığınız hangi aşırı yükleme yöntemi, kaynak yöneticisi tek aşaması yürütme en iyi duruma getirme destekleyip desteklemediğini gösterir. Geçici Kaynak Yöneticisi kurtarma gerçekleştiremezsiniz dolayı hiçbir kurtarma bilgi hazırla aşamasında geçici bir liste için yazılır. Bu nedenle, çağırma <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> yöntemi sonuçlanıyor bir <xref:System.InvalidOperationException>.

Aşağıdaki örnekte, böyle bir nesne katılımcı kullanarak işlem listeleme gösterilmiştir <xref:System.Transactions.Transaction.EnlistVolatile%2A> yöntemi.

[!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
[!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]

### <a name="optimizing-performance"></a>Performansı en iyi duruma getirme


  <xref:System.Transactions.Transaction> Sınıfı sağlar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> bir Promotable tek aşaması liste'nı (PSPE) listeleme yöntemi. Bu bir kalıcı Kaynak Yöneticisi (ana bilgisayar ve "daha sonra gerekirse MSDTC tarafından yönetilmek üzere ilerletilmiş bir işlem sahibi" RM) sağlar. Bunun hakkında daha fazla bilgi için bkz. [tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)
- [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
