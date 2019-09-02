---
title: Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: 2abb9c13e9b0cb394546252e0e51e53c8ff9eefb
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206003"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
Bir işlemde kullanılan her kaynak, eylemleri bir işlem Yöneticisi (TM) tarafından koordine edilen bir kaynak yöneticisi (RM) tarafından yönetilir. [Kaynakları bir işlem konusunun katılımcıları olarak listelemek](enlisting-resources-as-participants-in-a-transaction.md) , bir kaynağın (veya birden fazla kaynağın) bir işlemde nasıl kaydedilebilir olduğunu tartışır. Bu konu başlığı altında, işlem taahhüdünün kayıtlı kaynaklar arasında nasıl koordine edilebilir.  
  
 İşlemin sonunda, uygulama, işlemi taahhüt veya geri alınacak şekilde ister. İşlem Yöneticisi, bazı kaynak yöneticilerinin işlemi geri almak için oylama yaparken yürütülmesi için oylama gibi riskleri ortadan kaldırmalıdır.  
  
 İşlem, birden fazla kaynak içeriyorsa, iki aşamalı bir işleme (2PC) uygulamanız gerekir. İki aşamalı tamamlama Protokolü (hazırlama aşaması ve yürütme aşaması), işlem sona erdiğinde tüm kaynaklardaki tüm değişikliklerin tamamen kaydedilmiş veya tam olarak geri alındığı durumlarda sağlar. Tüm katılımcıları sonra sonucunu bildirilir. İki aşamalı tamamlama protokolü hakkında ayrıntılı bir tartışma için lütfen "*işlem işleme: Kavramlar ve teknikler (veri yönetimi sistemlerde Morgan Kaumann serisi) ISBN: 1558601902*", Jim Gray tarafından yapılır.  
  
 Ayrıca, tek aşamalı Işleme protokolüne bir parça ayırarak işlem performansını iyileştirebilirsiniz. Daha fazla bilgi için bkz. [tek aşamalı tamamlama ve promotable tek aşamalı bildirimi kullanarak iyileştirme](optimization-spc-and-promotable-spn.md).  
  
 Yalnızca bir işlemin sonucu hakkında bilgilendirilmek istiyorsanız ve oylama 'ye katılmak istemiyorsanız, <xref:System.Transactions.Transaction.TransactionCompleted> olaya kaydolmanız gerekir.  
  
## <a name="two-phase-commit-2pc"></a>İki aşamalı kayıt (2PC)  
 İlk işlem aşamasında, işlem yöneticisi her bir işlemin kaydedilip edilmeyeceğini veya geri döndürülüp döndürülmeyeceğini anlamak için her bir kaynağı sorgular. İkinci işlem aşamasında, işlem yöneticisi her bir kaynağa kendi sorgularının sonucunu bildirir ve gerekli temizleme işlemlerini gerçekleştirmesine izin verir.  
  
 Bu tür bir işleme katılmak için bir kaynak yöneticisi, bir 2PC sırasında <xref:System.Transactions.IEnlistmentNotification> TM olarak çağrılan yöntemler sağlayan arabirimini uygulamalıdır.  Aşağıdaki örnek, bu tür uygulaması örneği gösterir.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Aşama (Aşama 1) hazırla  
 Uygulamadan bir <xref:System.Transactions.CommittableTransaction.Commit%2A> istek alındıktan sonra, işlem yöneticisi her bir kaynağın üzerindeki oyunuzu almak için kaydedilen her bir kaynaktaki <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemini çağırarak her bir kayıtlı katılımcının hazırlama aşamasına başlar. işlem.  
  
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
  
 Dayanıklı Kaynak Yöneticisi bu çağrıyı aldığında, işlemin kurtarma bilgilerini ( <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği alarak kullanılabilir) ve işleme sırasında işlemi tamamlamak için hangi bilgilerin gerekli olduğunu günlüğe kaydetmelidir. Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.  
  
 RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi. Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı. Hazırlama aşamasında bu yöntemi <xref:System.Transactions.PreparingEnlistment> geri çağırmada çağırırsanız, TM 'ye bir salt okuma listesi olduğunu bildirir (diğer bir deyişle, işlem korumalı verileri okuyabilen ancak güncelleştireamayan kaynak yöneticileri) ve RM daha fazla bildirim almaz İşlem Yöneticisi 'nden, 2. aşama içindeki işlemin sonucuna göre.  
  
 Uygulama, tüm kaynak yöneticileri oyladıktan <xref:System.Transactions.PreparingEnlistment.Prepared%2A>sonra işlemin başarılı taahhüdüne bildirilir.  
  
### <a name="commit-phase-phase-2"></a>Aşama (Aşama 2) Kaydet  
 İşlemin ikinci aşamasında, işlem yöneticisi tüm kaynak yöneticilerinden başarılı bir şekilde alırsa (1. aşama sonunda tüm kaynak yöneticileri çağırılır <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ), her kaynak için <xref:System.Transactions.IEnlistmentNotification.Commit%2A> yöntemini çağırır Manager. Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.  
  
 Herhangi bir kaynak yöneticisi, 1. aşamada hazırlanmak üzere bir hata raporlamadıysanız, işlem <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> Yöneticisi her kaynak yöneticisi için yöntemini çağırır ve uygulamaya yapılan işleme başarısızlığını gösterir.  
  
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
  
 RM, bildirim türüne bağlı olarak işlemi tamamlamak için gereken herhangi bir çalışmayı gerçekleştirmelidir ve bu öğeyi, <xref:System.Transactions.Enlistment.Done%2A> <xref:System.Transactions.Enlistment> parametresindeki yöntemi çağırarak, TM 'yi bilgilendirir. Bu iş iş parçacığı üzerinde yapılabilir. Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1. Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).  
  
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
