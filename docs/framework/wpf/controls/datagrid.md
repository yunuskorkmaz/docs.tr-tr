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
ms.openlocfilehash: 7eb5c4719a18a288ca0ee3acb13c8c2498ab30f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676087"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid> Denetimi görüntülemek ve bir SQL veritabanı, LINQ sorgusu ya da başka bir bağlanabilir veri kaynağı gibi birçok farklı kaynaklardan gelen verileri düzenlemenize olanak sağlar. Daha fazla bilgi için [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Sütunları görüntüleyebilir metin denetimleri gibi bir <xref:System.Windows.Controls.ComboBox>, ya da tüm WPF gibi diğer içeriklere görüntüleri, düğmeler ve şablonda yer alan herhangi bir içerik. Kullanabileceğiniz bir <xref:System.Windows.Controls.DataGridTemplateColumn> şablonda tanımlanan verileri görüntülemek için. Aşağıdaki tabloda, varsayılan sütun türleri listelenmektedir.  
  
|Oluşturulan sütun türü|Veri Türü|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> Görünüm hücresi yazı tipi rengi ve boyutu gibi özelleştirilebilir. <xref:System.Windows.Controls.DataGrid> diğer WPF denetimlerinin tüm stil ve şablon işlevlerini destekler. <xref:System.Windows.Controls.DataGrid> Ayrıca, varsayılan ve düzenleme, sıralama ve doğrulama için özelleştirilebilir davranışlar içerir.  
  
 Aşağıdaki tablo bazı yaygın görevleri için listeler <xref:System.Windows.Controls.DataGrid> ve bunların nasıl yapılacağını. İlgili API görüntüleyerek daha fazla bilgi ve örnek kodu bulabilirsiniz.  
  
|Senaryo|Yaklaşım|  
|--------------|--------------|  
|Arka plan rengini değiştirme|Ayarlama <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> 2 veya daha fazla özelliğine atayın bir <xref:System.Windows.Media.Brush> için <xref:System.Windows.Controls.DataGrid.RowBackground%2A> ve <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> özellikleri.|  
|Hücre ve satır seçimi davranışını tanımlayın|Ayarlama <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ve <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> özellikleri.|  
|Üst bilgiler, hücre ve satırları görsel görünümünü özelleştirme|Yeni bir uygulama <xref:System.Windows.Style> için <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>, veya <xref:System.Windows.Controls.DataGrid.RowStyle%2A> özellikleri.|  
|Boyutlandırma seçenekleri ayarlama|Ayarlama <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, veya <xref:System.Windows.FrameworkElement.MinWidth%2A> özellikleri. Daha fazla bilgi için [DataGrid denetimindeki boyutlandırma seçenekleri](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md).|  
|Seçili öğelere erişim|Denetleme <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> seçili hücreleri almak için özellik ve <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> seçili satırları alınacağı özellik. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Son kullanıcı etkileşimlerini özelleştirin|Ayarlama <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, ve <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> özellikleri.|  
|İptal etme veya otomatik oluşturulan sütunları değiştirme|Tanıtıcı <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> olay.|  
|Bir sütunu Dondur|Ayarlama <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> özelliğini 1 ve ayarlayarak taşıma sütun en soldaki konumuna <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> özelliğinin 0.|  
|Veri kaynağı olarak XML verileri kullanma|Bağlama <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> üzerinde <xref:System.Windows.Controls.DataGrid> XPath Sorgulanacak öğeleri koleksiyonunu temsil eder. Her bir sütun oluşturun <xref:System.Windows.Controls.DataGrid>. Her sütun bağlama öğesi kaynak özelliği alır bir sorguya üzerinde XPath ayarlayarak bağlayın. Örnek için bkz. <xref:System.Windows.Controls.DataGridTextColumn>|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: DataGrid denetimindeki SQL Server veritabanından veri görüntüleme](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Açıklar ayarlanmış yeni bir WPF projesi, bir varlık çerçevesi öğesi ekleme, kaynağı ve verileri görüntülemek bir <xref:System.Windows.Controls.DataGrid>.|  
|[Nasıl yapılır: DataGrid denetimine satır ayrıntıları ekleme](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|Satır ayrıntıları için oluşturmayı açıklar bir <xref:System.Windows.Controls.DataGrid>.|  
|[Nasıl yapılır: DataGrid denetimi ile doğrulama uygulama](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|Değerleri doğrulamak açıklar <xref:System.Windows.Controls.DataGrid> hücre ve satırları ve görüntü doğrulama geri bildirim.|  
|[DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Etkileşim açıklar <xref:System.Windows.Controls.DataGrid> klavyeyi ve fareyi kullanarak denetimi.|  
|[Nasıl yapılır: DataGrid denetiminde filtre verileri gruplandırma, sıralama ve](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Verileri görüntülemeyi açıklar bir <xref:System.Windows.Controls.DataGrid> gruplandırma, sıralama ve filtreleme verileri tarafından farklı şekillerde.|  
|[DataGrid Denetimindeki Boyutlandırma Seçenekleri](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|İçinde mutlak ve otomatik boyutlandırma denetlemek nasıl açıklar <xref:System.Windows.Controls.DataGrid>.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.DataGrid>
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [Denetimler](../../../../docs/framework/wpf/controls/index.md)
- [WPF İçerik Modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md)
