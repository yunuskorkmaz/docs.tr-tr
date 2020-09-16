---
title: Windows Workflow’a Genel Bakış
description: Bu makalede, gerçek dünya süreçlerini tanımlayan modeller olan Workflow Foundation iş akışları açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: fc44adbe-1412-49ae-81af-0298be44aae6
ms.openlocfilehash: c54e405c5fff013f994f98cbf84fcce4d17d9d4e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558106"
---
# <a name="windows-workflow-overview"></a>Windows Workflow’a Genel Bakış
İş akışı, gerçek dünyada bir işlemi açıklayan bir model olarak depolanan *Etkinlikler* adlı bir dizi eleme birimi kümesidir. İş akışları, kısa veya uzun süreli iş parçaları arasında yürütme sırasını ve bağımlı ilişkileri açıklayan bir yol sağlar. Bu iş, başlangıçtan sona kadar modelden geçer ve Etkinlikler kişiler veya sistem işlevleri tarafından yürütülebilir.  
  
## <a name="workflow-run-time-engine"></a>İş akışı çalışma zamanı altyapısı  
 Çalışan her iş akışı örneği, ana bilgisayar işleminin aşağıdakilerden biri aracılığıyla etkileşimde bulunduğu işlem içi çalışma zamanı altyapısı tarafından oluşturulur ve sürdürülür:  
  
- Bir <xref:System.Activities.WorkflowInvoker> yöntemi gibi iş akışını çağıran bir.  
  
- <xref:System.Activities.WorkflowApplication>Tek bir iş akışı örneğinin yürütülmesi üzerinde açık bir denetim için.  
  
- <xref:System.ServiceModel.WorkflowServiceHost>Çok örnekli senaryolarda ileti tabanlı etkileşimler için A.  
  
 Bu sınıfların her biri, etkinlik yürütmeden sorumlu olarak temsil edilen çekirdek etkinlik çalışma zamanını sarmalanmış <xref:System.Activities.ActivityInstance> . <xref:System.Activities.ActivityInstance>Aynı anda çalışan bir uygulama etki alanı içinde birkaç nesne olabilir.  
  
 Önceki üç ana bilgisayar etkileşimi nesnesinin her biri, iş akışı programı olarak adlandırılan bir etkinlik ağacından oluşturulur. Bu türleri veya sarmalanmış bir özel Konağı kullanarak <xref:System.Activities.ActivityInstance> , iş akışları konsol uygulamaları, Forms tabanlı uygulamalar, Windows Hizmetleri, ASP.NET Web siteleri ve Windows Communication Foundation (WCF) hizmetleri dahil tüm Windows işlemleri içinde yürütülebilir.  
  
 ![Konak işlemindeki iş akışı bileşenleri](./media/44c79d1d-178b-4487-87ed-3e33015a3842.gif "44c79d1d-178B-4487-87ED-3e33015a3842")  
Konak işlemindeki iş akışı bileşenleri  
  
## <a name="interaction-between-workflow-components"></a>Iş akışı bileşenleri arasındaki etkileşim  
 Aşağıdaki diyagramda, iş akışı bileşenlerinin birbirleriyle nasıl etkileşim kurduğu gösterilmektedir.  
  
 ![İş akışı bileşenlerinin nasıl etkileşime gireceğini gösteren diyagram.](./media/overview/workflow-component-interatction.gif)  
  
 Önceki diyagramda, <xref:System.Activities.WorkflowInvoker.Invoke%2A> <xref:System.Activities.WorkflowInvoker> sınıfının yöntemi birkaç iş akışı örneğini çağırmak için kullanılır. <xref:System.Activities.WorkflowInvoker> , konaktan yönetim gerektirmeyen hafif iş akışları için kullanılır; ana bilgisayardan (örneğin, sürdürme) yönetilmesi gereken iş akışlarının <xref:System.Activities.Bookmark> yerine kullanılarak yürütülmesi gerekir <xref:System.Activities.WorkflowApplication.Run%2A> . Bir iş akışı örneğinin başka bir çağırmadan önce tamamlanmasını beklemek gerekmez; çalışma zamanı altyapısı birden çok iş akışı örneğinin aynı anda çalıştırılmasını destekler.  Çağrılan iş akışları aşağıdaki gibidir:  
  
- <xref:System.Activities.Statements.Sequence>Alt etkinlik içeren bir etkinlik <xref:System.Activities.Statements.WriteLine> . <xref:System.Activities.Variable>Üst etkinliğin bir öğesi alt etkinliğin bir öğesine bağlanır <xref:System.Activities.InArgument> . Değişkenler, bağımsız değişkenler ve bağlama hakkında daha fazla bilgi için bkz. [değişkenler ve bağımsız değişkenler](variables-and-arguments.md).  
  
- Özel bir etkinlik çağırılır `ReadLine` . <xref:System.Activities.OutArgument> `ReadLine` Etkinlik, çağırma yöntemine döndürülür <xref:System.Activities.WorkflowInvoker.Invoke%2A> .  
  
- Soyut sınıftan türetilen özel etkinlik <xref:System.Activities.CodeActivity> . , <xref:System.Activities.CodeActivity> <xref:System.Activities.CodeActivityContext> Yönteminin bir parametresi olarak kullanılabilir olan çalışma zamanı özelliklerine (izleme ve özellikler gibi) erişebilir <xref:System.Activities.CodeActivity.Execute%2A> . Bu çalışma zamanı özellikleri hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](workflow-tracking-and-tracing.md) ve [Iş akışı yürütme özellikleri](workflow-execution-properties.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [2006 veya WF BizTalk Server? Projeniz için doğru Iş akışı aracını seçme](/previous-versions/dotnet/articles/cc303238(v=msdn.10))
