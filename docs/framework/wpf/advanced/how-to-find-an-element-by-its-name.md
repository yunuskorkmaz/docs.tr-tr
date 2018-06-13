---
title: 'Nasıl yapılır: Öğeyi Adına Göre Bulma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: e2d176c9334c0a1d4c10819e0dc9f2c408e41d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543582"
---
# <a name="how-to-find-an-element-by-its-name"></a>Nasıl yapılır: Öğeyi Adına Göre Bulma
Bu örnek nasıl kullanılacağını açıklar <xref:System.Windows.FrameworkElement.FindName%2A> yöntemi kullanarak bir öğe bulmak için kendi <xref:System.Windows.FrameworkElement.Name%2A> değeri.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, belirli bir öğeyle adını kullanarak bulunacak yöntemin bir düğmesi olay işleyicisi olarak yazılır. `stackPanel` olan <xref:System.Windows.FrameworkElement.Name%2A> kök <xref:System.Windows.FrameworkElement> Aranmakta, ve örnek yöntemi sonra görsel olarak bulunan öğe olarak atama gösterir <xref:System.Windows.Controls.TextBlock> ve aşağıdakilerden birini değiştirme <xref:System.Windows.Controls.TextBlock> görünür [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] özellikleri.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
