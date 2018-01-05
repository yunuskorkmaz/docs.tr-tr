---
title: "Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e67777b5568214dff889088708db166efc6ae4dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma
Bu örnek özel bir oluşturulacağını gösterir <xref:System.Windows.Controls.ListView.View%2A> modu için bir <xref:System.Windows.Controls.ListView> denetim.  
  
## <a name="example"></a>Örnek  
 Kullanmalısınız <xref:System.Windows.Controls.ViewBase> sınıfı için özel bir görünüm oluşturduğunuzda <xref:System.Windows.Controls.ListView> denetim. Aşağıdaki örnek adı verilen bir görüntüleme modunu gösterir `PlainView`, türetilen <xref:System.Windows.Controls.ViewBase> sınıfı.  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Özel Görünüm için bir stil uygulamak için kullanmak <xref:System.Windows.Style> sınıfı. Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Style> için `PlainView` görüntüleme modu. Önceki örnekte bu stili değeri olarak ayarlanır <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> için tanımlı özellik `PlainView`.  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Özel Görünüm modunda veri düzenini tanımlamak için tanımlayan bir <xref:System.Windows.DataTemplate> nesnesi. Aşağıdaki örnek tanımlayan bir <xref:System.Windows.DataTemplate> verileri görüntülemek için kullanılabilir `PlainView` görüntüleme modu.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.ResourceKey> için `PlainView` kullanan görüntüleme modu <xref:System.Windows.DataTemplate> önceki örnekte tanımlanır.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 A <xref:System.Windows.Controls.ListView> denetimi, özel bir görünüm kullanabilir, ayarlarsanız <xref:System.Windows.Controls.ListView.View%2A> özelliği için kaynak anahtarı. Aşağıdaki örnekte nasıl belirtileceğini gösterir `PlainView` için görüntüleme modu olarak bir <xref:System.Windows.Controls.ListView>.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Tam bir örnek için bkz: [ListView birden çok görünümler örnek ile](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
