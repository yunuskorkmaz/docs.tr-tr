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
ms.openlocfilehash: f0887f36990de483139a9fde1472a78737cb7b72
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460377"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid> denetimi bir SQL veritabanı, LINQ sorgusu veya başka bir bağlanabilir veri kaynağı gibi birçok farklı kaynaktan veri görüntülemenizi ve düzenlemenizi sağlar. Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](../data/binding-sources-overview.md).  
  
 Sütunlar, <xref:System.Windows.Controls.ComboBox>gibi bir metin, denetim veya görüntü, düğme ya da bir şablonda bulunan herhangi bir içerik gibi başka bir WPF içeriği görüntüleyebilir. Bir şablonda tanımlanan verileri göstermek için bir <xref:System.Windows.Controls.DataGridTemplateColumn> kullanabilirsiniz. Aşağıdaki tabloda varsayılan olarak sağlanmış olan sütun türleri listelenmektedir.  
  
|Oluşturulan sütun türü|Veri Türü|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid>, görünümde, hücre yazı tipi, renk ve boyut gibi özelleştirilebilir. <xref:System.Windows.Controls.DataGrid>, diğer WPF denetimlerinin tüm stil ve şablon oluşturma işlevlerini destekler. <xref:System.Windows.Controls.DataGrid>, düzenlemenin, sıralamaya ve doğrulamaya yönelik varsayılan ve özelleştirilebilir davranışları da içerir.  
  
 Aşağıdaki tabloda <xref:System.Windows.Controls.DataGrid> ortak görevlerinin bazıları ve bunların nasıl yapılacağı listelenmektedir. İlgili API 'yi görüntüleyerek daha fazla bilgi ve örnek kod bulabilirsiniz.  
  
|Senaryo|Uygulanabilecek|  
|--------------|--------------|  
|Alternatif arka plan renkleri|<xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> özelliğini 2 veya daha fazla olarak ayarlayın ve ardından <xref:System.Windows.Controls.DataGrid.RowBackground%2A> ve <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> özelliklerine bir <xref:System.Windows.Media.Brush> atayın.|  
|Hücre ve satır seçimi davranışını tanımlama|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> ve <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> özelliklerini ayarlayın.|  
|Üst bilgilerin, hücrelerin ve satırların görsel görünümünü özelleştirme|<xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>, <xref:System.Windows.Controls.DataGrid.CellStyle%2A>veya <xref:System.Windows.Controls.DataGrid.RowStyle%2A> özelliklerine yeni bir <xref:System.Windows.Style> uygulayın.|  
|Boyutlandırma seçeneklerini ayarla|<xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>veya <xref:System.Windows.FrameworkElement.MinWidth%2A> özelliklerini ayarlayın. Daha fazla bilgi için bkz. [DataGrid denetimindeki boyutlandırma seçenekleri](sizing-options-in-the-datagrid-control.md).|  
|Seçili öğelere erişin|Seçili satırları almak için seçilen hücreleri ve <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> özelliğini almak üzere <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> özelliğini denetleyin. Daha fazla bilgi için bkz. <xref:System.Windows.Controls.DataGrid.SelectedCells%2A>.|  
|Son kullanıcı etkileşimlerini özelleştirme|<xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>, <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>, <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>ve <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> özelliklerini ayarlayın.|  
|Otomatik olarak oluşturulan sütunları iptal edin veya değiştirin|<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> olayı işleyin.|  
|Bir sütunu dondurma|<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> özelliğini 1 olarak ayarlayın ve <xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> özelliğini 0 olarak ayarlayarak sütunu en soldaki konuma taşıyın.|  
|Veri kaynağı olarak XML verileri kullanma|<xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, öğelerin koleksiyonunu temsil eden XPath sorgusuna bağlayın. <xref:System.Windows.Controls.DataGrid>her bir sütunu oluşturun. Bağlama üzerindeki XPath öğesini öğe kaynağındaki özelliği alan sorguya ayarlayarak her bir sütunu bağlayın. Örnek için bkz. <xref:System.Windows.Controls.DataGridTextColumn>|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: DataGrid Denetimindeki SQL Server Veritabanından Veri Görüntüleme](walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Yeni bir WPF projesi ayarlamayı, Entity Framework bir öğe eklemeyi, kaynağı ayarlamayı ve verileri bir <xref:System.Windows.Controls.DataGrid>görüntülemeyi açıklar.|  
|[Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme](how-to-add-row-details-to-a-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid>için satır ayrıntılarının nasıl oluşturulacağını açıklar.|  
|[Nasıl yapılır: DataGrid Denetimi ile Doğrulama Uygulama](how-to-implement-validation-with-the-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid> hücrelerinde ve satırlarda değerlerin nasıl doğrulanacağını ve doğrulama geri bildirimini görüntülemeyi açıklar.|  
|[DataGrid Denetiminde Varsayılan Klavye ve Fare Davranışı](default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|Klavye ve fareyi kullanarak <xref:System.Windows.Controls.DataGrid> denetimiyle nasıl etkileşim kuracağınızı açıklar.|  
|[Nasıl yapılır: DataGrid Denetiminde Verileri Gruplandırma, Sıralama ve Filtreleme](how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|Verileri gruplandırarak, sıralayarak ve filtreleyerek <xref:System.Windows.Controls.DataGrid> verilerin farklı yollarla nasıl görüntüleneceğini açıklar.|  
|[DataGrid Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid>mutlak ve otomatik boyutlandırmanın nasıl kontrol edileceğini açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataGrid>
- [Stil ve Şablon Oluşturma](styling-and-templating.md)
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Veri Şablonu Oluşturmaya Genel Bakış](../data/data-templating-overview.md)
- [Denetimler](index.md)
- [WPF İçerik Modeli](wpf-content-model.md)
