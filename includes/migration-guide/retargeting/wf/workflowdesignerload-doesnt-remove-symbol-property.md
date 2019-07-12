---
ms.openlocfilehash: 97a92c6bce80b93e9a8bdd863bf881631eaffb27
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804672"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="88db5-101">Sembol özellik WorkflowDesigner.Load kaldırmaz</span><span class="sxs-lookup"><span data-stu-id="88db5-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

|   |   |
|---|---|
|<span data-ttu-id="88db5-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="88db5-102">Details</span></span>|<span data-ttu-id="88db5-103">.NET Framework 4. 5'iş akışı Tasarımcısı ve 3.5 yeniden barındırılan iş akışı ile yüklenirken hedeflenirken <xref:System.Activities.Presentation.WorkflowDesigner.Load> yöntemi, bir <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> kaydedilirken iş akışı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="88db5-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> is thrown while saving the workflow.</span></span>|
|<span data-ttu-id="88db5-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="88db5-104">Suggestion</span></span>|<span data-ttu-id="88db5-105">Bu hata yalnızca, geçici olarak ayarlayarak çalışılabilmesi için .NET Framework 4.5 iş akışı Tasarımcısı'nda hedeflenirken bildirimlerini <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> kullanarak sorunu 4.0 .NET Framework.Alternatively kalmayabilir <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> yük iş akışı için yöntemi yerine <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span><span class="sxs-lookup"><span data-stu-id="88db5-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>|
|<span data-ttu-id="88db5-106">Kapsam</span><span class="sxs-lookup"><span data-stu-id="88db5-106">Scope</span></span>|<span data-ttu-id="88db5-107">Ana</span><span class="sxs-lookup"><span data-stu-id="88db5-107">Major</span></span>|
|<span data-ttu-id="88db5-108">Sürüm</span><span class="sxs-lookup"><span data-stu-id="88db5-108">Version</span></span>|<span data-ttu-id="88db5-109">4,5</span><span class="sxs-lookup"><span data-stu-id="88db5-109">4.5</span></span>|
|<span data-ttu-id="88db5-110">Tür</span><span class="sxs-lookup"><span data-stu-id="88db5-110">Type</span></span>|<span data-ttu-id="88db5-111">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="88db5-111">Retargeting</span></span>|
|<span data-ttu-id="88db5-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="88db5-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

