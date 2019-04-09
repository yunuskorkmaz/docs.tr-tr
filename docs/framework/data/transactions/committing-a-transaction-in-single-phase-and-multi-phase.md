---
title: Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
ms.openlocfilehash: cbe00fb792ab5f2a7586a958ddbe5bdf004656dc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089572"
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>Tek Aşamalı ve Çok Aşamalı İşlem Gerçekleştirme
Bir işlemde kullanılan her kaynak eylemlerini bir işlem yöneticisi (TM) düzenlenir Kaynak Yöneticisi (RM) tarafından yönetilir. [Katılımcı bir işlemde kaynakları kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) konu açıklar bir kaynak (veya birden fazla kaynak) bir işlemde nasıl kaydedilebilir. Bu konu nasıl işlem taahhüt kayıtlı kaynakları arasında Eşgüdümlü olabileceğini açıklar.  
  
 İşlemin sonunda, uygulama ya da kaydedilmiş veya geri için işlem ister. Bazı kaynak yöneticileri tamamlamaya oylama başkalarının çalışırken gibi hareket yöneticisi riskleri ortadan işlem geri dönmek için işaretleme.  
  
 İşlem birden fazla kaynak içeriyorsa, iki aşamalı bir kayıt (2PC) gerçekleştirmeniz gerekir. İki aşamalı tamamlama Protokolü (Hazırlık aşaması ve Tamamlama aşaması) işlem sona erdiğinde, tüm değişiklikleri tüm kaynaklara ya da tamamen kaydedilmiş veya tam döndürülmesine sağlar. Tüm katılımcıları sonra sonucunu bildirilir. İki aşamalı tamamlama protokolü hakkında ayrıntılı bilgi için lütfen kitap başvurun "*işlem: Kavramları ve teknikleri (Morgan Kaufmann dizide veri yönetim sistemleri) ISBN: 1558601902*"Jim gri tarafından.  
  
 Ayrıca, tek aşaması yürütme Protokolü bölümü gerçekleştirerek, hareketin performans iyileştirebilirsiniz. Daha fazla bilgi için [tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 Yalnızca bir hareketin sonucu haberdar olmak istiyor ve oylama katılmak istiyor musunuz, kaydedin <xref:System.Transactions.Transaction.TransactionCompleted> olay.  
  
## <a name="two-phase-commit-2pc"></a>İki aşamalı kayıt (2PC)  
 İlk işlem aşamasında hareket yöneticisi bir hareketin kaydedilmiş veya geri olup olmadığını belirlemek için her kaynak sorgular. İkinci işlem aşamasında, gerekli tüm temizlemesi gerçekleştirin izin veren hareket yöneticisi her kaynak kendi sorgu sonucunun uyarır.  
  
 Bu tür bir işlem katılmak için bir kaynak yöneticisi uygulamalıdır <xref:System.Transactions.IEnlistmentNotification> arabirimi, tarafından TM sırasında bir 2PC bildirimleri olarak adlandırılır yöntemleri sağlar.  Aşağıdaki örnek, bu tür uygulaması örneği gösterir.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Aşama (Aşama 1) hazırla  
 Alma bağlı bir <xref:System.Transactions.CommittableTransaction.Commit%2A> istek uygulamadan hareket yöneticisi çağırarak kayıtlı tüm katılımcıları hazırla aşaması başlar <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi her kayıtlı kaynak, her kaynak almak için kullanıcının oy kullanın işlem.  
  
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
  
 Kalıcı kaynak yöneticisi bu çağrı aldığında, hareketin kurtarma bilgilerini kapatması gerekir (alarak kullanılabilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği) ve hangi bilgileri üzerindeki kaydetme işlemi tamamlamak gereklidir. Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.  
  
 RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi. Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı. Bu yöntem çağırırsanız <xref:System.Transactions.PreparingEnlistment> geri çağırma hazırla aşamasında, onu bildiren TM salt okunur bir liste (okuyabilirsiniz ancak işlem korunan verileri güncelleştiremiyor diğer bir deyişle, kaynak yöneticileri) olduğunu ve daha fazla bildirim RM alır İşlem Yöneticisi'nden işlem sırasında Aşama 2 sonucunu için farklı.  
  
 Tüm kaynak yöneticileri oy sonra uygulama işlemin başarılı taahhüt bildirilir <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.  
  
### <a name="commit-phase-phase-2"></a>Aşama (Aşama 2) Kaydet  
 İkinci aşaması hareketin hareket yöneticisi başarılı alırsa, tüm kaynak yöneticileri hazırlar (tüm kaynak yöneticileri çağrılır <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 1 sonunda), onu çağırır <xref:System.Transactions.IEnlistmentNotification.Commit%2A> her kaynağın yöntemi Yöneticisi. Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.  
  
 Herhangi bir kaynak yöneticisi raporlanan 1 aşamasında hazırlamak için bir hata varsa hareket yöneticisi çağırır <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> her kaynak yöneticisi için yöntem ve uygulama için yürütme başarısız gösterir.  
  
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
  
 RM bildirim türüne göre işlemi tamamlamak için gerekli olan herhangi bir çalışma gerçekleştirme ve çağırarak bitirdi TM bildirmek <xref:System.Transactions.Enlistment.Done%2A> metodunda <xref:System.Transactions.Enlistment> parametresi. Bu iş iş parçacığı üzerinde yapılabilir. Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1. Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).  
  
### <a name="implementing-indoubt"></a>Nin şüpheli işlemi olmadığından uygulama  
 Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem. Durumları bilinmiyor şekilde hareket yöneticisi bir veya daha fazla katılımcılarıyla iletişim kaybolursa, bu yöntem çağrılır. Bu meydana gelirse, daha sonra herhangi bir işlem katılımcıları sola mı tutarsız bir durumda inceleyebilirsiniz bu olgu oturum açmanız gerekir.  
  
```csharp
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Tek aşaması yürütme en iyi hale getirme  
 Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir. Bu protokol hakkında daha fazla bilgi için bkz. [tek aşamalı işleme ve yükseltilebilir tek aşamalı bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)
- [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
