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
ms.openlocfilehash: fa7106207c69f19b647ba80ab7e724e9aad174c1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005082"
---
# <a name="table-overview"></a>Tabloya Genel Bakış
<xref:System.Windows.Documents.Table>, akış belge içeriğinin Kılavuz tabanlı sunumunu destekleyen bir blok düzeyi öğesidir. Bu öğenin esnekliği çok yararlı hale gelir, ancak doğru şekilde anlaşılması ve kullanılması daha karmaşık hale gelir.  
  
 Bu konu, aşağıdaki bölümleri içerir.  
  
- [Tablo Temelleri](#table_basics)  
  
- [Tablo nasıl farklı olur?](#table_vs_Grid)  
  
- [Temel tablo yapısı](#basic_table_structure)  
  
- [Tablo kapsama](#table_containment)  
  
- [Satır gruplandırmaları](#row_groupings)  
  
- [Arka plan Işleme önceliği](#rendering_precedence)  
  
- [Satırları veya sütunları yayma](#spanning_rows_or_columns)  
  
- [Kodla tablo oluşturma](#building_a_table_with_code)  
  
- [İlgili konular] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Tablo Temelleri  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Tablo nasıl farklı olur?  
 <xref:System.Windows.Documents.Table> ve <xref:System.Windows.Controls.Grid> bazı yaygın işlevselliği paylaşır, ancak her biri farklı senaryolar için idealdir. @No__t-0, akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md) ). Kılavuzlar, formların içinde en iyi şekilde kullanılır (temel olarak, akış içeriğinin dışında herhangi bir yerde). @No__t-0 <xref:System.Windows.Documents.Table>, <xref:System.Windows.Controls.Grid> olmadığı sürece sayfalandırma, sütun yeniden akıtma ve içerik seçimi gibi akış içeriği davranışlarını destekler. Diğer taraftan <xref:System.Windows.Controls.Grid> ' @no__t ın dışında en iyi şekilde <xref:System.Windows.Controls.Grid> ' nin bir satır ve sütun dizinine göre öğeleri eklemesi gibi birçok nedenden dolayı, <xref:System.Windows.Documents.Table> ' ü içermez. @No__t-0 öğesi, alt içeriğin katmanlanışını sağlar ve tek bir "hücresinde" birden fazla öğenin var olmasına izin verir. <xref:System.Windows.Documents.Table> katman katmanlarını desteklemez. @No__t-0 ' ın alt öğeleri, "hücre" sınırlarının alanına göre mutlak olarak konumlandırılmış olabilir. <xref:System.Windows.Documents.Table> bu özelliği desteklemez. Son olarak, <xref:System.Windows.Controls.Grid> daha az kaynak gerektirir <xref:System.Windows.Documents.Table>, performansı artırmak için <xref:System.Windows.Controls.Grid> kullanmayı düşünün.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Temel tablo yapısı  
 <xref:System.Windows.Documents.Table>, sütunlardan (<xref:System.Windows.Documents.TableColumn> öğe tarafından temsil edilen) ve satırlarda (<xref:System.Windows.Documents.TableRow> öğeleri tarafından gösterilen) oluşan kılavuza dayalı bir sunu sağlar. <xref:System.Windows.Documents.TableColumn> öğeleri içerik barındırmaz; yalnızca sütunların sütunlarını ve özelliklerini tanımlar. <xref:System.Windows.Documents.TableRow> öğelerinin, tablo için bir satır gruplandırması tanımlayan bir <xref:System.Windows.Documents.TableRowGroup> öğesinde barındırılması gerekir. tablo tarafından sunulacak gerçek içeriği içeren <xref:System.Windows.Documents.TableCell> öğeleri, bir <xref:System.Windows.Documents.TableRow> öğesinde barındırılmalıdır. <xref:System.Windows.Documents.TableCell>, yalnızca <xref:System.Windows.Documents.Block> ' den türetilen öğeleri içerebilir.  @No__t için geçerli alt öğeler-0 ekleme.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell> öğeleri doğrudan metin içeriğini barındırmayabilir. @No__t-0 gibi akış içeriği öğelerinin kapsama kuralları hakkında daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table> <xref:System.Windows.Controls.Grid> öğesine benzerdir, ancak daha fazla özelliğe sahiptir ve bu nedenle daha fazla kaynak yükü gerektirir.  
  
 Aşağıdaki örnekte, XAML ile basit bir 2 x 3 tablosu tanımlanmaktadır.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.  
  
 ![Temel bir tablonun nasıl işlediğini gösteren ekran görüntüsü.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Tablo kapsama  
 <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.Block> öğesinden türetilir ve <xref:System.Windows.Documents.Block> düzeyi öğeleri için ortak kurallara uyar.  @No__t-0 öğesi aşağıdaki öğelerden herhangi biri tarafından bulunabilir:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Satır gruplandırmaları  
 @No__t-0 öğesi tablo içindeki satırları rastgele gruplamak için bir yol sağlar; bir tablodaki her satır bir satır gruplandırmasına ait olmalıdır.  Satır grubu içindeki satırlar genellikle ortak bir amacı paylaşır ve bir grup olarak Stillenebilir.  Satır gruplandırmaları için ortak bir kullanım, tablo tarafından içerilen birincil içerikten bir başlık, üstbilgi ve altbilgi satırları gibi özel amaçlı satırları ayıramaktır.  
  
 Aşağıdaki örnek, stilli üstbilgi ve altbilgi satırları içeren bir tablo tanımlamak için XAML kullanır.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.  
  
 ![Ekran görüntüsü: tablo satır grupları](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Arka plan Işleme önceliği  
 Tablo öğeleri aşağıdaki sırada (z-Order küçükten en büyüğe) işlenir. Bu sıra değiştirilemez. Örneğin, bu öğeler için, bu belirlenen sırayı geçersiz kılmak için kullanabileceğiniz "Z-Order" özelliği yoktur.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Bir tablo içindeki bu öğelerin her biri için arka plan renklerini tanımlayan aşağıdaki örneği göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir (yalnızca arka plan renklerini gösterir).  
  
 ![Ekran görüntüsü: tablo&#45;z sırası](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Satırları veya sütunları yayma  
 Tablo hücreleri, sırasıyla <xref:System.Windows.Documents.TableCell.RowSpan%2A> veya <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> özniteliklerini kullanarak birden çok satır veya sütunu kapsayacak şekilde yapılandırılabilir.  
  
 Bir hücrenin üç sütuna yaydığı aşağıdaki örneği göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.  
  
 ![Ekran görüntüsü: üç sütunun hepsini kapsayan hücre](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Kodla tablo oluşturma  
 Aşağıdaki örneklerde, programlı olarak bir <xref:System.Windows.Documents.Table> oluşturma ve içerikle doldurma gösterilmektedir. Tablonun içerikleri, beş satıra (<xref:System.Windows.Documents.Table.RowGroups%2A> nesnesinde bulunan <xref:System.Windows.Documents.TableRow> nesneleriyle temsil edilir) ve altı sütun (<xref:System.Windows.Documents.TableColumn> nesneleri tarafından temsil edilir) olarak sunulur. Satırlar, tablonun tamamına başlık eklemek amaçlanan bir başlık satırı, tablodaki verilerin sütunlarını tanımlayacak bir başlık satırı ve Özet bilgileri içeren bir altbilgi satırı gibi farklı sunum amaçları için kullanılır.  "Title", "Header" ve "Footer" satırları kavramı tabloya ait değildir; Bunlar yalnızca farklı özelliklere sahip olan satırlardır. Tablo hücreleri, metin, resim veya neredeyse diğer [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesinden oluşan gerçek içeriği içerir.  
  
 İlk olarak, <xref:System.Windows.Documents.Table> ' i barındırmak için <xref:System.Windows.Documents.FlowDocument> oluşturulur ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve <xref:System.Windows.Documents.FlowDocument> içeriğine eklenir.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Sonra, altı <xref:System.Windows.Documents.TableColumn> nesnesi oluşturulur ve tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonuna eklenir ve bazı biçimlendirmeler uygulanır.  
  
> [!NOTE]
> Tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonunun standart sıfır tabanlı dizin oluşturmayı kullandığını unutmayın.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirmeler uygulanmış tabloya eklenir.  Başlık satırı, tablodaki altı sütunu kapsayan tek bir hücre içeriyor olur.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Ardından, başlık satırı oluşturulur ve tabloya eklenir ve üst bilgi satırındaki hücreler oluşturulur ve içerikle doldurulur.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Daha sonra, veriler için bir satır oluşturulur ve tabloya eklenir ve bu satırdaki hücreler oluşturulur ve içerikle doldurulur.  Bu satırı oluşturmak, biraz farklı biçimlendirme uygulanmış olan üst bilgi satırını oluşturmaya benzer.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Son olarak, bir altbilgi satırı oluşturulur, eklenir ve biçimlendirilir.  Başlık satırı gibi, alt bilgi, tablodaki altı sütunu kapsayan tek bir hücre içerir.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Akış belgesine genel bakış](flow-document-overview.md)
- [XAML ile tablo tanımlama](how-to-define-a-table-with-xaml.md)
- [WPF 'deki belgeler](documents-in-wpf.md)
- [Akış Içeriği öğelerini kullanma](how-to-use-flow-content-elements.md)
