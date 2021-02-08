---
description: 'Daha fazla bilgi edinin: kalıcı olmayan Iş akışı örnekleri'
title: Kalıcı Olmayan İş Akışı Örnekleri
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 0ee5968426a6bb800b9e70ac592c6da191c22511
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787909"
---
# <a name="non-persisted-workflow-instances"></a>Kalıcı Olmayan İş Akışı Örnekleri

İçinde durumunu devam eden yeni bir iş akışı örneği oluşturulduğunda <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , hizmet ana bilgisayarı örnek deposunda bu hizmet için bir giriş oluşturur. Daha sonra, iş akışı örneği ilk kez kalıcı olduğunda, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> geçerli örnek durumunu depolar. İş akışı Windows Işlem etkinleştirme hizmetinde barındırılıyorsa, örnek ilk kez kalıcı olduğunda hizmet dağıtım verileri de örnek deposuna yazılır.

İş akışı örneği kalıcı olmadığı sürece **kalıcı olmayan** bir durumda. Bu durumda, bir uygulama etki alanı geri dönüştürme, ana bilgisayar arızası veya bilgisayar hatasından sonra iş akışı örneği kurtarılamaz.

## <a name="the-non-persisted-state"></a>Kalıcı olmayan durum

Kalıcı olmayan dayanıklı iş akışı örnekleri aşağıdaki durumlarda kalıcı olmayan bir durumda kalır:

- Hizmet ana bilgisayarı, iş akışı örneği ilk kez kalıcı hale gelmeden önce çöker. İş akışı örneği örnek deposunda kalır ve kurtarılmaz. Bağıntılı bir ileti alınırsa, iş akışı örneği tekrar etkin hale gelir.

- İş akışı örneği, ilk kez kalıcı hale gelmeden önce bir özel durum yaşanır. Döndürülen öğesine bağlı olarak <xref:System.Activities.UnhandledExceptionAction> , aşağıdaki senaryolar oluşur:

  - <xref:System.Activities.UnhandledExceptionAction> Şu şekilde ayarlanır <xref:System.Activities.UnhandledExceptionAction.Abort> : bir özel durum oluştuğunda, hizmet dağıtım bilgileri örnek deposuna yazılır ve iş akışı örneği bellekten kaldırılır. İş akışı örneği kalıcı olmayan bir durumda kalır ve yeniden yüklenemez.

  - <xref:System.Activities.UnhandledExceptionAction> veya olarak ayarlanır <xref:System.Activities.UnhandledExceptionAction.Cancel> <xref:System.Activities.UnhandledExceptionAction.Terminate> : bir özel durum oluştuğunda, hizmet dağıtım bilgileri örnek deposuna yazılır ve etkinlik örneği durumu olarak ayarlanır <xref:System.Activities.ActivityInstanceState.Closed> .

Kaldırılmış kalıcı olmayan iş akışı örneklerinin denenmesinin riskini en aza indirmek için iş akışının yaşam döngüsünün başlarında kalıcı olmasını öneririz.

## <a name="detection-and-removal-of-non-persisted-instances"></a>Kalıcı olmayan örneklerin algılanması ve kaldırılması

, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Hiçbir kalıcı olmayan iş akışı örneğini örnek deposundan kaldırmaz. Ayrıca bunlarla ilişkili kalıcı olmayan iş akışı örneklerine sahip olan süre dolmayan kilit sahiplerini kaldırmaz.

Yöneticinin örnek deposunu kalıcı olmayan örnekler için düzenli olarak denetlemesini öneririz. Yöneticiler, bu iş akışının bağıntılı iletileri almadıkları sürece bu örnekleri örnek deposundan kaldırabilir. Örneğin, örnek veritabanında birkaç ay boyunca bulunuyorsa ve iş akışının genellikle birkaç güne sahip olduğu bilinmektedir, bu da kilitlenen başlatılmış bir örnek olduğunu varsaymak güvenli olacaktır.

SQL Iş akışı örneği deposundaki kalıcı olmayan örnekleri bulmak için aşağıdaki SQL sorgularını kullanabilirsiniz:

- Bu sorgu kalıcı olmayan tüm örnekleri bulur ve bunlar için KIMLIK ve oluşturma saati (UTC saat olarak saklanır) döndürür.

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- Bu sorgu kalıcı olmayan ve yüklenmeyen tüm örnekleri bulur ve bunlar için KIMLIK ve oluşturma saati (UTC saat olarak saklanır) döndürür.

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- Bu sorgu kalıcı olmayan tüm askıya alınmış örnekleri bulur ve KIMLIK, oluşturma saati (UTC zaman içinde depolanan), askıya alma nedeni ve bunlar için özel durum adı döndürür.

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

Kalıcı olmayan örnekleri silerken dikkatli kullanın. Genel olarak, tarafından oluşturulan veya yüklenmeyen kalıcı olmayan örneklerin kaldırılması güvenlidir <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Bu belirli örnekler, `[System.Activities.DurableInstancing].[Instances]` doğru örnek kimliği yerine, AŞAĞıDAKI SQL komutu kullanılarak görünümden silinerek depolamadan silinebilir.

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> Kalıcı olmayan tüm örnekleri kaldırmanızı önermeyiz çünkü bu, az önce oluşturulmuş ve henüz kalıcı olmayan örnekler içeriyor.
