---
title: Kurtarma Gerçekleştirme
description: .NET ' te kurtarma gerçekleştirin. Kaynak Yöneticisi, kaynak hatasından sonra işlem katılımcısını yeniden listeleyerek, dayanıklı işlem dökümüne yardımcı olur.
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: bb00d2f574cc2651b733f3308cf2ffc6b430cc31
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141971"
---
# <a name="performing-recovery"></a>Kurtarma Gerçekleştirme
Kaynak Yöneticisi, kaynak hatasından sonra işlem katılımcısını yeniden listeleyerek bir işlemde kalıcı kayıtlar çözümlemesini kolaylaştırır.  
  
## <a name="the-recovery-process"></a>Kurtarma işlemi  
 Bir kaynak durably listeleme (uygulaması tarafından açıklanan <xref:System.Transactions.IEnlistmentNotification> arabirimi), daha sonra olabilir kurtarma için uygun, çağırması gerekir <xref:System.Transactions.Transaction.EnlistDurable%2A> yöntemi. Buna ek olarak, bir Resource <xref:System.Transactions.Transaction.EnlistDurable%2A> Manager tanımlayıcısı (a) ile bir <xref:System.Guid> kaynak hatası durumunda işlemin katılımcısını tutarlı bir şekilde etiketlemesini sağlamanız gerekir. Bu nedenle, <xref:System.Guid> Ilk Enlist çağrısı için belirtilen, kurtarma sırasında çağrısındaki *resourceManagerIdentifier* parametresiyle aynı olmalıdır <xref:System.Transactions.TransactionManager.Reenlist%2A> . Aksi takdirde <xref:System.Transactions.TransactionException> oluşturulur. Dayanıklı kayıtlar hakkında daha fazla bilgi için bkz. [kaynakları bir işlem Içinde katılımcılar olarak listeleme](enlisting-resources-as-participants-in-a-transaction.md) .  
  
 Uygulamanız kalıcı Kaynak Yöneticisi, aldığında 2PC Protokolü (Aşama 1) hazırla kısımda <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> bildirim, bunu kendi hazırla kaydı bu aşamada oturum açması gerekir. Kayıt, işleme üzerindeki işlemi tamamlamak için gereken tüm bilgileri içermelidir. Hazırlık kaydına, hazırlık <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> listesine geri çağırma özelliği eklenerek daha sonra kurtarma sırasında erişilebilir. *preparingEnlistment* Kayıt günlük içinde yapılması gerekmez <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> yöntemi RM olarak bu iş parçacığı üzerinde yapabilir.  
  
 Kurtarma işlemi aşağıdaki iki adımlardan oluşur:  
  
### <a name="step-1---reenlist"></a>Adım 1 - ReEnlist  
 Kaynak Yöneticisi şüpheli her liste için hazırla bilgi kaydını inceler. Bu incelenerek yapılır <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> özelliği <xref:System.Transactions.PreparingEnlistment> Kaynak Yöneticisi'nde için geçirilen geri çağırma <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> bildirim aşamasında 1.  
  
 İncelediği her bir kayıt için <xref:System.Transactions.TransactionManager.Reenlist%2A> işlem yöneticisinde çağırır. Bu yöntem benzersiz bir üzerinde başarılı <xref:System.Guid> , kaynak yöneticisi yanı sıra bir bayt dizisi liste 's bilgileri tanımlar. Yeni bir <xref:System.Transactions.Enlistment> nesne döndürülür. Yeniden kayıt bir özel durumla başarısız olursa, kaynak yöneticisinin daha sonra yeniden denemesi gerekir.  
  
 Yalnızca çağırmalıdır <xref:System.Transactions.TransactionManager.Reenlist%2A> hata verdi bir kaynak yöneticisi yeniden başlatıldığında yöntemi. Ayrıca, bir kaynak yöneticisi tarafından yalnızca, iki aşamalı bir kaydetmenin ilk hazırlanması sırasında günlüğe çözülmemiş işlemleri yeniden listeleme yapmanız gerekir. Bu yöntemi geçersiz zamanlarda çağırmak için her türlü girişim hatalı sonuçlara neden olabilir.  
  
 Katılımcı bu yöntem kullanılarak yeniden listelense, işlemin sonucuna karşılık gelen aşama 2 yöntemleri <xref:System.Transactions.IEnlistmentNotification> (yani, <xref:System.Transactions.IEnlistmentNotification.Commit%2A> <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> veya <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> ) uygun şekilde çağırılır.  
  
### <a name="step-2---completing-the-recovery"></a>Adım 2 - kurtarma Tamamlanıyor  
 Tüm reenlistments tamamlandığında, kaynak yöneticisi çağırır <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> yöntemi. Bu yöntem, kurtarmayı tamamlar ve işlem yöneticisine kaynak yöneticisinin daha fazla şüpheli işlem olmadığını bildirir. Bunu yaptığınızda, kaynak yöneticisi değil çağırır garanti <xref:System.Transactions.TransactionManager.Reenlist%2A> yeniden yöntemi.  
  
 Yeni işlemlere kaydedilmeden önce tüm şüpheli işlemleri çözümlemek için Kaynak Yöneticisi gerekli değildir. İlk adım, Resource Manager, işlem yöneticisiyle bir ilişki kurulduktan sonra, ancak çağrıldıktan sonra <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> (2. adım), tekrar gerçekleştirilemediği zaman gerçekleştirilebilir. 2. adım işlem sonuçlarının etkilenmeden birden çok kez tekrarlanabilir.
