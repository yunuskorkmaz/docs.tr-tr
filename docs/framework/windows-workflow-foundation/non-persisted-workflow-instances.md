---
title: Kalıcı Olmayan İş Akışı Örnekleri
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 410451f0dfeb91111e77634245aa786c4afc5b04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644271"
---
# <a name="non-persisted-workflow-instances"></a>Kalıcı Olmayan İş Akışı Örnekleri
Bir iş akışının yeni bir örneği oluşturulduğunda, durumunda kalıcı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hizmet ana bilgisayarı örnek deposunda bu hizmet için bir giriş oluşturur. Sonuç olarak, ne zaman iş akışı örneği kalıcıdır ilk kez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> geçerli örneğin durumunu depolar. İş akışı Windows İşlem Etkinleştirme hizmetinde barındırılıyorsa, bu ilk kez örneği kalıcıdır hizmet dağıtım verileri de örnek deposuna yazılır.  
  
 İş akışı örneği kalıcı değil sürece olduğu bir **kalıcı olmayan** durumu. Bu durumdayken, iş akışı örneği bir uygulama etki alanı geri dönüşümü, ana bilgisayar hatası veya bilgisayar hatasından sonra kurtarılamaz.  
  
## <a name="the-non-persisted-state"></a>Kalıcı olmayan durumu  
 Kalıcı dayanıklı iş akışı örnekleri aşağıdaki durumlarda kalıcı olmayan bir durumda kalır:  
  
- İlk kez iş akışı örneği kalıcıdır önce hizmet ana bilgisayarı kilitleniyor. İş akışı örneği, örnek deposunda kalır ve kurtarılmamış. İlişkili bir ileti geldiğinde, iş akışı örneği tekrar etkin hale gelir.  
  
- İş akışı örneği bir özel durum karşılaştığında, önce ilk kez kalıcı hale getirilir. Yapılandırmanıza bağlı olarak <xref:System.Activities.UnhandledExceptionAction> döndürülen, aşağıdaki senaryolarda oluşur:  
  
    - <xref:System.Activities.UnhandledExceptionAction> ayarlanır <xref:System.Activities.UnhandledExceptionAction.Abort>: Bir özel durum oluştuğunda, hizmet dağıtım bilgileri için örnek deposuna yazılır ve bellekten iş akışı örneği kaldırılır. İş akışı örneği kalıcı olmayan bir durumda kalır ve yeniden yüklenemiyor.  
  
    - <xref:System.Activities.UnhandledExceptionAction> ayarlanır <xref:System.Activities.UnhandledExceptionAction.Cancel> veya <xref:System.Activities.UnhandledExceptionAction.Terminate>: Özel bir durum oluştuğunda, hizmet dağıtım bilgileri, örnek deposuna yazılır ve etkinlik örneğinin durumunu ayarlamak <xref:System.Activities.ActivityInstanceState.Closed>.  
  
 Kaldırılan kalıcı olmayan iş akışı örnekleri karşılaşıldığında riskini en aza indirmek için erken yaşam döngüsü içinde iş akışını sürdürmek öneririz.  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a>Algılama ve kaldırma kalıcı olmayan örnekleri  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Herhangi kalıcı olmayan iş akışı örnekleri örnek deposundan kaldırmaz. Kalıcı olmayan iş akışı örneği ile ilişkili tüm süresi dolan kilit sahiplerinin ayrıca kaldırmaz.  
  
 Yönetici kalıcı olmayan örnekleri için örnek deposuna düzenli aralıklarla denetleyen öneririz. Bu iş akışı bağıntılı iletilerin almaz alışık oldukları sürece Yöneticiler bu örnekleri örnek deposundan kaldırabilirsiniz. Örneğin, örnek veritabanında birkaç ay boyunca yapıldı ve iş akışı genellikle birkaç gün ömrü olduğunu bilinir, kilitlenen başlatılmış örneği olduğunu varsayın güvenli olurdu.  
  
 SQL iş akışı örneği Store içinde kalıcı olmayan örnekleri bulmak için aşağıdaki SQL sorgularını kullanabilirsiniz:  
  
- Bu sorgu, kalıcı ve (UTC saatiyle depolanır) kimliği ve oluşturma zamanı için bunları döndüren tüm örneklerini bulur.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
- Bu sorgu değil yerleştirildi ve yüklü değildir ve döndürür (UTC saatiyle depolanır) kimliği ve oluşturma zamanı bunları için tüm örneklerini bulur.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
- Bu sorgu kalıcı ve döndüren kimliği, oluşturma zamanı (UTC saatiyle depolanır), askıya alınmış tüm örneklerini bulur askıya alma nedeni ve bunlar için özel durum adı.  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 Kalıcı olmayan örnekleri silerken dikkatli olun. Genel olarak, kalıcı olmayan örnekleri tarafından oluşturulan kaldırmanın güvenli olduğunu <xref:System.ServiceModel.Activities.WorkflowServiceHost> askıya alınmış durumda veya yüklü değil. Bunları silerek, bu belirli örneklere Mağaza'dan silinebilir `[System.Activities.DurableInstancing].[Instances]` doğru örneği kimliğini değiştirerek aşağıdaki SQL komutunu kullanarak görünümü  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  Bu, az önce oluşturduğunuz ve henüz kalıcı örnekleri içerdiğinden tüm kalıcı olmayan örnekleri kaldırma önermiyoruz.
