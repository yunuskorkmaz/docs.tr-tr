---
title: "İşlemi tek aşamalı ve çok aşaması Tamamlanıyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2891313c15b4003db5d50f2e9f2d461de9397dfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>İşlemi tek aşamalı ve çok aşaması Tamamlanıyor
Bir işlem içinde kullanılan her bir kaynağın eylemlerini işlem yöneticisi (TM) tarafından düzenlenir Kaynak Yöneticisi (RM) tarafından yönetilir. [Kaydetme kaynakları bir işlemde katılımcı olarak](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) konuda ele alınmıştır bir kaynak (veya birden çok kaynak) bir işlem içinde nasıl kaydedilebilir. Bu konuda ele alınmıştır nasıl işlem taahhüt kayıtlı kaynakları arasında Eşgüdümlü olabilir.  
  
 İşlemin sonunda, uygulama işlemi ya da yürütülmeli veya geri ister. Başkalarının tamamlamaya oylama bazı kaynak yöneticileri while gibi işlem yöneticisi riskleri ortadan kaldırmanız gerekir işlemi geri oylama.  
  
 İşleminiz birden fazla kaynak içeriyorsa, iki aşamalı kayıt (2PC) gerçekleştirmeniz gerekir. İki aşamalı yürütme Protokolü (hazırlama aşamasında ve Tamamlama aşaması) işlem sona erdiğinde, tüm kaynakları yapılan tüm değişiklikler tamamen kaydedilen ya da tam olarak geri olduğunu sağlar. Tüm katılımcıları sonra sonucunu bildirilir. İki aşamalı yürütme protokolü hakkında ayrıntılı bilgi için lütfen rehberi başvurun "*hareket işleme: kavramlar ve teknikler (Morgan Kaufmann dizide veri yönetim sistemleri) ISBN:1558601902*" Jim gri tarafından.  
  
 Ayrıca, tek aşaması yürütme protokolünde bölümü gerçekleştirerek, işlemdeki performans iyi duruma getirebilirsiniz. Daha fazla bilgi için bkz: [tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
 Yalnızca bir işlemdeki sonucunu bilgilendirilmek istiyorsanız ve oylamasına katılmasına istemediğiniz, için kaydedeceğini <xref:System.Transactions.Transaction.TransactionCompleted> olay.  
  
## <a name="two-phase-commit-2pc"></a>İki aşamalı kayıt (2PC)  
 İlk işlem aşamasında, işlem yöneticisi bir işlem yürütülmeli veya geri olup olmadığını belirlemek için her bir kaynağın sorgular. İkinci işlem aşamasında, işlem yöneticisi, kendi sorgu sonucunun her bir kaynağın tüm gerekli temizlenmesini izin veren bildirir.  
  
 Bu tür bir işlem içinde katılmak için bir Kaynak Yöneticisi'ni uygulamalıdır <xref:System.Transactions.IEnlistmentNotification> tarafından TM 2PC sırasında bildirimleri olarak adlandırılır yöntemleri sağlayan arabirim.  Aşağıdaki örnek, bu tür uygulaması örneği gösterir.  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>Aşama (Aşama 1) hazırla  
 Alma sırasında bir <xref:System.Transactions.CommittableTransaction.Commit%2A> isteği uygulamadan işlem yöneticisi çağırarak tüm kayıtlı katılımcılar hazırlık aşamasında başlar <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi her kaynak kayıtlı, her bir kaynağın almak için 's oy işlem.  
  
 Uygular, Kaynak Yöneticisi <xref:System.Transactions.IEnlistmentNotification> arabirimi ilk uygulayan <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> yöntemi aşağıdaki basit örnekte gösterildiği gibi.  
  
```  
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
  
 Sağlam kaynak yöneticisi bu çağrı aldığında, işlemdeki kurtarma bilgileri günlüğe (alarak kullanılabilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği) ve ne olursa olsun üzerinde yürütme işlemi tamamlamak gerekli bir bilgidir. Bu içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi olduğundan RM iş parçacığı üzerinde bunu yapabilirsiniz.  
  
 RM bittiğinde kendi iş hazırlama, yürütme veya geri çağırarak için oy <xref:System.Transactions.PreparingEnlistment.Prepared%2A> veya <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> yöntemi. Dikkat <xref:System.Transactions.PreparingEnlistment> sınıfından devralan bir <xref:System.Transactions.Enlistment.Done%2A> yönteminden <xref:System.Transactions.Enlistment> sınıfı. Bu yöntem çağırırsanız <xref:System.Transactions.PreparingEnlistment> geri çağırma hazırlama aşamasında, sizi bilgilendirir TM salt okunur bir kaydı (okuyabilir, ancak işlem korunan verileri güncelleştirilemiyor diğer bir deyişle, kaynak yöneticileri) olduğunu ve başka hiçbir bildirim RM alır İşlem Yöneticisi'nden Aşama 2 işlemde sonucunu seçeceğine.  
  
 Tüm kaynak yöneticileri oy sonra uygulama işlem başarılı taahhüt işe <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.  
  
### <a name="commit-phase-phase-2"></a>Aşama (Aşama 2) Kaydet  
 İkinci aşama hareketin işlem yöneticisi başarılı alırsa, tüm kaynak yöneticileri hazırlar (tüm kaynak yöneticileri çağrılan <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 1 sonunda), onu çağırır <xref:System.Transactions.IEnlistmentNotification.Commit%2A> her kaynak için yöntemi Yöneticisi. Kaynak yöneticileri ardından değişiklikleri kalıcı yapın ve yürütme tamamlayın.  
  
 Herhangi bir kaynak yöneticisi Aşama 1 hazırlamak için bir hata bildirdi, İşlem Yöneticisi'ni çağırır <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> her kaynak yöneticisi için yöntem ve uygulamaya yürütme başarısızlığını gösterir.  
  
 Bu nedenle, kaynak yöneticisi aşağıdaki yöntemleri uygulamanız gerekir.  
  
```  
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
  
 RM bildirim türüne göre hareket tamamlamak gerekli herhangi bir iş gerçekleştirin ve çağırarak bitirdi TM bildirmek <xref:System.Transactions.Enlistment.Done%2A> yöntemi <xref:System.Transactions.Enlistment> parametresi. Bu iş iş parçacığı üzerinde yapılabilir. Satır içi çağrılır aynı iş parçacığı üzerinde Aşama 2 bildirimleri oluşabilir Not <xref:System.Transactions.PreparingEnlistment.Prepared%2A> yönteminde Aşama 1. Bu nedenle, sonra herhangi bir iş yapmanız gerektiğini değil <xref:System.Transactions.PreparingEnlistment.Prepared%2A> Aşama 2 bildirimleri almadan önce tamamladınız beklediğiniz araması (örneğin, serbest bırakma kilitler).  
  
### <a name="implementing-indoubt"></a>Nin şüpheli işlemi olmadığından uygulama  
 Son olarak, uygulamalıdır <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> geçici kaynak yöneticisi için yöntem. Durumları bilinmiyor şekilde işlem yöneticisi bir veya daha fazla katılımcı ile ilgili kişi kaybederse, bu yöntem çağrılır. Bu gerçekleşirse, böylece herhangi bir işlem katılımcının sola mı tutarsız bir durumda daha sonra araştırabilir olgunun oturum açmanız gerekir.  
  
```  
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>Tek aşaması yürütme en iyi hale getirme  
 Tüm güncelleştirmeleri herhangi bir açık işbirliği yapıldığından tek aşaması yürütme Protokolü çalışma zamanında daha etkilidir. Bu protokol, daha fazla bilgi için bkz [tek aşaması kaydetmek ve yükseltilebilir tek aşaması bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tek Aşamalı İşleme ve Yükseltilebilir Tek Aşamalı Bildirim kullanarak en iyi duruma getirme](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [Bir İşlemde Kaynakları Katılımcı Olarak Kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
