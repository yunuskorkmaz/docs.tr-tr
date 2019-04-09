---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 9af8d10c7db2d3bbe8b9443402cbb1cfeaa7edb3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091466"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme
Bu örnekte, içinde bir satıra stil ekleme işlemi gösterilmektedir bir <xref:System.Windows.Controls.ListView> uygulayan denetimi bir <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> modu.  
  
## <a name="example"></a>Örnek  
 Bir satıra stil uygulayabilirsiniz bir <xref:System.Windows.Controls.ListView> ayarlayarak denetimi bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> üzerinde <xref:System.Windows.Controls.ListView> denetimi. Olarak temsil edilen öğeleri stilini ayarlayın <xref:System.Windows.Controls.ListViewItem> nesneleri. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> satır içeriği görüntülemek için kullanılan nesneleri.  
  
 Aşağıdaki örnekler ayıklandığı, tam örnek depolanan şarkı bilgilerini koleksiyonunu görüntüler bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veritabanı. Veritabanındaki her bir şarkıyı Derecelendirme alanı vardır ve bu alanın değeri bir şarkıyı bilgi satırını görüntülemek nasıl belirtir.  
  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> için <xref:System.Windows.Controls.ListViewItem> şarkı koleksiyondaki şarkıya temsil eden nesneleri. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> nasıl görüntüleneceğini şarkı bilgilerini içeren bir satırın belirttiğiniz nesneleri.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.ControlTemplate> metin dizesi ekleyen `"Strongly Recommended"` satır. Bu şablon başvurulduğundan <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ve 5 (beş) değerini şarkıyı ait derecelendirme sahip olduğunda görüntüler. <xref:System.Windows.Controls.ControlTemplate> İçeren bir <xref:System.Windows.Controls.GridViewRowPresenter> sütunlardaki satır içeriğini tarafından tanımlandığı şekilde yerleştirir nesne <xref:System.Windows.Controls.GridView> görünüm modu.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [ListView Genel Bakışı](listview-overview.md)
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
