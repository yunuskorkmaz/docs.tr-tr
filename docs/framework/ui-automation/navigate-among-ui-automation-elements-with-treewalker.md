---
title: TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme
description: Treedenetçisi sınıfını kullanarak UI Otomasyon öğeleri arasında nasıl gezinmeyi gösteren bir kod örneği görürsünüz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168014"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , sınıfını kullanarak öğeler arasında gezinmeyi gösteren örnek kodu içerir <xref:System.Windows.Automation.TreeWalker> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker.GetParent%2A> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kök öğeyi veya masaüstünü bulana kadar ağacı ilerlemek için kullanır. Aşağıdaki öğesi, belirtilen öğenin ana penceresidir.  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> <xref:System.Windows.Forms.TreeView> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim görünümündeki ve etkin olan öğelerin tüm alt ağacını gösteren bir oluşturmak için ve kullanır.  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Öğelerini Alma](obtaining-ui-automation-elements.md)
