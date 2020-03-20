---
ms.openlocfilehash: 470fc2ddcfbb29a677cadb6e7e1d2e55784d7ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802484"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>İş akışı artık bazı durumlarda NullReferenceException yerine özgün özel durum atar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ve önceki sürümlerinde, bir iş akışı etkinliğinin Yürütme <code>null</code> yöntemi <xref:System.Exception.Message> özellik için bir değeriçeren bir özel <xref:System.NullReferenceException?displayProperty=name>durum attığında, System.Activities Workflow çalışma zamanı, özgün özel durum maskeleme özelliğini bir leştirir. .NET Framework 4.7'de, daha önce maskelen edilen özel durum atılır.|
|Öneri|Kodunuz işleme <xref:System.NullReferenceException?displayProperty=name>güveniyorsa, özel etkinliklerinizden atılabilecek özel durumları yakalamak için değiştirin.|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
