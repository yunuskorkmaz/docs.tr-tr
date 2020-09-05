---
ms.openlocfilehash: 61d5885c19e39b138090c1a98fa26348724893c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496615"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>İş akışı artık bazı durumlarda NullReferenceException yerine özgün özel durum oluşturur

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 ve önceki sürümlerde, bir iş akışı etkinliğinin Execute yöntemi özelliği için bir değer ile özel durum oluşturduğunda <code>null</code> <xref:System.Exception.Message> , System. Activities iş akışı çalışma zamanı bir oluşturur <xref:System.NullReferenceException?displayProperty=fullName> , özgün özel durumu maskeleyerek. .NET Framework 4,7 ' de, daha önce maskelenmiş özel durum oluşturulur.

#### <a name="suggestion"></a>Öneri

Kodunuz işleme alıyorsa <xref:System.NullReferenceException?displayProperty=fullName> , özel etkinliklerinizde oluşturulabilecek özel durumları yakalamak için değiştirin.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,7|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)`
- `M:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)`
- ``M:System.Activities.AsyncCodeActivity`1.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)``
- `M:System.Activities.WorkflowInvoker.Invoke`

-->
