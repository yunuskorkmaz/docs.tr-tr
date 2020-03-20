---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804672"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="fc964-101">WorkflowDesigner.Load sembol özelliğini kaldırmaz</span><span class="sxs-lookup"><span data-stu-id="fc964-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fc964-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fc964-102">Details</span></span>|<span data-ttu-id="fc964-103">İş akışı tasarımcısında .NET Framework 4.5 hedeflenirken ve <xref:System.Activities.Presentation.WorkflowDesigner.Load> yöntemle yeniden barındırılan 3,5 iş akışı yüklenirken, iş akışı tasarruf edilirken bir <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> adım atılır.</span><span class="sxs-lookup"><span data-stu-id="fc964-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="fc964-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="fc964-104">Suggestion</span></span>|<span data-ttu-id="fc964-105">Bu hata yalnızca iş akışı tasarımcısında .NET Framework 4.5'i hedefalırken ortaya <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> çıkar, bu nedenle 4.0 .NET Framework.Alternatively'e <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> ayarlayarak iş akışı yerine <xref:System.Activities.Presentation.WorkflowDesigner.Load>.'yi yüklemek için yöntem kullanılarak sorun önlenebilir.</span><span class="sxs-lookup"><span data-stu-id="fc964-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="fc964-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="fc964-106">Scope</span></span>|<span data-ttu-id="fc964-107">Ana</span><span class="sxs-lookup"><span data-stu-id="fc964-107">Major</span></span>|
|<span data-ttu-id="fc964-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="fc964-108">Version</span></span>|<span data-ttu-id="fc964-109">4,5</span><span class="sxs-lookup"><span data-stu-id="fc964-109">4.5</span></span>|
|<span data-ttu-id="fc964-110">Tür</span><span class="sxs-lookup"><span data-stu-id="fc964-110">Type</span></span>|<span data-ttu-id="fc964-111">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="fc964-111">Retargeting</span></span>|
|<span data-ttu-id="fc964-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fc964-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
