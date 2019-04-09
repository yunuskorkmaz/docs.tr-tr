---
title: Tabloya Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
ms.openlocfilehash: eb16f633f78e9d345d20c93847e2c22173267960
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161440"
---
# <a name="table-overview"></a>Tabloya Genel Bakış
<xref:System.Windows.Documents.Table> ızgara tabanlı akış belge içeriği sunumunu destekleyen bir blok düzeyinde öğesidir. Bu öğenin esnekliğini çok kullanışlı hale getirir, ancak aynı zamanda, anlamak ve doğru bir şekilde kullanmak için daha karmaşık hale getirir.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
-   [Tablo Temelleri](#table_basics)  
  
-   [Nasıl tablo farklı sonra kılavuz var mı?](#table_vs_Grid)  
  
-   [Temel tablo yapısı](#basic_table_structure)  
  
-   [Tablo kapsama](#table_containment)  
  
-   [Satır grupları](#row_groupings)  
  
-   [Arka plan işleme önceliği](#rendering_precedence)  
  
-   [Satırları veya sütunları yayma](#spanning_rows_or_columns)  
  
-   [Kod içeren bir tablo oluşturma](#building_a_table_with_code)  
  
-   [İlgili konular] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Tablo Temelleri  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Nasıl tablo farklı sonra kılavuz var mı?  
 <xref:System.Windows.Documents.Table> ve <xref:System.Windows.Controls.Grid> bazı ortak işlevselliği paylaşır, ancak her farklı senaryolar için idealdir. A <xref:System.Windows.Documents.Table> akış içeriği içinde kullanmak için tasarlanmıştır (bkz [akış belgesine genel bakış](flow-document-overview.md) akış içeriği hakkında daha fazla bilgi için). Kılavuzlar formları içinde kullanılan en iyi (temel olarak her yerde dışında içerik akışı). İçinde bir <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> destekleyen akış içerik davranışları sayfalandırma ve sütun yeniden akış içerik seçimi gibi bir <xref:System.Windows.Controls.Grid> desteklemez. A <xref:System.Windows.Controls.Grid> diğer yandan en iyi dışında kullanılan bir <xref:System.Windows.Documents.FlowDocument> dahil olmak üzere birçok nedenden dolayı <xref:System.Windows.Controls.Grid> öğeleri satır ve sütun dizinini temel alarak ekler <xref:System.Windows.Documents.Table> desteklemez. <xref:System.Windows.Controls.Grid> Öğesi alt içeriğin tek bir "hücre." mevcut birden fazla öğe izin vererek, katman sağlar. <xref:System.Windows.Documents.Table> katmanlama desteklemez. Alt öğeleri bir <xref:System.Windows.Controls.Grid> "hücre" sınırlarının alanını göre mutlak konumlandırılmalıdır. <xref:System.Windows.Documents.Table> Bu özelliği desteklemez. Son olarak, bir <xref:System.Windows.Controls.Grid> daha az kaynak gerektirir bir <xref:System.Windows.Documents.Table> şekilde kullanmayı bir <xref:System.Windows.Controls.Grid> performansını artırmak için.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Temel tablo yapısı  
 <xref:System.Windows.Documents.Table> sütunlardan oluşan bir kılavuz tabanlı sunu sağlar (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri). <xref:System.Windows.Documents.TableColumn> Öğe içerik barındırmayan; Bunlar yalnızca sütunları ve sütun özelliklerini tanımlayın. <xref:System.Windows.Documents.TableRow> öğeleri barındırılan, içinde bir <xref:System.Windows.Documents.TableRowGroup> tablosundaki satırları bir gruplandırmasını tanımlar. <xref:System.Windows.Documents.TableCell> Tablo tarafından sunulan gerçek içeriği içeren, öğeleri, barındırılan, içinde bir <xref:System.Windows.Documents.TableRow> öğesi. <xref:System.Windows.Documents.TableCell> yalnızca türetilen öğeler içerebilir <xref:System.Windows.Documents.Block>.  Geçerli alt öğeleri için bir <xref:System.Windows.Documents.TableCell> içerir.  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell> öğe metin içeriği doğrudan barındıramazsınız. Akış için kapsama kuralları hakkında daha fazla bilgi için gibi içerik öğeler <xref:System.Windows.Documents.TableCell>, bkz: [akış belgesine genel bakış](flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table> benzer <xref:System.Windows.Controls.Grid> öğe ancak daha fazla özellik içerir ve bu nedenle büyük kaynağı ek yükü gerektirir.  
  
 Aşağıdaki örnek, bir basit 2x3lük tabloyla tanımlar [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.  
  
 ![Temel tablo nasıl işlediğini gösteren ekran görüntüsü.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Tablo kapsama  
 <xref:System.Windows.Documents.Table> öğesinden türetilen <xref:System.Windows.Documents.Block> öğesi için genel kurallar aynılarını ve <xref:System.Windows.Documents.Block> düzey öğeleri.  A <xref:System.Windows.Documents.Table> öğesi yer almalıdır herhangi aşağıdaki öğeleri biri:  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Satır grupları  
 <xref:System.Windows.Documents.TableRowGroup> Öğesi rasgele bir tablo içindeki satırları grubu için bir yol sağlar; tablodaki her satır bir satır gruba ait olmanız gerekir.  Bir satır grubu içindeki satır genellikle ortak bir hedefi paylaşın ve bir grup olarak stillenmiş.  Bir satır gruplandırmalarına birincil içerik tablosu tarafından bulunan bir başlık, üstbilgi ve altbilgi satırlar gibi özel amaçlı satırları ayırmak için kullanılır.  
  
 Aşağıdaki örnekte [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] stil uygulanmış üstbilgi ve altbilgi satırları içeren bir tablo tanımlamak için.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: Tablo satır grupları](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Arka plan işleme önceliği  
 Tablo öğelerini (z düzenini en düşükten yükseğe doğru) aşağıdaki sırayla işlenir. Bu sıra değiştirilemez. Örneğin, kurulan bu sıralamayı geçersiz kılmak için kullanabileceğiniz bu öğelerin "Z düzenini" özellik yok.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Bir tablo içinde bu öğelerin her biri için arka plan renkleri tanımlar aşağıdaki örneği inceleyin.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Aşağıdaki şekil, bu örneğin (yalnızca gösteren arka plan renkleri) nasıl işlediğini gösterir.  
  
 ![Ekran: Tablo z&#45;sipariş](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Satırları veya sütunları yayma  
 Tablo hücreleri kullanarak birden çok satır veya sütuna yayılmasını yapılandırılabilir <xref:System.Windows.Documents.TableCell.RowSpan%2A> veya <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> öznitelikleri, sırasıyla.  
  
 Aşağıdaki örnekte, üç sütun, kapsayan bir hücre göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.  
  
 ![Ekran: Üç sütunu yayılan hücre](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Kod içeren bir tablo oluşturma  
 Aşağıdaki örnekler program aracılığıyla nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Documents.Table> ve içerikle doldurur. Tablosunun beş satır paylaştırıldı (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> bulunan nesneleri bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesi) ve altı sütunları (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> nesneleri). Satırları tablonun tamamını ve tabloda veri sütunlarının açıklamak için bir üst bilgi satırı özet bilgileri içeren bir alt bilgi satırı başlık yönelik bir başlık satırı da dahil olmak üzere farklı sunu amacıyla kullanılır.  "Title", "header" ve "alt" satırları kavramı tabloya devralınan değildir; Bunlar, yalnızca satır farklı özelliklere sahip olur. Tablo hücreleri metinlerin, resimlerin veya her türlü diğer oluşan gerçek içeriği içeren [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesi.  
  
 İlk olarak, bir <xref:System.Windows.Documents.FlowDocument> oluşturulan konağa <xref:System.Windows.Documents.Table>ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve içeriği için eklenen <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Ardından, altı <xref:System.Windows.Documents.TableColumn> nesnelerinin oluşturulduğu ve tablonun eklenen <xref:System.Windows.Documents.Table.Columns%2A> bazı biçimlendirme uygulanmış olan koleksiyonu.  
  
> [!NOTE]
>  Unutmayın tablo <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonun kullandığı standart sıfır tabanlı dizin.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanmış tablosuna eklenir.  Tablodaki tüm altı sütunu kapsayan tek bir hücre içermesi için başlık satırı gerçekleşir.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Ardından, bir üst bilgi satırı oluşturulur ve tabloya eklenen ve üst bilgi satırı hücrelerde oluşturulur ve içeriği ile doldurulur.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Ardından, veriler için bir satır oluşturulur ve tabloya eklenen ve bu satırı hücrelerde oluşturulur ve içerikle doldurulur.  Bu satırı oluşturma üst bilgi satırı biraz farklı biçimlendirme uygulanmış oluşturmak için benzer.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Son olarak, bir alt bilgi satırı oluşturulan, eklenen biçimlendirilmiş ve.  Başlık satırı gibi tüm altı sütun kapsayan tek bir hücre alt bilgi içerir.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Akış Belgesine Genel Bakış](flow-document-overview.md)
- [XAML ile Tablo Tanımlama](how-to-define-a-table-with-xaml.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Akış İçeriği Öğelerini Kullanma](how-to-use-flow-content-elements.md)
