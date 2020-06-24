---
title: Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme
description: Bir .NET işleminde katılımcı olarak listeleme kaynakları. Bir işlemdeki her kaynak bir işlem yöneticisi tarafından koordine edilen bir kaynak yöneticisi tarafından yönetilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
ms.openlocfilehash: c3c777593750b3a4f05ae97ed6e26e19f58e4d72
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141881"
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme

Bir işleme katılan her kaynak, eylemleri bir işlem yöneticisi tarafından koordine edilen bir kaynak yöneticisi tarafından yönetilir. Koordinasyon, işlem Yöneticisi aracılığıyla bir işlemde kayıtlı olan abonelere verilen bildirimler aracılığıyla yapılır.

Bu konu, bir kaynağın (veya birden fazla kaynağın) bir işlemde nasıl ve farklı kayıt türlerine nasıl kayyüklenebileceğini ele alır. [Tek aşamalı ve çok aşamalı bir Işlem yürütmek](committing-a-transaction-in-single-phase-and-multi-phase.md) , işlem taahhüdünün kayıtlı kaynaklar arasında nasıl koordine edilebilir olduğunu içerir.

## <a name="enlisting-resources-in-a-transaction"></a>Bir Işlemdeki kaynakları kaydetme

Bir kaynağın bir işleme katılmasını sağlamak için, işlem içinde listelenmesi gerekir. <xref:System.Transactions.Transaction>Sınıfı, bu işlevselliği sağlayan, adları **Listeleme** ile başlayan bir yöntemler kümesini tanımlar. Farklı **Listeleme** yöntemleri, bir kaynak yöneticisi 'nin sahip olabileceği farklı kayıt türlerine karşılık gelir. Özellikle, kullandığınız <xref:System.Transactions.Transaction.EnlistVolatile%2A> geçici kaynaklar için yöntemleri ve <xref:System.Transactions.Transaction.EnlistDurable%2A> kalıcı kaynaklar için yöntem. Süreklilik (veya tersine volatility) kaynak yöneticisi kaynak yöneticisi hatası kurtarma destekleyip başvuruyor. Bir Kaynak Yöneticisi hata kurtarmayı destekliyorsa, Aşama 1 sırasında verileri dayanıklı depolamaya (hazırla) devam ettirir. Bu, Resource Manager kapalıysa, kurtarma sonrasında işlemi yeniden listeleme ve TM 'den alınan bildirimlere göre uygun eylemleri gerçekleştirmenize olanak sağlar. Genel olarak, geçici kaynak yöneticileri bellek içi veri yapısı (örneğin, bellek içi bir işlem Hashtable) gibi geçici kaynakları yönetir ve dayanıklı kaynak yöneticileri, daha kalıcı bir yedekleme deposuna sahip kaynakları (örneğin, yedekleme deposu disk olan bir veritabanı) yönetir.

Kullanılacak karar sonra kolaylık <xref:System.Transactions.Transaction.EnlistDurable%2A> veya <xref:System.Transactions.Transaction.EnlistVolatile%2A> , kaynağın süreklilik desteğini tabanlı yöntemi, iki aşaması yürütme içinde (2PC) uygulayarak katılmak için kaynak listeleme <xref:System.Transactions.IEnlistmentNotification> , kaynak yöneticisi için arabirim. 2PC hakkında daha fazla bilgi için bkz. [tek aşamalı ve çok aşamalı bir işlem](committing-a-transaction-in-single-phase-and-multi-phase.md)yürütme.

Tek bir katılımcı çağırarak birden fazla bu iletişim kuralları için listeleme <xref:System.Transactions.Transaction.EnlistDurable%2A> ve <xref:System.Transactions.Transaction.EnlistVolatile%2A> birden çok kez.

### <a name="durable-enlistment"></a>Kalıcı liste

<xref:System.Transactions.Transaction.EnlistDurable%2A>Yöntemler, bir kaynak yöneticisinin işlem içinde sürekli bir kaynak olarak katılımını yapmak için kullanılır.  Kalıcı bir kaynak yöneticisinin bir işlemin ortasında aşağı doğru olması bekleniyorsa, bu, katılımcı olduğu tüm işlemlerde (yöntemini kullanarak) yeniden çevrimiçi duruma getirildikten sonra kurtarma işlemini gerçekleştirebilir, ancak <xref:System.Transactions.TransactionManager.Reenlist%2A> 2. aşama tamamlanamamıştı ve <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> kurtarma işlemini tamamladıktan sonra çağrı yapabilir. Kurtarma hakkında daha fazla bilgi için bkz. [Kurtarma gerçekleştirme](performing-recovery.md).

<xref:System.Transactions.Transaction.EnlistDurable%2A> Tüm getirin yöntemleri bir <xref:System.Guid> kendi ilk parameTRe olarak nesne. , <xref:System.Guid> Belirli bir kaynak yöneticisiyle dayanıklı bir kaydı ilişkilendirmek için işlem yöneticisi tarafından kullanılır. Bu nedenle, bu kaynak yöneticisi tutarlı bir şekilde aynı kullandığını zorunludur <xref:System.Guid> kendisi arasında bile yeniden başlatıldığında farklı kaynak yöneticileri belirlemek için Aksi takdirde kurtarma başarısız olabilir.

Yöntemin ikinci parametresi, <xref:System.Transactions.Transaction.EnlistDurable%2A> Resource Manager 'ın işlem bildirimlerini almak için uyguladığı nesnesine bir başvurudur. Kullandığınız aşırı yükleme, Resource Manager 'ın tek aşamalı Işleme (SPC) iyileştirmesini destekleyip desteklemediğini işlem yöneticisine bildirir. Çoğu zaman uygulamak <xref:System.Transactions.IEnlistmentNotification> Two-Phase (2PC) içinde yürütme katılmak için arabirim. Kaydetme işlemi iyileştirmek istiyorsanız, ancak, uygulama düşünebilirsiniz <xref:System.Transactions.ISinglePhaseNotification> SPC için arabirim. SPC hakkında daha fazla bilgi için bkz. tek aşamalı [işleme ve promotable tek aşamalı bildirimi kullanarak](optimization-spc-and-promotable-spn.md) [bir işlemi tek aşamada ve çok aşamalı](committing-a-transaction-in-single-phase-and-multi-phase.md) ve en iyi duruma getirme.

Üçüncü parameTRe bir <xref:System.Transactions.EnlistmentOptions> numaralandırma değeri ya da olabilir, <xref:System.Transactions.EnlistmentOptions.None> veya <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>. Değer olarak ayarlanırsa <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired> , kayıt, işlem yöneticisi 'Nden hazırlama bildirimi alındıktan sonra ek kaynak yöneticileri listesine eklenebilir. Ancak, bu liste türü tek aşaması yürütme en iyi hale getirme için uygun değil bilmeniz gerekir.

### <a name="volatile-enlistment"></a>Geçici liste

Gibi bir önbellek kullanarak listeleme geçici kaynaklarını yönetme katılımcıları <xref:System.Transactions.Transaction.EnlistVolatile%2A> yöntemleri. Bu tür nesneler bir işlemin sonucunu elde edemeyebilir veya bir sistem hatasından sonra katıldıkları herhangi bir işlemin durumunu kurtaramayabilir.

Bir bellek içi, geçici kaynak yönettiği, yukarıda belirtildiği gibi bir kaynak yöneticisi geçici bir liste hale getireceği. Kullanmanın avantajlarından biri, <xref:System.Transactions.Transaction.EnlistVolatile%2A> işlemin gereksiz bir şekilde ilerlemesini zorlamaktır. İşlem yükseltme hakkında daha fazla bilgi için bkz. [Işlem yönetimi ilerletme](transaction-management-escalation.md) konusu. Listenin her ikisi de kayıt işleminin işlem yöneticisi tarafından nasıl işlendiği ve kaynak yöneticisinin işlem yöneticisi tarafından beklenildiği bir farklılık anlamına gelir. Geçici Kaynak Yöneticisi kurtarma gerçekleştirmez olmasıdır. <xref:System.Transactions.Transaction.EnlistVolatile%2A> Yöntemleri olması değil bir <xref:System.Guid> parameTResi, çünkü geçici Kaynak Yöneticisi kurtarma gerçekleştirmez ve değil çağırırsınız <xref:System.Transactions.TransactionManager.Reenlist%2A> gereken yöntemi bir <xref:System.Guid>.

Kalıcı kayıtlar sayesinde, listeleme için kullandığınız herhangi bir aşırı yükleme yöntemi, Resource Manager 'ın tek aşamalı Işleme iyileştirmesini destekleyip desteklemediğini belirtir. Geçici Kaynak Yöneticisi kurtarma gerçekleştiremezsiniz dolayı hiçbir kurtarma bilgi hazırla aşamasında geçici bir liste için yazılır. Bu nedenle, çağırma <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> yöntemi sonuçlanıyor bir <xref:System.InvalidOperationException>.

Aşağıdaki örnek, yöntemi kullanılarak bir işlem için bir nesne için bir katılımcı olarak nasıl listelenmeyi gösterir <xref:System.Transactions.Transaction.EnlistVolatile%2A> .

[!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
[!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]

### <a name="optimizing-performance"></a>Performansı en iyi duruma getirme

<xref:System.Transactions.Transaction> Sınıfı sağlar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> bir Promotable tek aşaması liste'nı (PSPE) listeleme yöntemi. Bu, dayanıklı bir kaynak yöneticisinin (RM), daha sonra gerekirse MSDTC tarafından yönetilmek üzere ilerletilebilecek bir işlem barındırarak "sahip" olmasını sağlar. Bunun hakkında daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](optimization-spc-and-promotable-spn.md)
- [Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme](committing-a-transaction-in-single-phase-and-multi-phase.md)
