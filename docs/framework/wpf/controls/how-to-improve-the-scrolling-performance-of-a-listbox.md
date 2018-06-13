---
title: "Nasıl yapılır: ListBox'ın Kayma Performansını Artırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: 224b996ad97d9a71ce43023143b68c2ab5b8467b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552798"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>Nasıl yapılır: ListBox'ın Kayma Performansını Artırma
Varsa bir <xref:System.Windows.Controls.ListBox> sayıda öğe içeren bir kullanıcı kaydırdığında kullanıcı arabirimi yanıt yavaş olabilir <xref:System.Windows.Controls.ListBox> fare tekerleği kullanarak veya bir kaydırma çubuğu sürükleyerek. Performansını artırabilir <xref:System.Windows.Controls.ListBox> kullanıcı ne zaman kayar ayarlayarak `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
Aşağıdaki örnekte bir <xref:System.Windows.Controls.ListBox> ve ayarlar `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> kaydırma sırasında performansı artırmak için.  
  
## <a name="code"></a>Kod  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 Aşağıdaki örnek, önceki örnekte kullandığı verileri gösterir.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
