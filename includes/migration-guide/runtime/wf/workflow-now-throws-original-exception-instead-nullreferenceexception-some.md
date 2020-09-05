---
ms.openlocfilehash: 61d5885c19e39b138090c1a98fa26348724893c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496615"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="00b70-101">İş akışı artık bazı durumlarda NullReferenceException yerine özgün özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="00b70-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="00b70-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="00b70-102">Details</span></span>

<span data-ttu-id="00b70-103">.NET Framework 4.6.2 ve önceki sürümlerde, bir iş akışı etkinliğinin Execute yöntemi özelliği için bir değer ile özel durum oluşturduğunda <code>null</code> <xref:System.Exception.Message> , System. Activities iş akışı çalışma zamanı bir oluşturur <xref:System.NullReferenceException?displayProperty=fullName> , özgün özel durumu maskeleyerek. .NET Framework 4,7 ' de, daha önce maskelenmiş özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00b70-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="00b70-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="00b70-104">Suggestion</span></span>

<span data-ttu-id="00b70-105">Kodunuz işleme alıyorsa <xref:System.NullReferenceException?displayProperty=fullName> , özel etkinliklerinizde oluşturulabilecek özel durumları yakalamak için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="00b70-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="00b70-106">Name</span><span class="sxs-lookup"><span data-stu-id="00b70-106">Name</span></span>    | <span data-ttu-id="00b70-107">Değer</span><span class="sxs-lookup"><span data-stu-id="00b70-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="00b70-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="00b70-108">Scope</span></span>   |<span data-ttu-id="00b70-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="00b70-109">Minor</span></span>|
|<span data-ttu-id="00b70-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="00b70-110">Version</span></span>|<span data-ttu-id="00b70-111">4,7</span><span class="sxs-lookup"><span data-stu-id="00b70-111">4.7</span></span>|
|<span data-ttu-id="00b70-112">Tür</span><span class="sxs-lookup"><span data-stu-id="00b70-112">Type</span></span>|<span data-ttu-id="00b70-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="00b70-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="00b70-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="00b70-114">Affected APIs</span></span>

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
