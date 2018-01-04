---
title: "Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b7587a093b2b43856a05693bb785a0465211782
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma
Bu örnek emin olmak nasıl gösterir bir <xref:System.Windows.Controls.GridSplitter> denetim, diğer denetimlerinde gizli bir <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Panel.Children%2A> , Bir <xref:System.Windows.Controls.Grid> denetim işaretleme veya kod tanımlanan sırada işlenir. <xref:System.Windows.Controls.GridSplitter>denetimler gizli diğer denetimler tarafından bunları son öğeleri olarak tanımlamıyorsa <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu veya diğer verin, daha yüksek denetimleri <xref:System.Windows.Controls.Panel.ZIndexProperty>.  
  
 Önlemek için gizli <xref:System.Windows.Controls.GridSplitter> denetimleri, aşağıdakilerden birini yapın.  
  
-   Olduğundan emin olun <xref:System.Windows.Controls.GridSplitter> denetimleridir son <xref:System.Windows.Controls.Panel.Children%2A> eklenen <xref:System.Windows.Controls.Grid>. Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.GridSplitter> son öğesi olarak <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   Ayarlama <xref:System.Windows.Controls.Panel.ZIndexProperty> üzerinde <xref:System.Windows.Controls.GridSplitter> , aksi takdirde Gizle denetimden daha yüksek olmalıdır. Aşağıdaki örnek verir <xref:System.Windows.Controls.GridSplitter> daha yüksek denetim <xref:System.Windows.Controls.Panel.ZIndexProperty> daha <xref:System.Windows.Controls.Button> denetim.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   Aksi takdirde Gizle denetiminde kenar boşluklarını ayarlama <xref:System.Windows.Controls.GridSplitter> böylece <xref:System.Windows.Controls.GridSplitter> sunulur. Aşağıdaki örnek, aksi takdirde kaplama bir denetim ve Gizle kenar boşluklarını ayarlar <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.GridSplitter>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
