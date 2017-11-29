---
title: "Kurtarma gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a73e1b5c6cbb18e89b30550f02c0678e76d12ab4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="performing-recovery"></a>Kurtarma gerçekleştirme
Kaynak Yöneticisi, kaynak hatasından sonra işlem katılımcı reenlisting tarafından bir işlemde dayanıklı kayıtlar çözümlenmesi kolaylaştırır.  
  
## <a name="the-recovery-process"></a>Kurtarma işlemi  
 Bir kaynak durably listeleme (uygulaması tarafından açıklanan <xref:System.Transactions.IEnlistmentNotification> arabirimi), daha sonra olabilir kurtarma için uygun, çağırması gerekir <xref:System.Transactions.Transaction.EnlistDurable%2A> yöntemi. Ayrıca, sağlamanız gereken <xref:System.Transactions.Transaction.EnlistDurable%2A> yöntemi bir kaynak yöneticisi tanımlayıcısı ile (bir <xref:System.Guid>) tutarlı bir şekilde bir kaynak hatası durumunda işlem katılımcı etiketlemek için kullanılır. Bu nedenle, <xref:System.Guid> ilk Enlist çağrı için aynı olmalıdır sağlanan olan *resourceManagerIdentifier* parametresinde <xref:System.Transactions.TransactionManager.Reenlist%2A> Kurtarma sırasında çağırın. Aksi takdirde <xref:System.Transactions.TransactionException> oluşturulur. Dayanıklı kayıtlar hakkında daha fazla bilgi için bkz: [kaydetme kaynakları bir işlemde katılımcı olarak](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) .  
  
 Uygulamanız kalıcı Kaynak Yöneticisi, aldığında 2PC Protokolü (Aşama 1) hazırla kısımda <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> bildirim, bunu kendi hazırla kaydı bu aşamada oturum açması gerekir. Kayıt işleme yürütme işlemini tamamlamak için gereken tüm bilgiler içermelidir. Prepare kaydı daha sonra kurtarma sırasında alarak erişilebilir <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği *preparingEnlistment* geri çağırma. Kayıt günlük içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi RM olarak bu iş parçacığı üzerinde yapabilir.  
  
 Kurtarma işlemi aşağıdaki iki adımlardan oluşur:  
  
### <a name="step-1---reenlist"></a>Adım 1 - ReEnlist  
 Kaynak Yöneticisi şüpheli her liste için hazırla bilgi kaydını inceler. Bu incelenerek yapılır <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği <xref:System.Transactions.PreparingEnlistment> Kaynak Yöneticisi'nde için geçirilen geri çağırma <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> bildirim aşamasında 1.  
  
 Bunu inceler gibi her bir liste için onu çağırır <xref:System.Transactions.TransactionManager.Reenlist%2A> işlem yöneticisi üzerinde. Bu yöntem benzersiz bir üzerinde başarılı <xref:System.Guid> , kaynak yöneticisi yanı sıra bir bayt dizisi liste 's bilgileri tanımlar. Yeni bir <xref:System.Transactions.Enlistment> nesne döndürülür. Reenlistment bir özel durumla başarısız olursa, kaynak yöneticisi daha sonra yeniden denemek gerekir.  
  
 Yalnızca çağırmalıdır <xref:System.Transactions.TransactionManager.Reenlist%2A> hata verdi bir kaynak yöneticisi yeniden başlatıldığında yöntemi. Ayrıca, yalnızca iki aşamalı yürütme başlangıç hazırlama aşamasında bir kaynak yöneticisi tarafından günlüğe kaydedilen çözümlenmemiş işlemler yeniden kaydedemediğinden. Bu yöntemi geçersiz zamanlarda çağırmak için her türlü girişim hatalı sonuçlara neden olabilir.  
  
 Bu yöntem, Aşama 2 yöntemlerini kullanarak katılımcı reenlisted zaman <xref:System.Transactions.IEnlistmentNotification> hareketin sonucu karşılık gelir (diğer bir deyişle, <xref:System.Transactions.IEnlistmentNotification.Commit%2A> , <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> veya <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> ) uygun şekilde olarak adlandırılır.  
  
### <a name="step-2---completing-the-recovery"></a>Adım 2 - kurtarma Tamamlanıyor  
 Tüm reenlistments tamamlandığında, kaynak yöneticisi çağırır <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> yöntemi. Bu yöntem, Kurtarma tamamlandıktan ve işlem yöneticisi, Kaynak Yöneticisi'ni başka şüpheli işlemlerin olduğunu bildirir. Bunu yaptığınızda, kaynak yöneticisi değil çağırır garanti <xref:System.Transactions.TransactionManager.Reenlist%2A> yeniden yöntemi.  
  
 Bir Kaynak Yöneticisi'ni yeni işlemlerinde kaydetme önce tüm şüpheli işlemleri çözümlemek için gerekli değildir. İlk adım, Kaynak Yöneticisi'ni, sonra ancak işlem yöneticisi ile bir ilişki kurar. sonra herhangi bir zamanda gerçekleştirilebilir <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> bırakıldı (2. adım) çağrılır; 1. adım yeniden gerçekleştirilemiyor. 2. adım hareketlerin sonucunu etkilemeden birden çok kez yinelenebilir.
