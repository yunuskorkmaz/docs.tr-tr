---
title: Örnek etkinleştirme
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 41dfc076bdee72c2f4d0c781c6588caa927c740e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703406"
---
# <a name="instance-activation"></a>Örnek etkinleştirme
SQL iş akışı örneği Store düzenli olarak çalıştırılabilir veya etkinleştirilebilir iş akışı örnekleri Kalıcılık veritabanında algılar ve uyanır bir iç görev çalıştırır. Bir çalıştırılabilir iş akışı örneği bulursa örneğin etkinleştirme özelliğine sahip olan iş akışı ana bilgisayarı bildirir. Örnek deposuna etkinleştirilebilir iş akışı örneği bulursa, sırayla iş akışı örneği çalıştıran bir iş akışı ana etkinleştiren genel bir ana bilgisayar bildirir. Bu konunun aşağıdaki bölümlerinde ayrıntılı örnek etkinleştirme işlemi açıklanmaktadır.  
  
## <a name="RunnableSection"></a> Algılama ve çalıştırılabilir iş akışı örnekleri etkinleştirme  
 SQL iş akışı örneği Store iş akışı örneği göz önünde bulundurur *çalıştırılabilir* örneği askıya alınma durumunda veya tamamlandı durumuna değilse ve aşağıdaki koşulları karşılayan:  
  
-   Örnek kilitli olup süresi doldu bekleyen bir zamanlayıcı içerir.  
  
-   Örneğinin süresi dolmuş bir kilit üzerinde vardır.  
  
-   Örnek kilidi açılmış ve durumunun **Executing**.  
  
 SQL iş akışı örneği Store başlatır <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> çalıştırılabilir bir örneği bulduğunda. Bundan sonra SqlWorkflowInstanceStore durdurur kadar izleme <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> mağaza kez çağrılır.  
  
 Abone bir iş akışı ana bilgisayarı <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> ve yükleme özellikli örneği yürütür <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> belleğe örneği yüklemek için örnek deposu ile karşılaştırarak. Bir iş akışı ana bilgisayarı ana bilgisayar ve örnek meta veri özelliği varsa, bir iş akışı örneği yükleniyor uyumlu olarak kabul edilir **WorkflowServiceType** aynı değere ayarlar.  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>Algılama ve etkinleştirilebilir iş akışı örnekleri etkinleştirme  
 Bir iş akışı örneği kabul *etkinleştirilebilir* örneği çalıştırılabilir ve varsa örneği yüklerken birini özelliğine sahip olan hiçbir iş akışı ana bilgisayarda çalışan. Algılama ve etkinleştirme çalıştırılabilir iş akışı örnekleri üzerinde çalıştırılabilir bir iş akışı örneğinin tanımını için bkz.  
  
 SQL iş akışı örneği Store başlatır <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> veritabanında etkinleştirilebilir iş akışı örneği bulduğunda bu. Bundan sonra SqlWorkflowInstanceStore durdurur kadar izleme <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> mağaza kez çağrılır.  
  
 Bir genel ana bilgisayar için abone olduğunda <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> olay aldığında yürütülmeden <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> etkinleştirme parametresi bir iş akışı ana bilgisayar oluşturmak için gereken almak için örnek deposu ile karşılaştırarak. Genel konak hangi sırayla yükler ve çalıştırılabilir hizmet örneği çalıştıran bir iş akışı ana bilgisayar oluşturmak için bu etkinleştirme parametrelerini kullanır.  
  
## <a name="generic-hosts"></a>Genel konakları  
 Meta veri özelliğinin değeri olan bir konak genel yöneticisidir **WorkflowServiceType** genel konakları için ayarlanmış **WorkflowServiceType.Any** herhangi bir iş akışı türü işleyebileceğini belirtmek için. Genel bir ana bilgisayar adında bir XName parametresinin **ActivationType**.  
  
 Şu anda SQL iş akışı örneği Store kümesine ActivationType parametresinin değeri genel konaklarla destekler **WAS**. SQL iş akışı örneği Store ActivationType WAS için ayarlanmazsa, oluşturur bir <xref:System.Runtime.DurableInstancing.InstancePersistenceException>. İş akışı yönetimi hizmeti ile birlikte gelen [!INCLUDE[dublin](../../../includes/dublin-md.md)] kümesine etkinleştirme türü olan genel bir ana bilgisayar **WAS**.  
  
 WAS etkinleştirme için genel bir konağa bir dizi yeni konakları etkinleştirilebilmesi için uç nokta adresini türetmek için etkinleştirme parametresi gerektirir. WAS etkinleştirme için etkinleştirme site, uygulamanın site göreli yolunu ve hizmetinin uygulama göreli yolunu adını parametrelerdir. SQL iş akışı örneği Store yürütülmesi sırasında bu etkinleştirme parametreleri depolayan <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>.  
  
## <a name="runnable-instances-detection-period"></a>Çalıştırılabilir örnekleri algılama dönemi  
 **Çalıştırılabilir örnekleri algılama dönemi** SQL iş akışı örneği Store özelliği SQL iş akışı örneği Store sonra çalıştırılabilir veya etkinleştirilebilir akışlarınızın algılamak için algılama görev çalıştırır süreyi belirtir Önceki saptama döngüsünden sonra Kalıcılık veritabanı örnekleri. Bkz: [çalıştırılabilir örnekleri algılama dönemi](runnable-instances-detection-period.md) bu özellik hakkında daha fazla bilgi.
