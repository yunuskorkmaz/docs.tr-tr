---
title: Bir işlemde katılımcı olarak kaynakları kaydetme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
ms.openlocfilehash: cf7afb9fd255d9b67f40bc4e8c0685d727939972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>Bir işlemde katılımcı olarak kaynakları kaydetme
Bir işlem içinde katılan her bir kaynağın eylemlerini bir işlem yöneticisi tarafından düzenlenir kaynak yöneticisi tarafından yönetilir. Düzenleme İşlem Yöneticisi aracılığıyla bir işlemde listeye aboneleri için verilen bildirimleri yoluyla yapılır.  
  
 Bu konu, nasıl bir kaynak (veya birden çok kaynak) bir işlem, aynı zamanda kaydı farklı türde kaydedilebilir kapsar. [Tek aşamalı ve çok aşama işlemde yürüten](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md) konu kapsar nasıl işlem taahhüt kayıtlı kaynakları arasında Eşgüdümlü olabilir.  
  
## <a name="enlisting-resources-in-a-transaction"></a>Kaynakları bir işlemde kaydetme  
 Bir işlemde bir kaynak için sırayla işlem listesine gerekir. <xref:System.Transactions.Transaction> Sınıfı tanımlayan bir dizi yöntem ile başlar, adları **Enlist** bu işlevsellik sağlar. Farklı **Enlist** yöntemleri karşılık gelen bir Kaynak Yöneticisi'ni olabilir kaydı farklı türleri için. Özellikle, kullandığınız <xref:System.Transactions.Transaction.EnlistVolatile%2A> geçici kaynaklar için yöntemleri ve <xref:System.Transactions.Transaction.EnlistDurable%2A> kalıcı kaynaklar için yöntem. Süreklilik (veya tersine volatility) kaynak yöneticisi kaynak yöneticisi hatası kurtarma destekleyip başvuruyor. Kaynak Yöneticisi hatadan kurtarma destekliyorsa, aşama 1 sırasında verileri dayanıklı depolama devam (hazırlama) sağlayacak şekilde Kaynak Yöneticisi'ni kullanılamaz hale gelirse, Kurtarma sırasında işlemdeki yeniden listeleme ve bildirimlerini göre uygun eylemleri gerçekleştirin TM aldı. Genel olarak, geçici kaynak yöneticileri bir bellek içi veri yapısı (örneğin, bir bellek içi işlem yapılan işlem-hashtable) gibi volatile kaynakları yönetme ve dayanıklı kaynak yöneticileri yönetme daha kalıcı bir yedekleme deposu kaynakları (örneğin, bir Veritabanı), yedekleme deposu disktir.  
  
 Kullanılacak karar sonra kolaylık <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> , kaynağın süreklilik desteğini tabanlı yöntemi, iki aşaması yürütme içinde (2PC) uygulayarak katılmak için kaynak listeleme <xref:System.Transactions.IEnlistmentNotification> , kaynak yöneticisi için arabirim. 2PC hakkında daha fazla bilgi için bkz: [tek aşamalı ve çok aşama işlemde yürüten](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md).  
  
 Tek bir katılımcı çağırarak birden fazla bu iletişim kuralları için listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> ve <xref:System.Transactions.Transaction.EnlistVolatile%2A> birden çok kez.  
  
### <a name="durable-enlistment"></a>Kalıcı liste  
 <xref:System.Transactions.Transaction.EnlistDurable%2A> Yöntemleri dayanıklı bir kaynak olarak hareket katılım için kaynak yöneticisi listeleme için kullanılır.  Sağlam Kaynak Yöneticisi bir işlem gerçekleştiriyor alınırsa, reenlisting tarafından tekrar çevrimiçi olana sonra onu kurtarma gerçekleştirebileceğiniz bekleniyor (kullanarak <xref:System.Transactions.TransactionManager.Reenlist%2A> yöntemi), katılımcı olan ve belirtmiyor tüm işlemlerin tam Aşama 2 ve çağrı <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> kurtarma işlemi tamamlandıktan sonra. Kurtarma hakkında daha fazla bilgi için bkz: [kurtarma gerçekleştirme](../../../../docs/framework/data/transactions/performing-recovery.md).  
  
 <xref:System.Transactions.Transaction.EnlistDurable%2A> Tüm getirin yöntemleri bir <xref:System.Guid> kendi ilk parameTRe olarak nesne. <xref:System.Guid> İşlem yöneticisi tarafından dayanıklı kaydı belirli resource manager ile ilişkilendirmek için kullanılır. Bu nedenle, bu kaynak yöneticisi tutarlı bir şekilde aynı kullandığını zorunludur <xref:System.Guid> kendisi arasında bile yeniden başlatıldığında farklı kaynak yöneticileri belirlemek için Aksi takdirde kurtarma başarısız olabilir.  
  
 Öğesinin ikinci parametresi, <xref:System.Transactions.Transaction.EnlistDurable%2A> işlem bildirimleri almak için Kaynak Yöneticisi'ni uygulayan nesneye bir başvurusu yöntemidir. Kullandığınız aşırı işlem yöneticisi, Kaynak Yöneticisi'ni tek aşaması Yürüt (SPC) en iyi duruma getirme destekleyip desteklemediğini bildirir. Çoğu zaman uygulamak <xref:System.Transactions.IEnlistmentNotification> Two-Phase (2PC) içinde yürütme katılmak için arabirim. Kaydetme işlemi iyileştirmek istiyorsanız, ancak, uygulama düşünebilirsiniz <xref:System.Transactions.ISinglePhaseNotification> SPC için arabirim. SPC hakkında daha fazla bilgi için bkz: [tek aşamalı ve çok aşama işlemde yürüten](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md) ve [tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 Üçüncü parameTRe bir <xref:System.Transactions.EnlistmentOptions> numaralandırma değeri ya da olabilir, <xref:System.Transactions.EnlistmentOptions.None> veya <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>. Değer ayarlanmışsa <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>, kaydı İşlem Yöneticisi'nden hazırlık bildirim alma sırasında ek kaynak yöneticileri listeleyebilir. Ancak, bu liste türü tek aşaması yürütme en iyi hale getirme için uygun değil bilmeniz gerekir.  
  
### <a name="volatile-enlistment"></a>Geçici liste  
 Gibi bir önbellek kullanarak listeleme geçici kaynaklarını yönetme katılımcıları <xref:System.Transactions.Transaction.EnlistVolatile%2A> yöntemleri. Bu tür nesneleri bir işlem sonucunu elde etmek veya bir sistem hatasından sonra katıldıkları herhangi bir işlem durumunu kurtarmak mümkün olmayabilir.  
  
 Bir bellek içi, geçici kaynak yönettiği, yukarıda belirtildiği gibi bir kaynak yöneticisi geçici bir liste hale getireceği. Kullanmanın avantajlarından biri <xref:System.Transactions.Transaction.EnlistVolatile%2A> gereksiz bir yükseltme işlemi zorlamaz değil. İşlem yükseltme hakkında daha fazla bilgi için bkz: [işlem yönetimi yükseltme](../../../../docs/framework/data/transactions/transaction-management-escalation.md) konu. Volatilely kaydetme, hem bir fark kaydı işlem yöneticisi tarafından nasıl işleneceğini içinde olduğu anlamına gelir, kaynak yöneticisi işlem yöneticisi tarafından beklenen yanı sıra. Geçici Kaynak Yöneticisi kurtarma gerçekleştirmez olmasıdır. <xref:System.Transactions.Transaction.EnlistVolatile%2A> Yöntemleri olması değil bir <xref:System.Guid> parameTResi, çünkü geçici Kaynak Yöneticisi kurtarma gerçekleştirmez ve değil çağırırsınız <xref:System.Transactions.TransactionManager.Reenlist%2A> gereken yöntemi bir <xref:System.Guid>.  
  
 Dayanıklı kayıtlar gibi ile Kaynak Yöneticisi'ni tek aşaması yürütme iyileştirme destekleyip desteklemediğini listeleme için kullandığınız hangi aşırı yükleme yöntemi için işlem yöneticisi gösterir. Geçici Kaynak Yöneticisi kurtarma gerçekleştiremezsiniz dolayı hiçbir kurtarma bilgi hazırla aşamasında geçici bir liste için yazılır. Bu nedenle, çağırma <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> yöntemi sonuçlanıyor bir <xref:System.InvalidOperationException>.  
  
 Aşağıdaki örnek, böyle bir nesnenin kullanarak işlem Katılımcısı olarak listeleme gösterilmiştir <xref:System.Transactions.Transaction.EnlistVolatile%2A> yöntemi.  
  
 [!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
 [!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]  
  
### <a name="optimizing-performance"></a>Performansı en iyi duruma getirme  
 <xref:System.Transactions.Transaction> Sınıfı sağlar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> bir Promotable tek aşaması liste'nı (PSPE) listeleme yöntemi. Bu sağlam Kaynak Yöneticisi (RM barındırmak ve "gerekirse MSDTC tarafından yönetilecek daha sonra ilerletilen bir işlem kendi") sağlar. Bunun hakkında daha fazla bilgi için bkz: [tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
