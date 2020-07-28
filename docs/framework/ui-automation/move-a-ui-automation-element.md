---
title: UI Otomasyon Öğesini Taşıma
description: UI Otomasyonu öğesinin belirtilen ekran konumuna nasıl taşınacağını gösteren örnek koda bakın. Windowdeseni ve TransformPattern Denetim desenlerini kullanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
ms.openlocfilehash: 4c8bec4e6d7a241588a3ab261cb80ce9ac242024
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166145"
---
# <a name="move-a-ui-automation-element"></a>UI Otomasyon Öğesini Taşıma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu örnek, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğenin belirtilen ekran konumuna nasıl taşınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Automation.WindowPattern> <xref:System.Windows.Automation.TransformPattern> bir Win32 hedef uygulamasını programlama yoluyla ayrık ekran konumlarına taşımak ve izlemek için ve denetim desenlerini kullanır <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent> .  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windowmodel örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
