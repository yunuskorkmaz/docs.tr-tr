---
title: "Örnek etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: de2152e557ccfe19c47247e2501f2e2d62253e81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="instance-activation"></a>Örnek etkinleştirme
SQL iş akışı örneği deposuna düzenli aralıklarla uyanır ve runnable veya activatable iş akışı örnekleri Kalıcılık veritabanında algılar iç bir görev çalıştırır. Runnable iş akışı örneği bulursa örneği etkinleştirilirken özelliğine sahip iş akışı ana bildirir. Örnek deposuna activatable iş akışı örneği bulursa, sırayla iş akışı örneği çalıştıran bir iş akışı ana etkinleştirir genel bir ana bilgisayar bildirir. Bu konudaki aşağıdaki bölümlerde ayrıntılı örneği etkinleştirme işlemi açıklanmaktadır.  
  
##  <a name="RunnableSection"></a>Algılama ve Runnable iş akışı örnekleri etkinleştirme  
 SQL iş akışı örneği deposuna bir iş akışı örneği göz önünde bulundurur *runnable* örneği askıya alınmış durumda veya tamamlanmış durumda değilse ve aşağıdaki koşulları karşılayan:  
  
-   Örnek kilidi ve süresi dolmuş bekleyen bir süreölçeri vardır.  
  
-   Örneğinin süresi dolmuş bir kilit üzerinde vardır.  
  
-   Kilidi açılmış bir örneğidir ve durumunun **Executing**.  
  
 SQL iş akışı örneği deposuna başlatır <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> runnable örneği bulduğunda. Bundan sonra SqlWorkflowInstanceStore durdurur kadar izleme <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> Mağaza'bir kez çağrılır.  
  
 Abone bir iş akışı ana <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> ve yükleme yeteneğine örneği yürütür <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> belleğe örneği yüklemek için örnek deposuna karşı. Bir iş akışı ana ana bilgisayar ve örnek meta veri özelliği varsa, bir iş akışı örneği yükleniyor uyumlu olarak kabul edilir **WorkflowServiceType** aynı değere ayarlayın.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Algılama ve Activatable iş akışı örnekleri etkinleştirme  
 Bir iş akışı örneği olarak kabul *activatable* runnable bir örneğidir ve varsa örnek yüklenirken özelliğine sahip hiçbir iş akışı ana bilgisayarda çalışan. Algılama ve etkinleştirme Runnable iş akışı örnekleri yukarıda runnable iş akışı örneği tanımları için bkz.  
  
 SQL iş akışı örneği deposuna başlatır <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> veritabanında activatable iş akışı örneği bulduğunda bunu. Bundan sonra SqlWorkflowInstanceStore durdurur kadar izleme <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> Mağaza'bir kez çağrılır.  
  
 İçin abone genel bir ana bilgisayarın <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> olayı aldığı yürütülmeden <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> bir iş akışı ana oluşturmak için gereken etkinleştirme parametrelerini elde etmek için örnek deposuna karşı. Genel ana bilgisayar, sırayla yükler ve runnable hizmet örneği çalıştıran bir iş akışı ana bilgisayar oluşturmak için bu etkinleştirme parametreleri kullanır.  
  
## <a name="generic-hosts"></a>Genel ana bilgisayar  
 Meta veri özelliğinin değeri olan bir konak genel bir ana bilgisayardır **WorkflowServiceType** için genel barındıran ayarlamak **WorkflowServiceType.Any** herhangi bir iş akışı türü işleyebileceğini belirtmek için. Genel ana bilgisayar adında bir XName parametresine sahip **ActivationType**.  
  
 Şu anda SQL iş akışı örneği deposuna kümesine ActivationType parametresinin değeri genel konaklarla destekleyen **WAS**. SQL iş akışı örneği deposuna ActivationType WAS ayarlanmamışsa oluşturur bir <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. İş akışı yönetimi hizmeti ile birlikte [!INCLUDE[dublin](../../../includes/dublin-md.md)] kümesine etkinleştirme türüne sahip genel bir ana bilgisayar **WAS**.  
  
 WAS etkinleştirme için genel bir konağı yeni konakları etkinleştirilebilmesi için uç nokta adresi çıkarmaya Etkinleştirme parametreleri kümesini gerektiriyor. Site, uygulama site göreli yolu ve hizmet uygulama göreli yol adını WAS etkinleştirme için etkinleştirme parametreleridir. SQL iş akışı örneği deposuna yürütülmesi sırasında bu etkinleştirme parametreleri depolar <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>.  
  
## <a name="runnable-instances-detection-period"></a>Runnable örnekleri algılama süresi  
 **Runnable örnekleri algılama süresi** özelliği SQL iş akışı örneği deposunun SQL iş akışı örneği deposuna sonra hiçbir runnable veya activatable iş akışı algılamak için algılama görev çalıştırır süre belirtir Önceki algılama döngüsü sonra Kalıcılık veritabanındaki örnekleri. Bkz: [Runnable örnekleri algılama süresi](../../../docs/framework/windows-workflow-foundation/runnable-instances-detection-period.md) bu özellik hakkında daha fazla ayrıntı için.
