---
ms.openlocfilehash: 19c613bf48479cb1e52531a4d6594db8ad89b8f3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774487"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>Sembol özellik WorkflowDesigner.Load kaldırmaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4. 5'iş akışı Tasarımcısı ve 3.5 yeniden barındırılan iş akışı ile yüklenirken hedeflenirken <xref:System.Activities.Presentation.WorkflowDesigner.Load> yöntemi, bir <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> kaydedilirken iş akışı oluşturulur.|
|Öneri|Bu hata yalnızca, geçici olarak ayarlayarak çalışılabilmesi için .NET Framework 4.5 iş akışı Tasarımcısı'nda hedeflenirken bildirimlerini <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> kullanarak sorunu 4.0 .NET Framework.Alternatively kalmayabilir <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> yük iş akışı için yöntemi yerine <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|
