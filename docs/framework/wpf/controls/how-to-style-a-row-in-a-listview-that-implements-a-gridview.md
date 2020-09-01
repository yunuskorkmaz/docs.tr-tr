---
title: 'Nasıl yapılır: GridView kullanan ListView içindeki bir satırı stil oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271951"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme
Bu örnek, mod kullanan bir denetimdeki bir satırın nasıl stilli <xref:System.Windows.Controls.ListView> olduğunu gösterir <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> .  
  
## <a name="example"></a>Örnek  
 Denetimde bir satırı ayarlayarak bir denetimin bir satırına stil uygulayabilirsiniz <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListView> . Nesne olarak temsil edilen öğelerinin stilini ayarlayın <xref:System.Windows.Controls.ListViewItem> . , <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> Satır içeriğini göstermek için kullanılan nesnelere başvurur.  
  
 Aşağıdaki örneklerin ayıklandığı tüm örnek, bir XML veritabanında depolanan bir şarkı bilgileri koleksiyonunu görüntüler. Veritabanındaki her şarkının bir derecelendirme alanı vardır ve bu alanın değeri bir şarkı bilgileri satırının nasıl görüntüleneceğini belirtir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListViewItem> Song koleksiyonundaki şarkıları temsil eden nesneler için nasıl tanımlanacağını gösterir. , <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> Şarkı bilgilerinin bir satırını görüntülemeyi belirten nesneler başvurur.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> metin dizesini satıra ekleyen bir gösterir `"Strongly Recommended"` . Bu şablona içinde başvurulur <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ve şarkının derecelendirmesi 5 (beş) olduğunda görüntülenir. , <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.GridViewRowPresenter> Görüntüleme modu tarafından tanımlanan şekilde sütunlarda satır içeriğini oluşturan bir nesne içerir <xref:System.Windows.Controls.GridView> .  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.GridView> .  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [ListView Genel Bakışı](listview-overview.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
