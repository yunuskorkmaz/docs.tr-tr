---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804672"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load sembol özelliğini kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|İş akışı tasarımcısında .NET Framework 4.5 hedeflenirken ve <xref:System.Activities.Presentation.WorkflowDesigner.Load> yöntemle yeniden barındırılan 3,5 iş akışı yüklenirken, iş akışı tasarruf edilirken bir <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> adım atılır.|
|Öneri|Bu hata yalnızca iş akışı tasarımcısında .NET Framework 4.5'i hedefalırken ortaya <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> çıkar, bu nedenle 4.0 .NET Framework.Alternatively'e <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> ayarlayarak iş akışı yerine <xref:System.Activities.Presentation.WorkflowDesigner.Load>.'yi yüklemek için yöntem kullanılarak sorun önlenebilir.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
