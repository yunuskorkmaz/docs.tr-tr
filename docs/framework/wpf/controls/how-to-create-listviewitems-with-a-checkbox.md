---
title: 'Nasıl yapılır: CheckBox ile ListViewItems Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: b09d5ad11b0961febf524cec1e19cb1e59832e44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083113"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>Nasıl yapılır: CheckBox ile ListViewItems Oluşturma
Bu örnek, bir sütunun görüntülenecek gösterilmektedir <xref:System.Windows.Controls.CheckBox> denetimlerini bir <xref:System.Windows.Controls.ListView> kullanan denetimi bir <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Örnek  
 İçeren bir sütun oluşturmak için <xref:System.Windows.Controls.CheckBox> denetimlerini bir <xref:System.Windows.Controls.ListView>, oluşturun bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.CheckBox>. Ardından <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> , bir <xref:System.Windows.Controls.GridViewColumn> için <xref:System.Windows.DataTemplate>.  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.DataTemplate> içeren bir <xref:System.Windows.Controls.CheckBox>. Örnek bağlar <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> özelliği <xref:System.Windows.Controls.CheckBox> için <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> özelliği değerinin <xref:System.Windows.Controls.ListViewItem> , içerir. Bu nedenle, <xref:System.Windows.Controls.ListViewItem> içeren <xref:System.Windows.Controls.CheckBox> seçildiğinde <xref:System.Windows.Controls.CheckBox> denetlenir.  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 Aşağıdaki örnek, bir sütun oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.CheckBox> kontrol eder. Sütunu, örnek yapmak için <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> özelliği <xref:System.Windows.Controls.GridViewColumn> için <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView Genel Bakış](listview-overview.md)
- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [GridView Genel Bakış](gridview-overview.md)
