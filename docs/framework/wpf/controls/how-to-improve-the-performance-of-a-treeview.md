---
title: "Nasıl yapılır: TreeView'un Performansını Artırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: de1b46da2a7c6c3db0c0c19cdbb654fcf2fbbd6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153445"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>Nasıl yapılır: TreeView'un Performansını Artırma
Varsa bir <xref:System.Windows.Controls.TreeView> sayıda öğe içeriyorsa kullanıcı arabiriminde, yüklemek için gereken süreyi önemli gecikmeye neden olabilir. Yükleme süresi ayarlayarak iyileştirebilirsiniz `VirtualizingStackPanel.IsVirtualizing` özelliğine bağlı `true`.  Kullanıcı arabirimini de bir kullanıcı kaydırdığında tepki vermek yavaş olabilir <xref:System.Windows.Controls.TreeView> fare tekerleğini kullanarak veya bir kaydırma çubuğunun sürükleyerek. Performansını iyileştirebilir <xref:System.Windows.Controls.TreeView> kullanıcı ne zaman kaydırma ayarlayarak `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Örnek  
  
## <a name="description"></a>Açıklama  
Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.TreeView> ayarlayan `VirtualizingStackPanel.IsVirtualizing` özelliği true olarak eklenmiş ve `VirtualizingStackPanel.VirtualizationMode` özelliğine bağlı <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> performansı iyileştirmek için.  
  
## <a name="code"></a>Kod  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 Aşağıdaki örnek, önceki örnekte kullandığı verileri gösterir.  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetimler](../advanced/optimizing-performance-controls.md)
