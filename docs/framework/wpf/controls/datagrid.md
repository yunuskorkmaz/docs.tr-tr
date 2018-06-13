---
title: DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: a8f267706c1ace02b091329360779711981d01e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557088"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid> Denetimi görüntülemek ve bir SQL veritabanı, LINQ sorgusu veya diğer bir bağlanabilir veri kaynağından gibi birçok farklı kaynaklardan gelen verileri düzenlemenize olanak sağlar. Daha fazla bilgi için bkz: [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Sütunları görüntüleyebilirsiniz metin denetimleri gibi bir <xref:System.Windows.Controls.ComboBox>, veya herhangi diğer WPF içeriği, görüntüleri, düğmeleri ya da şablonda yer alan herhangi bir içerik. Kullanabileceğiniz bir <xref:System.Windows.Controls.DataGridTemplateColumn> bir şablonda tanımlanan verileri görüntülemek için. Aşağıdaki tabloda, varsayılan olarak sağlanan sütun türleri listelenmektedir.  
  
|Oluşturulan sütun türü|Veri Türü|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> hücre yazı tipi, renk ve boyutu gibi görünümü özelleştirilebilir. <xref:System.Windows.Controls.DataGrid> diğer WPF denetimlerinin tüm stil ve şablon işlevlerini destekler. <xref:System.Windows.Controls.DataGrid> Ayrıca varsayılan ve düzenleme, sıralama ve doğrulama için özelleştirilebilir davranışları içerir.  
  
 Aşağıdaki tabloda bazı için ortak görevleri listeler <xref:System.Windows.Controls.DataGrid> ve bunların nasıl yapılacağını. İlgili API'ye görüntüleyerek, daha fazla bilgi ve örnek kod bulabilirsiniz.  
  
|Senaryo|Yaklaşım|  
|--------------|--------------|  
|Arka plan renklerini değiştirme|Ayarlama <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> 2 veya daha fazla özelliğe ve atayın bir <xref:System.Windows.Media.Brush> için <xref:System.Windows.Controls.DataGrid.RowBackground%2A> ve <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> özellikleri.|  
|Hücre ve satır seçimi davranışını tanımlayın|Ayarlama <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ve <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> özellikleri.|  
|Üstbilgiler, hücre ve satırları görsel görünümünü özelleştirme|Yeni bir uygulama <xref:System.Windows.Style> için <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, veya <xref:System.Windows.Controls.DataGrid.RowStyle%2A> özellikleri.|  
|Boyutlandırma seçenekleri ayarlama|Ayarlama <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, veya <xref:System.Windows.FrameworkElement.MinWidth%2A> özellikleri. Daha fazla bilgi için bkz: [boyutlandırma seçenekleri DataGrid denetiminde](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md).|  
|Seçili öğelere erişim|Denetleme <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> seçili hücreleri almak için özellik ve <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> seçili satırları alınacağı özellik. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Son kullanıcı etkileşimleri özelleştirme|Ayarlama <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, ve <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> özellikleri.|  
|İptal etme veya otomatik oluşturulan sütunları değiştirme|Tanıtıcı <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> olay.|  
|Sütun dondurma|Ayarlama <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> özelliğini 1 ve ayarlayarak taşıma sütun en solundaki konuma <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> özelliğinin 0.|  
|XML verileri veri kaynağı olarak kullanın|Bağlama <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> üzerinde <xref:System.Windows.Controls.DataGrid> XPath sorguya öğeler koleksiyonunu temsil eder. Her sütunda oluşturma <xref:System.Windows.Controls.DataGrid>. Her sütun bağlama öğesi kaynağında özelliği alır sorguya üzerinde XPath ayarlayarak bağlayın. Örnek için bkz. <xref:System.Windows.Controls.DataGridTextColumn>|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Kümesine yeni bir WPF projesi, bir varlık çerçevesi öğesi ekleyin, kaynağı ve verileri görüntülemek açıklar bir <xref:System.Windows.Controls.DataGrid>.|  
|[Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|Satır ayrıntılarını oluşturmayı açıklar bir <xref:System.Windows.Controls.DataGrid>.|  
|[Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|Değerleri doğrulamak açıklar <xref:System.Windows.Controls.DataGrid> hücre ve satırları ve görüntü doğrulaması geri bildirim.|  
|[DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Etkileşim açıklar <xref:System.Windows.Controls.DataGrid> klavye ve fare kullanarak denetim.|  
|[Nasıl yapılır: DataGrid Denetiminde Verileri Gruplandırma, Sıralama ve Filtreleme](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Verileri görüntülemeyi açıklar bir <xref:System.Windows.Controls.DataGrid> gruplandırma, sıralama ve verileri filtreleme, farklı şekillerde.|  
|[DataGrid Denetimindeki Boyutlandırma Seçenekleri](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|Mutlak ve otomatik boyutlandırma denetlemek açıklar <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DataGrid>  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [Denetimler](../../../../docs/framework/wpf/controls/index.md)  
 [WPF İçerik Modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md)
