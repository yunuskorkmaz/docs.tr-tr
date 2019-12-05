---
title: Windows Workflow’a Genel Bakış
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: ada5ec75d130c9c518c5129db6c12b61c3acbf45
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802537"
---
# <a name="windows-workflow-overview"></a>Windows Workflow’a Genel Bakış
İş akışı, gerçek dünyada bir işlemi açıklayan bir model olarak depolanan *Etkinlikler* adlı bir dizi eleme birimi kümesidir. İş akışları, kısa veya uzun süreli iş parçaları arasında yürütme sırasını ve bağımlı ilişkileri açıklayan bir yol sağlar. Bu iş, başlangıçtan sona kadar modelden geçer ve Etkinlikler kişiler veya sistem işlevleri tarafından yürütülebilir.  
  
## <a name="workflow-run-time-engine"></a>İş akışı çalışma zamanı altyapısı  
 Çalışan her iş akışı örneği, ana bilgisayar işleminin aşağıdakilerden biri aracılığıyla etkileşimde bulunduğu işlem içi çalışma zamanı altyapısı tarafından oluşturulur ve sürdürülür:  
  
- Bir yöntemi gibi iş akışını çağıran <xref:System.Activities.WorkflowInvoker>.  
  
- Tek bir iş akışı örneğinin yürütülmesi üzerinde açık denetim için bir <xref:System.Activities.WorkflowApplication>.  
  
- Çok örnekli senaryolarda ileti tabanlı etkileşimler için bir <xref:System.ServiceModel.WorkflowServiceHost>.  
  
 Bu sınıfların her biri, etkinlik yürütmeden sorumlu bir <xref:System.Activities.ActivityInstance> olarak temsil edilen çekirdek etkinlik çalışma zamanını sarmalanmış olarak kaydırır. Aynı anda çalışan bir uygulama etki alanı içinde birkaç <xref:System.Activities.ActivityInstance> nesne bulunabilir.  
  
 Önceki üç ana bilgisayar etkileşimi nesnesinin her biri, iş akışı programı olarak adlandırılan bir etkinlik ağacından oluşturulur. Bu türleri veya <xref:System.Activities.ActivityInstance>sarmalayan özel bir ana bilgisayarı kullanarak, iş akışları konsol uygulamaları, Forms tabanlı uygulamalar, Windows Hizmetleri, ASP.NET Web siteleri ve Windows Communication Foundation (WCF) hizmetleri dahil olmak üzere herhangi bir Windows işlemi içinde yürütülebilir.  
  
 ![Konak işlemindeki iş akışı bileşenleri](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178B-4487-87ED-3e33015a3842")  
Konak işlemindeki iş akışı bileşenleri  
  
## <a name="interaction-between-workflow-components"></a>Iş akışı bileşenleri arasındaki etkileşim  
 Aşağıdaki diyagramda, iş akışı bileşenlerinin birbirleriyle nasıl etkileşim kurduğu gösterilmektedir.  
  
 ![İş akışı bileşenlerinin nasıl etkileşime gireceğini gösteren diyagram.](./media/overview/workflow-component-interatction.gif)  
  
 Önceki diyagramda, <xref:System.Activities.WorkflowInvoker> sınıfının <xref:System.Activities.WorkflowInvoker.Invoke%2A> yöntemi birkaç iş akışı örneğini çağırmak için kullanılır. <xref:System.Activities.WorkflowInvoker>, konaktan yönetim gerektirmeyen hafif iş akışları için kullanılır; ana bilgisayardan (örneğin, <xref:System.Activities.Bookmark> sürdürme) yönetilmesi gereken iş akışlarının, bunun yerine <xref:System.Activities.WorkflowApplication.Run%2A> kullanılarak yürütülmesi gerekir. Bir iş akışı örneğinin başka bir çağırmadan önce tamamlanmasını beklemek gerekmez; çalışma zamanı altyapısı birden çok iş akışı örneğinin aynı anda çalıştırılmasını destekler.  Çağrılan iş akışları aşağıdaki gibidir:  
  
- Bir <xref:System.Activities.Statements.WriteLine> alt etkinliği içeren <xref:System.Activities.Statements.Sequence> etkinliği. Üst etkinliğin bir <xref:System.Activities.Variable> alt etkinliğin bir <xref:System.Activities.InArgument> bağlanır. Değişkenler, bağımsız değişkenler ve bağlama hakkında daha fazla bilgi için bkz. [değişkenler ve bağımsız değişkenler](variables-and-arguments.md).  
  
- `ReadLine`adlı özel bir etkinlik. `ReadLine` etkinliğinin <xref:System.Activities.OutArgument> çağıran <xref:System.Activities.WorkflowInvoker.Invoke%2A> metoduna döndürülür.  
  
- <xref:System.Activities.CodeActivity> soyut sınıfından türetilen özel bir etkinlik. <xref:System.Activities.CodeActivity>, <xref:System.Activities.CodeActivity.Execute%2A> yönteminin bir parametresi olarak kullanılabilir <xref:System.Activities.CodeActivityContext> kullanarak çalışma zamanı özelliklerine (izleme ve özellikler gibi) erişebilir. Bu çalışma zamanı özellikleri hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](workflow-tracking-and-tracing.md) ve [Iş akışı yürütme özellikleri](workflow-execution-properties.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [2006 veya WF BizTalk Server? Projeniz için doğru Iş akışı aracını seçme](https://docs.microsoft.com/previous-versions/dotnet/articles/cc303238(v=msdn.10))
