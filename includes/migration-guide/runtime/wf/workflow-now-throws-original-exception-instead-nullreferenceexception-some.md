---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760470"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="37340-101">İş akışı şimdi bazı durumlarda NullReferenceException yerine özgün özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="37340-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="37340-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="37340-102">Details</span></span>|<span data-ttu-id="37340-103">.NET Framework 4.6.2 ve yürütme yönteminin bir iş akışı etkinliği ile bir özel durum oluşturduğunda önceki sürümlerinde, bir <code>null</code> değerini <xref:System.Exception.Message> özelliği System.Activities iş akışı çalışma zamanı oluşturur bir <xref:System.NullReferenceException?displayProperty=name>, maskeleme özgün özel durum. .NET Framework 4.7 daha önce maskelenmiş özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="37340-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="37340-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="37340-104">Suggestion</span></span>|<span data-ttu-id="37340-105">Kodunuz üzerinde işleme dayanıyorsa <xref:System.NullReferenceException?displayProperty=name>, özel etkinliklerinizi oluşturulan özel durumları yakalamak için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="37340-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="37340-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="37340-106">Scope</span></span>|<span data-ttu-id="37340-107">İkincil</span><span class="sxs-lookup"><span data-stu-id="37340-107">Minor</span></span>|
|<span data-ttu-id="37340-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="37340-108">Version</span></span>|<span data-ttu-id="37340-109">4.7</span><span class="sxs-lookup"><span data-stu-id="37340-109">4.7</span></span>|
|<span data-ttu-id="37340-110">Tür</span><span class="sxs-lookup"><span data-stu-id="37340-110">Type</span></span>|<span data-ttu-id="37340-111">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="37340-111">Runtime</span></span>|
|<span data-ttu-id="37340-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="37340-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

