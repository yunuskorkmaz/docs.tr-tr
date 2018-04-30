---
title: Windows iş akışı genel bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc1aa65b413b87b27c05e7a12ce607d1cd30b89b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="windows-workflow-overview"></a>Windows iş akışı genel bakış
Bir iş akışı olarak adlandırılan elemental birimler kümesidir *etkinlikleri* gerçek işlem açıklayan model olarak depolanır. İş akışı yürütme ve kısa veya uzun süre çalışan iş parçalarını bağımlı ilişkiler sırasını açıklayan bir yol sağlar. Bu iş modeli aracılığıyla baştan geçirir ve etkinlikleri, kişiler veya sistem işlevleri tarafından yürütülen.  
  
## <a name="workflow-run-time-engine"></a>İş akışı çalışma zamanı altyapısı  
 Çalışan her iş akışı örneği oluşturulur ve ana bilgisayar işlemi şunlardan birini etkileşimde, bir işlem çalışma zamanı altyapısı tarafından saklanır:  
  
-   A <xref:System.Activities.WorkflowInvoker>, iş akışı gibi bir yöntemi çağırır.  
  
-   A <xref:System.Activities.WorkflowApplication> tek iş akışı örneğini yürütmeyi üzerinde açık denetim için.  
  
-   A <xref:System.ServiceModel.WorkflowServiceHost> ileti tabanlı etkileşimleri çok örnekli senaryolarda.  
  
 Bu sınıfların her biri olarak gösterilen çekirdek etkinlik çalışma zamanı saran bir <xref:System.Activities.ActivityInstance> Etkinlik yürütme sorumlu. Birkaç da olabilir <xref:System.Activities.ActivityInstance> eşzamanlı olarak çalışan bir uygulama etki alanı içindeki nesneleri.  
  
 Yukarıdaki üç ana etkileşim nesnelerin her biri için bir iş akışı program olarak adlandırılan etkinliklerin ağacından oluşturulur. Bu tür veya sarmalar özel bir ana bilgisayar kullanarak <xref:System.Activities.ActivityInstance>, konsol uygulamaları dahil olmak üzere herhangi bir Windows işlemi içinde iş akışları yürütülebilir form tabanlı uygulamalar, Windows Hizmetleri [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web siteleri ve [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Hizmetleri.  
  
 ![Ana bilgisayar işlemi iş akışı bileşenlerinde](../../../docs/framework/windows-workflow-foundation/media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178b-4487-87ed-3e33015a3842")  
Ana bilgisayar işlemi iş akışı bileşenleri  
  
## <a name="interaction-between-workflow-components"></a>İş akışı bileşenler arasındaki etkileşimi  
 Aşağıdaki diyagramda, iş akışı bileşenlerinin birbirleriyle nasıl etkileşim kurduğu gösterilmektedir.  
  
 ![İş akışı etkileşim](../../../docs/framework/windows-workflow-foundation/media/workflowinteraction.gif "WorkflowInteraction")  
  
 Yukarıdaki diyagramda <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemi <xref:System.Activities.WorkflowInvoker> sınıfı birkaç iş akışı örnekleri çağırmak için kullanılır. <xref:System.Activities.WorkflowInvoker> ana bilgisayardan yönetim gerekmez basit iş akışları için kullanılır; ana bilgisayardan yönetim gereken iş akışları (gibi <xref:System.Activities.Bookmark> sürdürme) kullanarak yürütülmelidir <xref:System.Activities.WorkflowApplication.Run%2A> yerine. Bir iş akışı örneği başka çağırmadan önce tamamlanmasını beklemek için gerekli değildir; çalışma zamanı altyapısı, aynı anda birden çok iş akışı örneği çalıştırılmasını destekler.  Çağrılan iş akışları aşağıdaki gibidir:  
  
-   A <xref:System.Activities.Statements.Sequence> içeren etkinliği bir <xref:System.Activities.Statements.WriteLine> alt etkinlik. A <xref:System.Activities.Variable> üst etkinlik bağlı bir <xref:System.Activities.InArgument> alt etkinlik. Değişkenleri, bağımsız değişkenler ve bağlama hakkında daha fazla bilgi için bkz: [değişkenleri ve bağımsız değişkenler](../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
-   Özel bir aktivite olarak adlandırılan `ReadLine`. Bir <xref:System.Activities.OutArgument> , `ReadLine` etkinlik için arama döndürülen <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemi.  
  
-   Türetilen özel bir aktivite <xref:System.Activities.CodeActivity> soyut sınıf. <xref:System.Activities.CodeActivity> (Örneğin, izleme ve özellikleri) çalışma zamanı özelliklere erişebilir kullanarak <xref:System.Activities.CodeActivityContext> bir parametresi olarak kullanılabilir <xref:System.Activities.CodeActivity.Execute%2A> yöntemi. Bu çalışma zamanı özellikleri hakkında daha fazla bilgi için bkz: [izleme ve izleme iş akışı](../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) ve [iş akışı yürütme özellikleri](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [BizTalk Server 2006 veya WF? Projeniz için doğru iş akışının aracı seçme](http://go.microsoft.com/fwlink/?LinkId=154901)
