---
title: GridView Sütun Üstbilgi Stil ve Şablonlarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
ms.openlocfilehash: 83643d8acea706bad439683702e4228d240b97bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090328"
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>GridView Sütun Üstbilgi Stil ve Şablonlarına Genel Bakış
Bu genel bakışta bir sütun başlığını özelleştirmek için kullandığınız özellikler için öncelik sırasını anlatır <xref:System.Windows.Controls.GridView> görünüm modu bir <xref:System.Windows.Controls.ListView> denetimi.  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>GridView sütun başlığı özelleştirme  
 İçerik, Düzen ve bir sütun başlığına stilini tanımlayan özellikleri bir <xref:System.Windows.Controls.GridView> üzerinde birçok ilgili sınıflar bulunur. Bu özelliklerden bazıları benzer işlevselliği veya aynı sahiptir.  
  
 Aşağıdaki tablodaki satırları aynı işlevi gerçekleştirir özellik gruplarını gösterir. Bu özellikler sütun başlıklarının özelleştirmek için kullanabileceğiniz bir <xref:System.Windows.Controls.GridView>. İlgili özellikler için öncelik sağdan sola özelliği görselinin sağ sütundaki en yüksek önceliğe sahip olduğu sırasıdır. Örneğin, bir <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ayarlanır <xref:System.Windows.Controls.GridViewColumnHeader> nesne ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> ilişkili ayarlanmışsa <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> önceliklidir. Bu senaryoda, <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> hiçbir etkisi olmaz.  
  
 **GridView sütun başlıklarını için ilgili özellikleri**  
  
|||||  
|-|-|-|-|  
|**Sınıflar**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**Bağlam Menüsü Özellikleri**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|Geçerli değil|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**Araç İpucu**<br /><br /> **Özellikler**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|Geçerli değil|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**Üstbilgi şablonu**<br /><br /> **Özellikler**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**Stil özellikleri**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>için **üstbilgi şablonu özellikleri**ayarlamanız, şablon ve şablon seçiciyi özellikleri, şablon özelliği önceliğe. Örneğin, her ikisi de ayarlarsanız <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> özellikleri <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği önceliklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır Konuları](listview-how-to-topics.md)
- [ListView Genel Bakış](listview-overview.md)
- [GridView Genel Bakış](gridview-overview.md)
