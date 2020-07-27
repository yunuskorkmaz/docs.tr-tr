---
title: DataGrid
description: DataGrid denetiminin bir veritabanı, LINQ sorgusu veya başka bir bağlanabilir veri kaynağı gibi farklı kaynaklardan verileri görüntülemenize ve düzenlemenize nasıl olanak sağladığını öğrenin.
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
ms.openlocfilehash: 3db49c12fcb363ef7f99e5c69beae09ab05addcf
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168315"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>Denetim, BIR SQL veritabanı, LINQ sorgusu veya başka bir bağlanabilir veri kaynağı gibi birçok farklı kaynaktan veri görüntülemenizi ve düzenlemenizi sağlar. Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](../data/binding-sources-overview.md).  
  
 Sütunlar metin, denetimler gibi, gibi <xref:System.Windows.Controls.ComboBox> DIĞER WPF içerikleri veya bir şablonda yer alan herhangi bir içerik gibi resimleri görüntüleyebilir. Bir <xref:System.Windows.Controls.DataGridTemplateColumn> şablonda tanımlanan verileri göstermek için kullanabilirsiniz. Aşağıdaki tabloda varsayılan olarak sağlanmış olan sütun türleri listelenmektedir.  
  
|Oluşturulan sütun türü|Veri Türü|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>görünümde, hücre yazı tipi, renk ve boyut gibi özelleştirilebilir. <xref:System.Windows.Controls.DataGrid>diğer WPF denetimlerinin tüm stil ve şablon oluşturma işlevlerini destekler. <xref:System.Windows.Controls.DataGrid>Ayrıca, düzenlenecek, sıralamaya ve doğrulamaya yönelik varsayılan ve özelleştirilebilir davranışları içerir.  
  
 Aşağıdaki tabloda, için genel görevlerden bazıları <xref:System.Windows.Controls.DataGrid> ve bunların nasıl yapılacağı listelenmektedir. İlgili API 'yi görüntüleyerek daha fazla bilgi ve örnek kod bulabilirsiniz.  
  
|Senaryo|Yaklaşım|  
|--------------|--------------|  
|Alternatif arka plan renkleri|<xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A>Özelliği 2 veya daha fazla olarak ayarlayın ve ardından <xref:System.Windows.Media.Brush> <xref:System.Windows.Controls.DataGrid.RowBackground%2A> ve <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> özelliklerine atayın.|  
|Hücre ve satır seçimi davranışını tanımlama|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>Ve özelliklerini ayarlayın <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> .|  
|Üst bilgilerin, hücrelerin ve satırların görsel görünümünü özelleştirme|<xref:System.Windows.Style> <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A> ,, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A> <xref:System.Windows.Controls.DataGrid.CellStyle%2A> Veya <xref:System.Windows.Controls.DataGrid.RowStyle%2A> özelliklerine yeni bir uygulama uygulayın.|  
|Boyutlandırma seçeneklerini ayarla|,,,, <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> Veya özelliklerini ayarlayın <xref:System.Windows.FrameworkElement.MinWidth%2A> . Daha fazla bilgi için bkz. [DataGrid denetimindeki boyutlandırma seçenekleri](sizing-options-in-the-datagrid-control.md).|  
|Seçili öğelere erişin|Seçili <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> satırları almak için seçili hücreleri ve özelliği almak için özelliği denetleyin <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> . Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Son kullanıcı etkileşimlerini özelleştirme|,,,, <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> Ve özelliklerini ayarlayın <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> .|  
|Otomatik olarak oluşturulan sütunları iptal edin veya değiştirin|Olayı işleyin <xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> .|  
|Bir sütunu dondurma|<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A>Özelliğini 1 olarak ayarlayın ve özelliğini 0 olarak ayarlayarak sütunu en soldaki konuma taşıyın <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> .|  
|Veri kaynağı olarak XML verileri kullanma|<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>Üzerinde <xref:System.Windows.Controls.DataGrid> öğesini öğe koleksiyonunu temsil eden XPath sorgusuna bağlayın. İçindeki her bir sütunu oluşturun <xref:System.Windows.Controls.DataGrid> . Bağlama üzerindeki XPath öğesini öğe kaynağındaki özelliği alan sorguya ayarlayarak her bir sütunu bağlayın. Örnek için bkz. <xref:System.Windows.Controls.DataGridTextColumn>|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Yeni bir WPF projesi ayarlamayı, Entity Framework bir öğe eklemeyi, kaynağı ayarlamayı ve verileri bir içinde görüntülemeyi açıklar <xref:System.Windows.Controls.DataGrid> .|  
|[Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme](how-to-add-row-details-to-a-datagrid-control.md)|Bir için satır ayrıntılarının nasıl oluşturulacağını açıklar <xref:System.Windows.Controls.DataGrid> .|  
|[Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama](how-to-implement-validation-with-the-datagrid-control.md)|Hücrelerde ve satırlarda değerlerin nasıl doğrulanacağını <xref:System.Windows.Controls.DataGrid> ve doğrulama geri bildirimini görüntülemeyi açıklar.|  
|[DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid>Klavye ve fareyi kullanarak denetimle nasıl etkileşim kuracağınızı açıklar.|  
|[Nasıl yapılır: DataGrid Denetiminde Verileri Gruplandırma, Sıralama ve Filtreleme](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid>Verileri gruplandırarak, sıralayarak ve filtreleyerek verileri farklı şekillerde görüntülemeyi açıklar.|  
|[DataGrid Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-datagrid-control.md)|İçinde mutlak ve otomatik boyutlandırmanın nasıl kontrol edileceğini açıklar <xref:System.Windows.Controls.DataGrid> .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Denetimler](index.md)
- [WPF İçerik Modeli](wpf-content-model.md)
