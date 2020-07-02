---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616085"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner. Load, sembol özelliğini kaldırmaz

#### <a name="details"></a>Ayrıntılar

İş akışı tasarımcısında .NET Framework 4,5 ' i hedeflerken ve yöntemi ile yeniden barındırılan bir 3,5 iş akışını yüklerken, <xref:System.Activities.Presentation.WorkflowDesigner.Load> <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> iş akışı kaydedilirken bir oluşturulur.

#### <a name="suggestion"></a>Öneri

Bu hata yalnızca iş akışı tasarımcısında .NET Framework 4,5 ' i hedeflerken bildirimler. bu nedenle, ' ı 4,0 .NET Framework ayarlanarak geçici olarak gerçekleştirilebilir `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` . alternatif olarak, <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> bunun yerine iş akışını yüklemek için yöntemi kullanılarak sorun önlenebilir <xref:System.Activities.Presentation.WorkflowDesigner.Load> .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
