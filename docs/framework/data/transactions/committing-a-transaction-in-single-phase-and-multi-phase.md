---
title: Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
description: .NET 'teki bir veya iki aşamada işlem yürütme hakkında bilgi edinin. İşlem birden fazla kaynak içeriyorsa, iki aşamalı bir işleme (2PC) gerçekleştirilmesi gerekir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: f46c22294da4db017eceb0bfd0b5cb2bb093c0b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147417"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme

Bir işlemde kullanılan her kaynak, eylemleri bir işlem Yöneticisi (TM) tarafından koordine edilen bir kaynak yöneticisi (RM) tarafından yönetilir. [Kaynakları bir işlem konusunun katılımcıları olarak listelemek](enlisting-resources-as-participants-in-a-transaction.md) , bir kaynağın (veya birden fazla kaynağın) bir işlemde nasıl kaydedilebilir olduğunu tartışır. Bu konu başlığı altında, işlem taahhüdünün kayıtlı kaynaklar arasında nasıl koordine edilebilir.  
  
 İşlemin sonunda, uygulama, işlemi taahhüt veya geri alınacak şekilde ister. İşlem Yöneticisi, bazı kaynak yöneticilerinin işlemi geri almak için oylama yaparken yürütülmesi için oylama gibi riskleri ortadan kaldırmalıdır.  
  
 İşlem, birden fazla kaynak içeriyorsa, iki aşamalı bir işleme (2PC) uygulamanız gerekir. İki aşamalı tamamlama Protokolü (hazırlama aşaması ve yürütme aşaması), işlem sona erdiğinde tüm kaynaklardaki tüm değişikliklerin tamamen kaydedilmiş veya tam olarak geri alındığı durumlarda sağlar. Tüm katılımcıları sonra sonucunu bildirilir. İki aşamalı tamamlama protokolü hakkında ayrıntılı bir tartışma için lütfen "*Işlem işleme: kavramlar ve teknikler (veri yönetimi sistemlerdeki Morgan Kaumann serisi) ISBN: 1558601902*" adlı Jim Gray adlı kitaba bakın.  
  
 Ayrıca, tek aşamalı Işleme protokolüne bir parça ayırarak işlem performansını iyileştirebilirsiniz. Daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).  
  
 Yalnızca bir işlemin sonucu hakkında bilgilendirilmek istiyorsanız ve oylama 'ye katılmak istemiyorsanız, olaya kaydolmanız gerekir <xref:System.Transactions.Transaction.TransactionCompleted> .  
  
## <a name="two-phase-commit-2pc"></a>İki aşamalı kayıt (2PC)  

 İlk işlem aşamasında, işlem yöneticisi her bir işlemin kaydedilip edilmeyeceğini veya geri döndürülüp döndürülmeyeceğini anlamak için her bir kaynağı sorgular. İkinci işlem aşamasında, işlem yöneticisi her bir kaynağa kendi sorgularının sonucunu bildirir ve gerekli temizleme işlemlerini gerçekleştirmesine izin verir.  
  
 Bu tür bir işleme katılmak için bir kaynak yöneticisi, <xref:System.Transactions.IEnlistmentNotification> BIR 2PC SıRASıNDA TM olarak çağrılan yöntemler sağlayan arabirimini uygulamalıdır.  Aşağıdaki örnek, bu tür uygulaması örneği gösterir.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Aşama (Aşama 1) hazırla  

 Uygulamadan bir istek alındıktan sonra <xref:System.Transactions.CommittableTransaction.Commit%2A> , işlem yöneticisi <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> her bir kaynağın işlem üzerindeki oylamasını elde etmek için, her bir kayıtlı kaynaktaki yöntemini çağırarak, tüm kayıtlı katılımcıların hazırlama aşamasına başlar.  
  
 Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.  
  
```csharp
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 Dayanıklı Kaynak Yöneticisi bu çağrıyı aldığında, işlemin kurtarma bilgilerini (özelliği alarak kullanılabilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> ) ve işleme sırasında işlemi tamamlamak için hangi bilgilerin gerekli olduğunu günlüğe kaydetmelidir. Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.  
  
 RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi. Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı. <xref:System.Transactions.PreparingEnlistment>Hazırlama aşamasında bu yöntemi geri çağırmada çağırırsanız, TM 'ye bir salt okuma listesi olduğunu bildirir (yani, işlem korumalı verileri okuyabilen ancak güncelleştiremediğini belirten kaynak yöneticileri) ve RM, işlem yöneticisi 'nden, Aşama 2 ' deki işlemin sonucuna göre başka hiçbir bildirim almaz.  
  
 Uygulama, tüm kaynak yöneticileri oyladıktan sonra işlemin başarılı taahhüdüne bildirilir <xref:System.Transactions.PreparingEnlistment.Prepared%2A> .  
  
### <a name="commit-phase-phase-2"></a>Aşama (Aşama 2) Kaydet  

 İşlemin ikinci aşamasında, işlem yöneticisi tüm kaynak yöneticilerinden başarılı bir şekilde alırsa (1. aşama sonunda tüm kaynak yöneticileri çağırılır <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ), <xref:System.Transactions.IEnlistmentNotification.Commit%2A> her kaynak yöneticisi için yöntemini çağırır. Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.  
  
 Herhangi bir kaynak yöneticisi, 1. aşamada hazırlanmak üzere bir hata raporlamadıysanız, işlem yöneticisi <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> her kaynak yöneticisi için yöntemini çağırır ve uygulamaya yapılan işleme başarısızlığını gösterir.  
  
 Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.  
  
```csharp
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment
     enlistment.Done();
}  
```  
  
 RM, bildirim türüne bağlı olarak işlemi tamamlamak için gereken herhangi bir çalışmayı gerçekleştirmelidir ve bu öğeyi, parametresindeki yöntemi çağırarak, TM 'yi bilgilendirir <xref:System.Transactions.Enlistment.Done%2A> <xref:System.Transactions.Enlistment> . Bu iş iş parçacığı üzerinde yapılabilir. Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1. Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).  
  
### <a name="implementing-indoubt"></a>Nin şüpheli işlemi olmadığından uygulama  

 Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem. İşlem Yöneticisi bir veya daha fazla katılımcı ile iletişim kesilirse, durumu bilinmiyor olarak bu yöntem çağrılır. Bu durumda, daha sonra işlem katılımcılarının herhangi birinin tutarsız bir durumda bırakılmış olup olmadığı araştırabilmeniz için bu olguyu günlüğe yazmanız gerekir.  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Tek aşaması yürütme en iyi hale getirme  

 Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir. Bu protokol hakkında daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](optimization-spc-and-promotable-spn.md)
- [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](enlisting-resources-as-participants-in-a-transaction.md)
