---
ms.openlocfilehash: 470fc2ddcfbb29a677cadb6e7e1d2e55784d7ac2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764070"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>İş akışı şimdi bazı durumlarda NullReferenceException yerine özgün özel durum oluşturur

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 ve yürütme yönteminin bir iş akışı etkinliği ile bir özel durum oluşturduğunda önceki sürümlerinde, bir <code>null</code> değerini <xref:System.Exception.Message> özelliği System.Activities iş akışı çalışma zamanı oluşturur bir <xref:System.NullReferenceException?displayProperty=name>, maskeleme özgün özel durum. .NET Framework 4.7 daha önce maskelenmiş özel durum oluşturulur.|
|Öneri|Kodunuz üzerinde işleme dayanıyorsa <xref:System.NullReferenceException?displayProperty=name>, özel etkinliklerinizi oluşturulan özel durumları yakalamak için değiştirin.|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
