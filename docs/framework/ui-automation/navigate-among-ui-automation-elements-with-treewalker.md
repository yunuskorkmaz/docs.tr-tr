---
title: TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme
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
ms.openlocfilehash: aed8c624a75364dcc97c73ae7ebd6331275ceff4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182877"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda gezinme gösteren örnek kodu içeren [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanarak öğeleri <xref:System.Windows.Automation.TreeWalker> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Automation.TreeWalker.GetParent%2A> gitmeye [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kök öğe veya Masaüstü bulana kadar ağaç. Yalnızca aşağıda belirtilen öğenin üst pencere öğesidir.  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> ve <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> oluşturmak için bir <xref:System.Windows.Forms.TreeView> tamamını bir alt ağacı gösteren [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , etkin ve denetim görünümünde olan öğeler.  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Öğelerini Alma](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
