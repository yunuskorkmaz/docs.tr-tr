---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616085"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="c2206-101">WorkflowDesigner. Load, sembol özelliğini kaldırmaz</span><span class="sxs-lookup"><span data-stu-id="c2206-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

#### <a name="details"></a><span data-ttu-id="c2206-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c2206-102">Details</span></span>

<span data-ttu-id="c2206-103">İş akışı tasarımcısında .NET Framework 4,5 ' i hedeflerken ve yöntemi ile yeniden barındırılan bir 3,5 iş akışını yüklerken, <xref:System.Activities.Presentation.WorkflowDesigner.Load> <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> iş akışı kaydedilirken bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c2206-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> is thrown while saving the workflow.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c2206-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="c2206-104">Suggestion</span></span>

<span data-ttu-id="c2206-105">Bu hata yalnızca iş akışı tasarımcısında .NET Framework 4,5 ' i hedeflerken bildirimler. bu nedenle, ' ı 4,0 .NET Framework ayarlanarak geçici olarak gerçekleştirilebilir `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` . alternatif olarak, <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> bunun yerine iş akışını yüklemek için yöntemi kullanılarak sorun önlenebilir <xref:System.Activities.Presentation.WorkflowDesigner.Load> .</span><span class="sxs-lookup"><span data-stu-id="c2206-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>

| <span data-ttu-id="c2206-106">Name</span><span class="sxs-lookup"><span data-stu-id="c2206-106">Name</span></span>    | <span data-ttu-id="c2206-107">Değer</span><span class="sxs-lookup"><span data-stu-id="c2206-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c2206-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c2206-108">Scope</span></span>   | <span data-ttu-id="c2206-109">Ana</span><span class="sxs-lookup"><span data-stu-id="c2206-109">Major</span></span>       |
| <span data-ttu-id="c2206-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="c2206-110">Version</span></span> | <span data-ttu-id="c2206-111">4,5</span><span class="sxs-lookup"><span data-stu-id="c2206-111">4.5</span></span>         |
| <span data-ttu-id="c2206-112">Tür</span><span class="sxs-lookup"><span data-stu-id="c2206-112">Type</span></span>    | <span data-ttu-id="c2206-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="c2206-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c2206-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c2206-114">Affected APIs</span></span>

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
