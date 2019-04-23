---
title: "Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: 1caa652c4a2a3a7d0a8d40fe703df7a3e8038c9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147101"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.DataTemplate> ve <xref:System.Windows.Style> nesnelerin görünümünü belirtmek için bir <xref:System.Windows.Controls.ListView> kullanan denetimi bir <xref:System.Windows.Controls.GridView> görünüm modu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde gösterildiği <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> için sütun başlığını özelleştirme nesneleri bir <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 Aşağıdaki örnek bu kullanmayı gösterir <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> ayarlamak için nesneleri <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> özelliklerini bir <xref:System.Windows.Controls.GridViewColumn>. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Sütun hücrelerin içeriğinin özelliği tanımlar.  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> Ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> yalnızca iki sütun üst bilgisi görünümünü özelleştirmek için kullanabileceğiniz çeşitli özelliklerin bir <xref:System.Windows.Controls.GridView> denetimi. Daha fazla bilgi için [GridView sütun üstbilgi stil ve şablonlarına genel bakış](gridview-column-header-styles-and-templates-overview.md).  
  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.DataTemplate> hücrelerin görünüşünü özelleştiren bir <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 Aşağıdaki örnek bunu kullanmayı gösterir <xref:System.Windows.DataTemplate> içeriğini tanımlamak için bir <xref:System.Windows.Controls.GridViewColumn> hücre. Bu şablon yerine kullanılan <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> önceki gösterilen özelliği <xref:System.Windows.Controls.GridViewColumn> örnek.  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [GridView Genel Bakış](gridview-overview.md)
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [ListView Genel Bakış](listview-overview.md)
