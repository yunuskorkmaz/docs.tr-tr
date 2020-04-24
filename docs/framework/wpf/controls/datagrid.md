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
ms.openlocfilehash: cdf4bfff8182b62d55f56b823c7ff129de4f9f1c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646126"
---
# <a name="datagrid"></a>DataGrid
Denetim, <xref:System.Windows.Controls.DataGrid> SQL veritabanı, LINQ sorgusu veya başka bir bağlanabilir veri kaynağı gibi birçok farklı kaynaktan gelen verileri görüntülemenizi ve görüntülemenizi sağlar. Daha fazla bilgi için [Bkz. Bağlayıcı Kaynaklara Genel Bakış.](../data/binding-sources-overview.md)  
  
 Sütunlar, resimler, düğmeler <xref:System.Windows.Controls.ComboBox>veya şablonda bulunan herhangi bir içerik gibi metin, denetimveya başka bir WPF içeriği gibi denetimleri görüntüleyebilir. Şablonda tanımlanan <xref:System.Windows.Controls.DataGridTemplateColumn> verileri görüntülemek için a kullanabilirsiniz. Aşağıdaki tablo, varsayılan olarak sağlanan sütun türlerini listeler.  
  
|Oluşturulan Sütun Türü|Veri Türü|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>hücre yazı tipi, renk ve boyut gibi görünüm olarak özelleştirilebilir. <xref:System.Windows.Controls.DataGrid>diğer WPF denetimlerinin tüm stil ve ayartıcı işlevselliğini destekler. <xref:System.Windows.Controls.DataGrid>düzenleme, sıralama ve doğrulama için varsayılan ve özelleştirilebilir davranışları da içerir.  
  
 Aşağıdaki tabloda, bunların nasıl <xref:System.Windows.Controls.DataGrid> gerçekleştirilebildiği ve gerçekleştirilebildiği ortak görevlerden bazıları listelenir. İlgili API'yi görüntüleyerek daha fazla bilgi ve örnek kod bulabilirsiniz.  
  
|Senaryo|Yaklaşım|  
|--------------|--------------|  
|Alternatif arka plan renkleri|Özelliği 2 veya daha fazlasına ayarlayın <xref:System.Windows.Media.Brush> ve <xref:System.Windows.Controls.DataGrid.RowBackground%2A> sonra <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> bir tanesini ve özelliklerine atayın. <xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A>|  
|Hücre ve satır seçimi davranışını tanımlama|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> Ve <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> özelliklerini ayarlayın.|  
|Üstbilginin, hücrelerin ve satırların görsel görünümünü özelleştirme|<xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>Yeni <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.CellStyle%2A> <xref:System.Windows.Controls.DataGrid.RowStyle%2A> bir uygulama , , veya özellikleri. <xref:System.Windows.Style>|  
|Boyutlandırma seçeneklerini ayarlama|, <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A> <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A> veya özelliklerini ayarlayın. Daha fazla bilgi için [DataGrid Denetimi'ndeki Boyutlandırma Seçenekleri'ne](sizing-options-in-the-datagrid-control.md)bakın.|  
|Seçili öğelere erişin|Seçili <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> hücreleri ve seçili <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> satırları almak için özelliği almak için özelliği denetleyin. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Son kullanıcı etkileşimlerini özelleştirme|, <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> ve özelliklerini ayarlayın.|  
|Otomatik oluşturulan sütunları iptal etme veya değiştirme|<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> Olayı ele alın.|  
|Sütunu dondurma|<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> Özelliği 1 olarak ayarlayın ve özelliği 0 olarak ayarlayarak <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> sütunu en sol konuma taşıyın.|  
|XML verilerini veri kaynağı olarak kullanma|Öğelerin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> toplanmasını <xref:System.Windows.Controls.DataGrid> temsil eden XPath sorgusuna bağlanın. Her sütunu <xref:System.Windows.Controls.DataGrid>' da oluşturun. Öğe kaynağındaki özelliği alan sorguya bağlama da XPath'i ayarlayarak her sütunu bağlayın. Örnek için bkz. <xref:System.Windows.Controls.DataGridTextColumn>|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Yeni bir WPF projesinin nasıl ayarlanır, Varlık Çerçeve Öğesi ekleme, kaynağı <xref:System.Windows.Controls.DataGrid>ayarlama ve verileri bir ' de görüntüleme|  
|[Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme](how-to-add-row-details-to-a-datagrid-control.md)|Bir <xref:System.Windows.Controls.DataGrid>.|  
|[Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama](how-to-implement-validation-with-the-datagrid-control.md)|Hücrelerde ve satırlarda <xref:System.Windows.Controls.DataGrid> değerlerin nasıl doğrulaşdırılabildiğini ve doğrulama geri bildirimini nasıl görüntüleyeceklerini açıklar.|  
|[DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Klavye ve fareyi <xref:System.Windows.Controls.DataGrid> kullanarak denetimle nasıl etkileşimde ne yapılacağını açıklar.|  
|[Nasıl yapılır: DataGrid Denetiminde Verileri Gruplandırma, Sıralama ve Filtreleme](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Verileri gruplandırma, sıralama <xref:System.Windows.Controls.DataGrid> ve filtreleme ile verileri farklı şekillerde görüntülemeyi açıklar.|  
|[DataGrid Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-datagrid-control.md)|Mutlak ve otomatik boyutlandırmanın nasıl <xref:System.Windows.Controls.DataGrid>denetlenebildiğini açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Denetimler](index.md)
- [WPF İçerik Modeli](wpf-content-model.md)
