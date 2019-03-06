---
title: "Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma"
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: 0e1984241c07a69e2b350a61dc5873716c6fa5df
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375707"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a>Nasıl yapılır: Bir GridSplitter'ın Görünür Olduğundan Emin Olma
Bu örnek nasıl emin olunacağı gösterir bir <xref:System.Windows.Controls.GridSplitter> denetim, diğer denetimleri gizli bir <xref:System.Windows.Controls.Grid>.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.Panel.Children%2A> , Bir <xref:System.Windows.Controls.Grid> denetim işaretleme veya kod içinde tanımlanan sırada işlenir. <xref:System.Windows.Controls.GridSplitter> denetimler gizli göre diğer denetimler, bunları son öğeleri olarak tanımlamazsanız <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonu veya diğer verin, daha yüksek bir denetimleri <xref:System.Windows.Controls.Panel.ZIndexProperty>.  
  
 Önlemek için gizli <xref:System.Windows.Controls.GridSplitter> denetimleri, aşağıdakilerden birini yapın.  
  
-   Emin olun <xref:System.Windows.Controls.GridSplitter> denetimlerdir son <xref:System.Windows.Controls.Panel.Children%2A> eklenen <xref:System.Windows.Controls.Grid>. Aşağıdaki örnekte gösterildiği <xref:System.Windows.Controls.GridSplitter> içerisindeki son öğe olarak <xref:System.Windows.Controls.Panel.Children%2A> koleksiyonunu <xref:System.Windows.Controls.Grid>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   Ayarlama <xref:System.Windows.Controls.Panel.ZIndexProperty> üzerinde <xref:System.Windows.Controls.GridSplitter> Aksi halde gizleyecek bir denetimi yüksek olabilir. Aşağıdaki örnek verir <xref:System.Windows.Controls.GridSplitter> daha yüksek bir denetim <xref:System.Windows.Controls.Panel.ZIndexProperty> daha <xref:System.Windows.Controls.Button> denetimi.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   Aksi halde gizleyecek denetimde kenar boşluklarını ayarlama <xref:System.Windows.Controls.GridSplitter> böylece <xref:System.Windows.Controls.GridSplitter> sunulur. Aşağıdaki örnek, aksi takdirde kaplama bir denetim ve Gizle kenar boşlukları ayarlar <xref:System.Windows.Controls.GridSplitter>.  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](~/samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.GridSplitter>
- [Nasıl Yapılır Konuları](gridsplitter-how-to-topics.md)
