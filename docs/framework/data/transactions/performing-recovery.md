---
title: Kurtarma Gerçekleştirme
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: 149ac6b6162893de830f59b3d18008d8298eab56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793620"
---
# <a name="performing-recovery"></a>Kurtarma Gerçekleştirme
Bir kaynak yöneticisi sonra kaynak hatası işlem katılımcı reenlisting tarafından bir işlemde kalıcı listeye çözümlenmesi kolaylaştırır.  
  
## <a name="the-recovery-process"></a>Kurtarma işlemi  
 Bir kaynak durably listeleme (uygulaması tarafından açıklanan <xref:System.Transactions.IEnlistmentNotification> arabirimi), daha sonra olabilir kurtarma için uygun, çağırması gerekir <xref:System.Transactions.Transaction.EnlistDurable%2A> yöntemi. Ayrıca, sağlamanız gereken <xref:System.Transactions.Transaction.EnlistDurable%2A> bir kaynak yöneticisi tanımlayıcısı yöntemiyle (bir <xref:System.Guid>) tutarlı bir şekilde bir kaynak hatası durumunda hareketin katılımcı etiketlemek için kullanılır. Bu nedenle, <xref:System.Guid> çağrısı için ilk Enlist aynı olması sağlanan olan *resourceManagerIdentifier* parametresinde <xref:System.Transactions.TransactionManager.Reenlist%2A> Kurtarma sırasında çağırın. Aksi takdirde <xref:System.Transactions.TransactionException> oluşturulur. Kalıcı kayıtlar hakkında daha fazla bilgi için bkz. [katılımcı bir işlemde kaynakları kaydetme](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) .  
  
 Uygulamanız kalıcı Kaynak Yöneticisi, aldığında 2PC Protokolü (Aşama 1) hazırla kısımda <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> bildirim, bunu kendi hazırla kaydı bu aşamada oturum açması gerekir. Kayıt üzerinde yürütme işlemi tamamlamak için gerekli olan tüm bilgileri içermelidir. Hazırlama kayıt daha sonra kurtarma sırasında alınıyor tarafından erişilebilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği *preparingEnlistment* geri çağırma. Kayıt günlük içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi RM olarak bu iş parçacığı üzerinde yapabilir.  
  
 Kurtarma işlemi aşağıdaki iki adımlardan oluşur:  
  
### <a name="step-1---reenlist"></a>Adım 1 - ReEnlist  
 Kaynak Yöneticisi şüpheli her liste için hazırla bilgi kaydını inceler. Bu incelenerek yapılır <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği <xref:System.Transactions.PreparingEnlistment> Kaynak Yöneticisi'nde için geçirilen geri çağırma <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> bildirim aşamasında 1.  
  
 İnceler böyle her bir liste için onu çağırır <xref:System.Transactions.TransactionManager.Reenlist%2A> üzerinde hareket yöneticisi. Bu yöntem benzersiz bir üzerinde başarılı <xref:System.Guid> , kaynak yöneticisi yanı sıra bir bayt dizisi liste 's bilgileri tanımlar. Yeni bir <xref:System.Transactions.Enlistment> nesne döndürülür. Reenlistment özel durumla başarısız olursa, kaynak yöneticisi daha sonra yeniden denemek gerekir.  
  
 Yalnızca çağırmalıdır <xref:System.Transactions.TransactionManager.Reenlist%2A> hata verdi bir kaynak yöneticisi yeniden başlatıldığında yöntemi. Ayrıca, yalnızca bir kaynak yöneticisi tarafından iki aşamalı tamamlama ilk hazırla aşamasında günlüğe çözümlenmemiş işlemleri reenlist. Bu yöntemi geçersiz zamanlarda çağırmak için her türlü girişim hatalı sonuçlara neden olabilir.  
  
 Bu yöntem, Aşama 2 yöntemleri kullanılarak katılımcı reenlisted olduğunda <xref:System.Transactions.IEnlistmentNotification> hareketin sonucu için karşılık gelen (diğer bir deyişle, <xref:System.Transactions.IEnlistmentNotification.Commit%2A> , <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> veya <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> ) uygun olarak adlandırılır.  
  
### <a name="step-2---completing-the-recovery"></a>Adım 2 - kurtarma Tamamlanıyor  
 Tüm reenlistments tamamlandığında, kaynak yöneticisi çağırır <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> yöntemi. Bu yöntem kurtarma tamamlar ve hareket yöneticisi kaynak yöneticisi daha fazla şüpheli işlemleri olduğunu bildirir. Bunu yaptığınızda, kaynak yöneticisi değil çağırır garanti <xref:System.Transactions.TransactionManager.Reenlist%2A> yeniden yöntemi.  
  
 Bir kaynak yöneticisi yeni işlemlerinde kaydetme önce tüm şüpheli hareketleri çözmek için gerekli değildir. İlk adım, ancak sonra hareket yöneticisi ile bir ilişki Kaynak Yöneticisi kurar sonra herhangi bir zamanda gerçekleştirilebilir <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> bırakıldı (2. adım) çağrılır; adım 1 yeniden gerçekleştirilemez. Adım 2 hareketlerin sonucunu etkilenmeden birden çok kez tekrarlanabilir.
