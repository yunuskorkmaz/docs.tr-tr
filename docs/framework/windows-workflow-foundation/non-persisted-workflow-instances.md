---
title: Kalıcı olmayan iş akışı örnekleri
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 410451f0dfeb91111e77634245aa786c4afc5b04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516756"
---
# <a name="non-persisted-workflow-instances"></a>Kalıcı olmayan iş akışı örnekleri
Bir iş akışı yeni bir örneğini oluşturulduğunda durumundayken kalıcı <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, hizmet ana bilgisayarı örnek deposunda bu hizmet için bir giriş oluşturur. Sonuç olarak, ne zaman iş akışı örneği kalıcıdır ilk kez <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> geçerli örnek durum depolar. İş akışı Windows İşlem Etkinleştirme hizmeti barındırılıyorsa örneği ilk kez kalıcı veri hizmeti dağıtımı da örnek deposuna yazılır.  
  
 İş akışı örneği kalıcı olmayan sürece olan bir **kalıcı olmayan** durumu. Bu durumundayken, iş akışı örneği bir uygulama etki alanı geri dönüşümü, ana bilgisayar hatası veya bilgisayar hatasından sonra kurtarılamaz.  
  
## <a name="the-non-persisted-state"></a>Kalıcı olmayan durumu  
 Aşağıdaki durumlarda kalıcı olmayan bir durumda değil kalıcı dayanıklı iş akışı örnekleri kalır:  
  
-   İş akışı örneği ilk kez kalıcı önce Hizmet Konağı çöküyor. İş akışı örneği örnek deposunda kalır ve kurtarılmamış. Bağlantılı bir ileti alınırsa, iş akışı örneği yeniden etkin hale gelir.  
  
-   İlk kez kalıcı önce iş akışı örneği bir özel durum karşılaşır. Bağlı olarak <xref:System.Activities.UnhandledExceptionAction> döndürülen, aşağıdaki senaryolarda oluşur:  
  
    -   <xref:System.Activities.UnhandledExceptionAction> ayarlanmış <xref:System.Activities.UnhandledExceptionAction.Abort>: bir özel durum oluştu, hizmet dağıtım bilgileri için örnek deposuna yazılır ve iş akışı örneği bellekten olduğunda. İş akışı örneği kalıcı olmayan bir durumda kalır ve yeniden yüklenemiyor.  
  
    -   <xref:System.Activities.UnhandledExceptionAction> ayarlanmış <xref:System.Activities.UnhandledExceptionAction.Cancel> veya <xref:System.Activities.UnhandledExceptionAction.Terminate>: bir özel durum oluştu, hizmet dağıtım bilgileri için örnek deposuna yazılır ve etkinlik örnek durum kümesine <xref:System.Activities.ActivityInstanceState.Closed>.  
  
 Kalıcı olmayan bellekten iş akışı örnekleri karşılaşmadan riskini en aza indirmek için erken yaşam döngüsü iş akışını sürdürmek öneririz.  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a>Algılama ve temizleme kalıcı olmayan örnekleri  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Hiç kalıcı olmayan iş akışı örneği örnek deposundan kaldırmaz. Kalıcı olmayan iş akışı örneği ilişkili tüm süresi dolan kilit sahiplerinin ayrıca kaldırmaz.  
  
 Yönetici kalıcı olmayan örnekleri için örnek deposuna düzenli olarak denetler öneririz. Yöneticiler bu iş akışı bağıntılı iletileri almaz bilmeniz sürece bu örneklerde örneği Mağazası'ndan kaldırabilir. Örneğin, örnek veritabanında birkaç ay olmuştur ve iş akışı genellikle birkaç gün ömrü olduğunu biliniyorsa ise, onu bu çöken örneği başlatılmış olduğunu varsaymak güvenli olabilir.  
  
 SQL iş akışı örneği Mağazası'nda kalıcı olmayan örneklerini bulmak için aşağıdaki SQL sorgularını kullanabilirsiniz:  
  
-   Bu sorgu kalıcı ve (UTC saatiyle depolanır) kimliği ve oluşturulması zaman bunları döndüren tüm örneklerini bulur.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   Bu sorgu, değil devam ediyor ve yüklü değil ve (UTC saatiyle depolanır) kimliği ve oluşturulması zaman bunları döndürür tüm örneklerini bulur.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   Bu sorgu kalıcı ve döndüren kimliği, oluşturma zamanı (UTC saatiyle depolanır), askıya alınmış tüm örneklerini bulur askıya neden ve bunlar için özel durum adı.  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 Kalıcı olmayan örnekleri silerken dikkatli olun. Genel olarak, kalıcı olmayan örnekleri tarafından oluşturulan kaldırmak güvenli <xref:System.ServiceModel.Activities.WorkflowServiceHost> , askıya alınmış durumda veya yüklü değil. Bu belirli örnekleri onlardan silerek depolama alanından silinebilir `[System.Activities.DurableInstancing].[Instances]` doğru örneği kimlik değiştirerek aşağıdaki SQL komutunu kullanarak görünümü  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  Bu yeni oluşturduğunuz ve henüz kalıcı örnekleri içerdiğinden kalıcı olmayan tüm örneklerini kaldırma önermiyoruz.
