---
title: İş Akışı Örneği Oluşturma ve Çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715197"
---
# <a name="creating-and-running-a-workflow-instance"></a>İş Akışı Örneği Oluşturma ve Çalıştırma

Bu örnek, bir iş akışı örneğinin nasıl çalıştırılacağını gösterir. Bu, zaman uyumlu ve zaman uyumsuz olarak nasıl yürütüleceğini gösterir.

## <a name="demonstrates"></a>Gösterir

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Tartışma

Örneğin ilk bölümü <xref:System.Activities.WorkflowInvoker.Invoke%2A>kullanır. Bu, bir iş akışını yürütmek için en temel yoldur. <xref:System.Activities.WorkflowInvoker.Invoke%2A> ile yürütülen iş akışları zaman uyumlu olarak yürütülür.

Örneğin ikinci bölümü <xref:System.Activities.WorkflowApplication> sınıfını kullanır. <xref:System.Activities.WorkflowApplication>, çalışan iş akışıyla etkileşim kurma ve iş akışını zaman uyumsuz olarak çalıştırma özelliği de dahil olmak üzere her bir örnek üzerinde daha fazla denetime sahip olmasını sağlar.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Ayrıca bkz.

- [WorkflowInvoker ve WorkflowApplication Kullanma](../using-workflowinvoker-and-workflowapplication.md)
