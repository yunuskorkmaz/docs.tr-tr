---
title: 'Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: ce79899d5c8e825ecb39e14ae8af4e0c33f13db3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733547"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme
Bu örnek, <xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A> modunu uygulayan <xref:System.Windows.Controls.ListView> denetimindeki bir satırın nasıl stilli olduğunu gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.ListView> denetiminde bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ayarlayarak <xref:System.Windows.Controls.ListView> denetimindeki bir satıra stil uygulayabilirsiniz. <xref:System.Windows.Controls.ListViewItem> nesne olarak temsil edilen öğelerinin stilini ayarlayın. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, satır içeriğini göstermek için kullanılan <xref:System.Windows.Controls.ControlTemplate> nesnelerine başvurur.  
  
 Aşağıdaki örneklerin ayıklandığı tüm örnek, bir XML veritabanında depolanan bir şarkı bilgileri koleksiyonunu görüntüler. Veritabanındaki her şarkının bir derecelendirme alanı vardır ve bu alanın değeri bir şarkı bilgileri satırının nasıl görüntüleneceğini belirtir.  
  
 Aşağıdaki örnek, Song koleksiyonundaki şarkıları temsil eden <xref:System.Windows.Controls.ListViewItem> nesneleri için <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> nasıl tanımlanacağını gösterir. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, şarkı bilgilerinin bir satırını görüntülemeyi belirten <xref:System.Windows.Controls.ControlTemplate> nesnelerine başvurur.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Aşağıdaki örnek, `"Strongly Recommended"` metin dizesini satıra ekleyen bir <xref:System.Windows.Controls.ControlTemplate> gösterir. Bu şablona <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> başvurulur ve şarkının derecelendirmesinin 5 (beş) değerine sahip olduğu zaman görüntülenir. <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.Controls.GridView> görünüm modu tarafından tanımlanan şekilde sütunlarda satır içeriğini oluşturan bir <xref:System.Windows.Controls.GridViewRowPresenter> nesnesi içerir.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 Aşağıdaki örnek <xref:System.Windows.Controls.GridView>tanımlar.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [ListView Genel Bakış](listview-overview.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
