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
ms.openlocfilehash: 01a5233a5436688caee3783cb26d344284df52e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964306"
---
# <a name="table-overview"></a>Tabloya Genel Bakış
<xref:System.Windows.Documents.Table>, akış belge içeriğinin Kılavuz tabanlı sunumunu destekleyen bir blok düzeyi öğesidir. Bu öğenin esnekliği çok yararlı hale gelir, ancak doğru şekilde anlaşılması ve kullanılması daha karmaşık hale gelir.  
  
 Bu konuda aşağıdaki bölümleri içerir.  
  
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
 <xref:System.Windows.Documents.Table>ve <xref:System.Windows.Controls.Grid> bazı yaygın işlevleri paylaşabilirsiniz, ancak her biri farklı senaryolar için idealdir. , Akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için bkz. [akış belgesine genel bakış](flow-document-overview.md) ). <xref:System.Windows.Documents.Table> Kılavuzlar, formların içinde en iyi şekilde kullanılır (temel olarak, akış içeriğinin dışında herhangi bir yerde). Bir <xref:System.Windows.Documents.FlowDocument>içinde, <xref:System.Windows.Documents.Table> sayfalandırma, sütun yeniden akışı <xref:System.Windows.Controls.Grid> ve içerik seçimi gibi akış içeriği davranışlarını destekler, ancak bunu yapmaz. Diğer taraftan bir, bir satır ve sütun dizinine <xref:System.Windows.Documents.Table> göre öğe ekleme dahil olmak üzere <xref:System.Windows.Controls.Grid> birçok nedenden dolayı en iyi şekilde kullanılır <xref:System.Windows.Documents.FlowDocument>. <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid> Öğesi, alt içeriğin katmanlanışını sağlar ve tek bir "hücresinde" birden fazla öğenin var olmasına izin verir. <xref:System.Windows.Documents.Table>katmanlanın desteklemez. Öğesinin <xref:System.Windows.Controls.Grid> alt öğeleri, "hücre" sınırlarının alanına göre mutlak olarak konumlandırılmış olabilir. <xref:System.Windows.Documents.Table>Bu özelliği desteklemez. Son olarak, <xref:System.Windows.Controls.Grid> bir daha az kaynak <xref:System.Windows.Documents.Table> gerektirir. bu nedenle, <xref:System.Windows.Controls.Grid> performansı artırmak için bir kullanmayı düşünün.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Temel tablo yapısı  
 <xref:System.Windows.Documents.Table>sütunlardan ( <xref:System.Windows.Documents.TableColumn> öğelerle gösterilir) ve satırlarıyla ( <xref:System.Windows.Documents.TableRow> öğelerle gösterilir) oluşan kılavuza dayalı bir sunu sağlar. <xref:System.Windows.Documents.TableColumn>öğeler içerik barındırmaz; yalnızca sütunların sütunlarını ve özelliklerini tanımlar. <xref:System.Windows.Documents.TableRow>öğeler, tablo için bir satır <xref:System.Windows.Documents.TableRowGroup> gruplandırması tanımlayan bir öğede barındırılmalıdır. <xref:System.Windows.Documents.TableCell>tablo tarafından sunulacak gerçek içeriği içeren öğelerin bir <xref:System.Windows.Documents.TableRow> öğesinde barındırılması gerekir. <xref:System.Windows.Documents.TableCell>yalnızca öğesinden <xref:System.Windows.Documents.Block>türetilen öğeleri içerebilir.  Bir <xref:System.Windows.Documents.TableCell> içerme için geçerli alt öğeler.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>öğeler metin içeriğini doğrudan barındıramayabilir. Gibi <xref:System.Windows.Documents.TableCell>Flow içerik öğelerine yönelik kapsama kuralları hakkında daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table>, <xref:System.Windows.Controls.Grid> öğesine benzerdir, ancak daha fazla özelliğe sahiptir ve bu nedenle daha fazla kaynak yükü gerektirir.  
  
 Aşağıdaki örnek ile [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]basit bir 2 x 3 tablosunu tanımlar.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.  
  
 ![Temel bir tablonun nasıl işlediğini gösteren ekran görüntüsü.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Tablo kapsama  
 <xref:System.Windows.Documents.Table>öğesinden türetilir ve düzey öğeleri için <xref:System.Windows.Documents.Block> ortak kurallara uyar. <xref:System.Windows.Documents.Block>  Bir <xref:System.Windows.Documents.Table> öğe aşağıdaki öğelerden herhangi biri tarafından bulunabilir:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Satır gruplandırmaları  
 Öğesi <xref:System.Windows.Documents.TableRowGroup> , tablodaki satırları rastgele gruplamak için bir yol sağlar; bir tablodaki her satır bir satır gruplandırmasına ait olmalıdır.  Satır grubu içindeki satırlar genellikle ortak bir amacı paylaşır ve bir grup olarak Stillenebilir.  Satır gruplandırmaları için ortak bir kullanım, tablo tarafından içerilen birincil içerikten bir başlık, üstbilgi ve altbilgi satırları gibi özel amaçlı satırları ayıramaktır.  
  
 Aşağıdaki örnek, stilli [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] üstbilgi ve altbilgi satırlarıyla bir tablo tanımlamak için kullanır.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.  
  
 ![Yakala Tablo satır grupları](./media/table-rowgroups.png "Table_RowGroups")  
  
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
  
 ![Yakala Tablo z&#45;sırası](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Satırları veya sütunları yayma  
 Tablo hücreleri, sırasıyla <xref:System.Windows.Documents.TableCell.RowSpan%2A> veya <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> özniteliklerini kullanarak birden çok satır veya sütunu kapsayacak şekilde yapılandırılabilir.  
  
 Bir hücrenin üç sütuna yaydığı aşağıdaki örneği göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.  
  
 ![Yakala Üç sütunun]tümünü kapsayan hücre(./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Kodla tablo oluşturma  
 Aşağıdaki örneklerde, programlama yoluyla nasıl bir <xref:System.Windows.Documents.Table> oluşturma ve içerikle doldurma gösterilmektedir. Tablonun içerikleri beş satıra (bir <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.Table.RowGroups%2A> nesnede bulunan nesnelerle gösterilir) ve altı sütuna (nesnelere göre <xref:System.Windows.Documents.TableColumn> gösterilen) dahil edilir. Satırlar, tablonun tamamına başlık eklemek amaçlanan bir başlık satırı, tablodaki verilerin sütunlarını tanımlayacak bir başlık satırı ve Özet bilgileri içeren bir altbilgi satırı gibi farklı sunum amaçları için kullanılır.  "Title", "Header" ve "Footer" satırları kavramı tabloya ait değildir; Bunlar yalnızca farklı özelliklere sahip olan satırlardır. Tablo hücreleri, metin, resim veya neredeyse herhangi bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğeden oluşan gerçek içeriği içerir.  
  
 İlk olarak, <xref:System.Windows.Documents.FlowDocument> bir <xref:System.Windows.Documents.Table>barındırmak için oluşturulur ve yeni <xref:System.Windows.Documents.Table> bir <xref:System.Windows.Documents.FlowDocument>oluşturulur ve içeriğine eklenir.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Sonra, altı <xref:System.Windows.Documents.TableColumn> nesne oluşturulur ve <xref:System.Windows.Documents.Table.Columns%2A> tablonun koleksiyonuna eklenir, bazı biçimlendirmeler uygulanır.  
  
> [!NOTE]
> Tablo <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonunun standart sıfır tabanlı dizin oluşturmayı kullandığını unutmayın.  
  
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

- [Akış Belgesine Genel Bakış](flow-document-overview.md)
- [XAML ile Tablo Tanımlama](how-to-define-a-table-with-xaml.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Akış İçeriği Öğelerini Kullanma](how-to-use-flow-content-elements.md)
