---
title: İş Akışı Örneği Oluşturma ve Çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016041"
---
# <a name="creating-and-running-a-workflow-instance"></a>İş Akışı Örneği Oluşturma ve Çalıştırma

Bu örnek, bir iş akışı örneğinin nasıl çalıştırılacağını gösterir. Bu, zaman uyumlu ve zaman uyumsuz olarak nasıl yürütüleceğini gösterir.

## <a name="demonstrates"></a>Gösteriler

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Tartışma

Örneğin ilk bölümü kullanır <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Bu, bir iş akışını yürütmek için en temel yoldur. İle <xref:System.Activities.WorkflowInvoker.Invoke%2A> yürütülen iş akışları zaman uyumlu olarak yürütülür.

Örneğin ikinci bölümü <xref:System.Activities.WorkflowApplication> sınıfını kullanır. <xref:System.Activities.WorkflowApplication>çalışan iş akışıyla etkileşim kurma ve iş akışını zaman uyumsuz olarak çalıştırma özelliği de dahil olmak üzere her bir örnek üzerinde daha fazla denetime sahip olmasını sağlar.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Ayrıca bkz.

- [WorkflowInvoker ve WorkflowApplication Kullanma](../using-workflowinvoker-and-workflowapplication.md)
