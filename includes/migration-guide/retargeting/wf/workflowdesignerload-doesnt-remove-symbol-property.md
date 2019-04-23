---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774487"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="b1902-101">Sembol özellik WorkflowDesigner.Load kaldırmaz</span><span class="sxs-lookup"><span data-stu-id="b1902-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b1902-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b1902-102">Details</span></span>|<span data-ttu-id="b1902-103">.NET Framework 4. 5'iş akışı Tasarımcısı ve 3.5 yeniden barındırılan iş akışı ile yüklenirken hedeflenirken <xref:System.Activities.Presentation.WorkflowDesigner.Load> yöntemi, bir <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> kaydedilirken iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b1902-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="b1902-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="b1902-104">Suggestion</span></span>|<span data-ttu-id="b1902-105">Bu hata yalnızca, geçici olarak ayarlayarak çalışılabilmesi için .NET Framework 4.5 iş akışı Tasarımcısı'nda hedeflenirken bildirimlerini <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> kullanarak sorunu 4.0 .NET Framework.Alternatively kalmayabilir <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> yük iş akışı için yöntemi yerine <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="b1902-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="b1902-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b1902-106">Scope</span></span>|<span data-ttu-id="b1902-107">Ana</span><span class="sxs-lookup"><span data-stu-id="b1902-107">Major</span></span>|
|<span data-ttu-id="b1902-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b1902-108">Version</span></span>|<span data-ttu-id="b1902-109">4,5</span><span class="sxs-lookup"><span data-stu-id="b1902-109">4.5</span></span>|
|<span data-ttu-id="b1902-110">Tür</span><span class="sxs-lookup"><span data-stu-id="b1902-110">Type</span></span>|<span data-ttu-id="b1902-111">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="b1902-111">Retargeting</span></span>|
|<span data-ttu-id="b1902-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b1902-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
