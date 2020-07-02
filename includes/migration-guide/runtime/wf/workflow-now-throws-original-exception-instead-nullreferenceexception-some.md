---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621392"
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
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
