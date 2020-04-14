---
title: 'Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243225"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>Nasıl yapilir: ListView için özel bir görünüm modu oluşturma

Bu örnek, denetim <xref:System.Windows.Controls.ListView.View%2A> <xref:System.Windows.Controls.ListView> için özel bir modun nasıl oluşturulurunu gösterir.  
  
## <a name="example"></a>Örnek  
 Denetim için <xref:System.Windows.Controls.ViewBase> özel bir görünüm oluştururken sınıfı kullanmanız gerekir. <xref:System.Windows.Controls.ListView> Aşağıdaki örnek, `PlainView` <xref:System.Windows.Controls.ViewBase> sınıftan türetilen bir görünüm modu gösterir.  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 Özel görünüme stil uygulamak için <xref:System.Windows.Style> sınıfı kullanın. Aşağıdaki örnekte <xref:System.Windows.Style> `PlainView` görünüm modu için bir tanımvardır. Önceki örnekte, bu stil için <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> `PlainView`tanımlanan özelliğin değeri olarak ayarlanır.  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 Özel görünüm modunda verilerin düzenini tanımlamak için <xref:System.Windows.DataTemplate> bir nesne tanımlayın. Aşağıdaki örnek, <xref:System.Windows.DataTemplate> `PlainView` görünüm modunda verileri görüntülemek için kullanılabilecek bir tanım tanımlar.  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 Aşağıdaki örnek, önceki örnekte `PlainView` tanımlananı kullanan <xref:System.Windows.DataTemplate> görünüm moduiçin bir <xref:System.Windows.ResourceKey> modelin nasıl tanımlanır gösteriş yapılacağını gösterir.  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <xref:System.Windows.Controls.ListView.View%2A> Özelliği <xref:System.Windows.Controls.ListView> kaynak anahtarına ayarlarsanız denetim özel bir görünüm kullanabilir. Aşağıdaki örnekte, bir `PlainView` <xref:System.Windows.Controls.ListView>. için görünüm modu olarak nasıl belirtilir gösterilmektedir.  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 Tam örnek için, [Birden Çok Görüntülemeli ListView (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) veya [Birden Çok Görüntülemeli ListView (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [ListView Genel Bakış](listview-overview.md)
- [GridView Genel Bakış](gridview-overview.md)
