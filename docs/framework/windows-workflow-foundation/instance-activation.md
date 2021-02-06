---
description: Örnek etkinleştirme hakkında daha fazla bilgi edinin
title: Örnek Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: a301f49fb79e7c74cd3a64e891526e5b89fdd1c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631209"
---
# <a name="instance-activation"></a>Örnek Etkinleştirme

SQL Iş akışı örneği deposu, düzenli aralıklarla uyandığı ve kalıcılık veritabanındaki runetkinleştirilebilir veya iş akışı örneklerini algılayan bir iç görev çalıştırır. Bir çalıştırılabilir iş akışı örneği bulursa, örneği etkinleştirebilen iş akışı konağına bildirir. Örnek deposunda bir etkinleştirilebilir iş akışı örneği bulunursa, iş akışı örneğini çalıştıran bir iş akışı konağını etkinleştiren genel bir konağa bildirir. Bu konudaki aşağıdaki bölümlerde örnek etkinleştirme işlemi ayrıntılı olarak açıklanmaktadır.  
  
## <a name="detecting-and-activating-runnable-workflow-instances"></a><a name="RunnableSection"></a> Çalıştırılabilir Iş akışı örnekleri algılanıyor ve etkinleştiriliyor  

 SQL Iş akışı örneği deposu, örnek askıya alınma durumunda veya tamamlanmış durumda değilse, *çalıştırılabilir* bir iş akışı örneğini kabul eder ve aşağıdaki koşulları karşılar:  
  
- Örneğin kilidi açık ve süresi geçmiş bir bekleme süreölçeri vardır.  
  
- Örneğin, üzerinde süresi doldu kilidi vardır.  
  
- Örneğin kilidi açıldı ve durumu **yürütülüyor**.  
  
 SQL Iş akışı örneği deposu, <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> bir runbir örnek bulduğunda öğesini oluşturur. Bundan sonra SqlWorkflowInstanceStore, <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> depoda bir kez çağrılana kadar izlemeyi durduruyor.  
  
 İçin abone olan ve örneği yükleyebilen bir iş akışı ana bilgisayarı örneği <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> belleğe yüklemek için örnek deposuna karşı yürütülür. Konak ve örnekte, **WorkflowServiceType** meta veri özelliği aynı değere ayarlanmışsa bir iş akışı konağı, bir iş akışı örneği yükleme yeteneğine sahip olarak kabul edilir.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Etkinleştirilebilir Iş akışı örnekleri algılanıyor ve etkinleştiriliyor  

 Örnek çalıştırılabilir ise, bir iş akışı örneği *etkinleştirilebilir* olarak kabul edilir ve örneğin bilgisayarda çalışan bir iş akışı konağı yoktur. Bkz. runsee iş akışı örneği tanımı için yukarıdaki çalıştırılabilir Iş akışı örneklerini algılama ve etkinleştirme.  
  
 SQL Iş akışı örneği deposu, <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> veritabanında bir etkinleştirilebilir iş akışı örneği bulduğunda öğesini başlatır. Bundan sonra SqlWorkflowInstanceStore, <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> depoda bir kez çağrılana kadar izlemeyi durduruyor.  
  
 İçin abone olan bir genel ana bilgisayar <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> olayı aldığında, <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> bir iş akışı konağı oluşturmak için gereken etkinleştirme parametrelerini elde etmek üzere örnek deposuna karşı yürütülür. Genel ana bilgisayar bu etkinleştirme parametrelerini, bir iş akışı konağı oluşturmak için kullanır, bu da çalıştırılabilir hizmet örneğini yükler ve çalıştırır.  
  
## <a name="generic-hosts"></a>Genel konaklar  

 Genel ana bilgisayar, genel konaklar için **WorkflowServiceType** meta veri özelliğinin değerini içeren bir ana bilgisayar, **WorkflowServiceType olarak ayarlanmıştır. herhangi** bir iş akışı türünü Işleyebileceğini belirtmek için Any. Genel ana bilgisayar **ActivationType** adlı bir XName parametresine sahiptir.  
  
 Şu anda SQL Iş akışı örneği deposu, ActivationType parametresinin değeri **was** olarak ayarlanan genel Konakları destekler. ActivationType, olarak ayarlanmamışsa, SQL Iş akışı örneği deposu bir oluşturur <xref:System.Runtime.DurableInstancing.InstancePersistenceException> . Windows Server AppFabric barındırma özellikleriyle birlikte gelen Iş akışı yönetim hizmeti, etkinleştirme türü **was** olarak ayarlanmış olan genel bir ana bilgisayar.  
  
 WAS etkinleştirmesi için, genel bir ana bilgisayar, yeni ana bilgisayarların etkinleştiribileceği uç nokta adresini türeten bir etkinleştirme parametreleri kümesi gerektirir. WAS etkinleştirme için etkinleştirme parametreleri sitenin adı, siteye göre uygulamanın yolu ve uygulamaya göre hizmetin yoludur. SQL Iş akışı örneği deposu, yürütme sırasında bu etkinleştirme parametrelerini depolar <xref:System.Activities.DurableInstancing.SaveWorkflowCommand> .  
  
## <a name="runnable-instances-detection-period"></a>Çalıştırılabilir Örnekleri Algılama Dönemi  

 SQL Iş akışı örneği deposunun **çalıştırılabilir örnek algılama dönemi** ÖZELLIĞI, SQL Iş akışı örneği deposunun, önceki algılama döngüsünden sonra kalıcılık veritabanında herhangi bir çalıştırılabilir veya etkinleştirilebilir iş akışı örneğini algılamak için bir algılama görevi çalıştırması için geçen süreyi belirtir. Bu özellik hakkında daha fazla bilgi için bkz. [çalıştırılabilir örnekler algılama süresi](runnable-instances-detection-period.md) .
