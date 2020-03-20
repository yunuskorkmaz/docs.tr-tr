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
ms.openlocfilehash: 4bd747cea43755116c56b16f1de9a6ffb59935ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187266"
---
# <a name="table-overview"></a>Tabloya Genel Bakış
<xref:System.Windows.Documents.Table>Akış belge içeriğinin ızgara tabanlı sunusunu destekleyen bir blok düzeyi öğesidir. Bu öğenin esnekliği çok yararlı hale getirir, ama aynı zamanda daha doğru anlamak ve kullanmak daha karmaşık hale getirir.  
  
 Bu konuda aşağıdaki bölümler yer almaktadır.  
  
- [Tablo Temelleri](#table_basics)  
  
- [Nasıl Tablo Farklı sonra Grid nedir?](#table_vs_Grid)  
  
- [Temel Tablo Yapısı](#basic_table_structure)  
  
- [Tablo İçerme](#table_containment)  
  
- [Satır Gruplandırmaları](#row_groupings)  
  
- [Arka Plan Oluşturma Önceliği](#rendering_precedence)  
  
- [Satırları veya Sütunları Kapsayan](#spanning_rows_or_columns)  
  
- [Kodlu Tablo Oluşturma](#building_a_table_with_code)  
  
- [İlgili Konular]
  
<a name="table_basics"></a>
## <a name="table-basics"></a>Tablo Temelleri  
  
<a name="table_vs_Grid"></a>
### <a name="how-is-table-different-then-grid"></a>Nasıl Tablo Farklı sonra Grid nedir?  
 <xref:System.Windows.Documents.Table>ve <xref:System.Windows.Controls.Grid> bazı ortak işlevleri paylaşın, ancak her biri farklı senaryolar için en uygunudur. A, <xref:System.Windows.Documents.Table> akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için [Akış Belgesine Genel Bakış'a](flow-document-overview.md) bakın). Izgaralar en iyi formların içinde kullanılır (temelde akış içeriğidışında herhangi bir yerde). Bir <xref:System.Windows.Documents.FlowDocument>içinde, <xref:System.Windows.Documents.Table> bir değil iken <xref:System.Windows.Controls.Grid> pagination, sütun yeniden akışı ve içerik seçimi gibi akış içeriği davranışlarını destekler. Öte <xref:System.Windows.Controls.Grid> yandan a en iyi bir <xref:System.Windows.Documents.FlowDocument> satır ve <xref:System.Windows.Controls.Grid> sütun dizini dayalı öğeleri ekler <xref:System.Windows.Documents.Table> dahil olmak üzere birçok nedenden dolayı dışında kullanılır, değil. Öğe, <xref:System.Windows.Controls.Grid> tek bir "hücre" içinde birden fazla öğenin bulunmasına izin vererek alt içeriğin katmanlanmasına izin verir. <xref:System.Windows.Documents.Table>katmanlamayı desteklemez. A'nın <xref:System.Windows.Controls.Grid> alt öğeleri kesinlikle kendi "hücre" sınırlarının alanına göre konumlandırılabilir. <xref:System.Windows.Documents.Table>bu özelliği desteklemez. Son olarak, daha <xref:System.Windows.Controls.Grid> az <xref:System.Windows.Documents.Table> kaynak gerektirir <xref:System.Windows.Controls.Grid> sonra bir çok performansı artırmak için bir kullanmayı düşünün.  
  
<a name="basic_table_structure"></a>
### <a name="basic-table-structure"></a>Temel Tablo Yapısı  
 <xref:System.Windows.Documents.Table>sütunlar (öğelerle <xref:System.Windows.Documents.TableColumn> temsil edilen) ve satırlardan (öğelerle <xref:System.Windows.Documents.TableRow> temsil edilen) oluşan ızgara tabanlı bir sunu sağlar. <xref:System.Windows.Documents.TableColumn>öğeler içerik barındırmaz; sütunları ve sütunların özelliklerini tanımlarlar. <xref:System.Windows.Documents.TableRow>öğeler, tablo için <xref:System.Windows.Documents.TableRowGroup> satır gruplandırmasını tanımlayan bir öğede barındırılmalıdır. <xref:System.Windows.Documents.TableCell>tablo tarafından sunulacak gerçek içeriği içeren öğeler, bir <xref:System.Windows.Documents.TableRow> öğede barındırılmalıdır. <xref:System.Windows.Documents.TableCell>yalnızca <xref:System.Windows.Documents.Block>.  Bir <xref:System.Windows.Documents.TableCell> için geçerli alt öğeleri içerir.  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <xref:System.Windows.Documents.TableCell>öğeler doğrudan metin içeriğini barındıramaz. Akış içeriği öğeleri <xref:System.Windows.Documents.TableCell>için kapsama kuralları hakkında daha fazla bilgi için bkz. [Flow Document Overview](flow-document-overview.md)  
  
> [!NOTE]
> <xref:System.Windows.Documents.Table><xref:System.Windows.Controls.Grid> öğeye benzer, ancak daha fazla yeteneği vardır ve bu nedenle, daha fazla kaynak yükü gerektirir.  
  
 Aşağıdaki örnek, XAML ile basit bir 2 x 3 tablo tanımlar.  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlettigini gösterir.  
  
 ![Temel tablonun nasıl işladığını gösteren ekran görüntüsü.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>
### <a name="table-containment"></a>Tablo İçerme  
 <xref:System.Windows.Documents.Table><xref:System.Windows.Documents.Block> öğeden türetilmiştir ve düzey öğeleri için <xref:System.Windows.Documents.Block> ortak kurallara bağlıdır.  Bir <xref:System.Windows.Documents.Table> öğe aşağıdaki öğelerden herhangi biri tarafından bulunabilir:  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>
### <a name="row-groupings"></a>Satır Gruplandırmaları  
 Öğe, <xref:System.Windows.Documents.TableRowGroup> bir tablo içindeki satırları rasgele gruplandırmanın bir yolunu sağlar; tablodaki her satır bir satır grubuna ait olmalıdır.  Satır grubu içindeki satırlar genellikle ortak bir amacı paylaşır ve grup olarak şekillendirilebilir.  Satır gruplandırmaları için yaygın bir kullanım, tablonun içerdiği birincil içerikten başlık, üstbilgi ve altbilgi satırları gibi özel amaçlı satırları ayırmaktır.  
  
 Aşağıdaki örnek, stilde üstbilgi ve altbilgi satırları olan bir tablo tanımlamak için XAML kullanır.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlettigini gösterir.  
  
 ![Ekran görüntüsü: Tablo satır grupları](./media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>
### <a name="background-rendering-precedence"></a>Arka Plan Oluşturma Önceliği  
 Tablo öğeleri aşağıdaki sırada işlenir (en düşükten en yükseğe z sırası). Bu sipariş değiştirilemez. Örneğin, bu öğeler için bu kurulu düzeni geçersiz kılmak için kullanabileceğiniz "Z-order" özelliği yoktur.  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 Tablodaki bu öğelerin her biri için arka plan renklerini tanımlayan aşağıdaki örneği göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlettigini gösterir (yalnızca arka plan renklerini gösterir).  
  
 ![Ekran görüntüsü: Tablo z&#45;sırası](./media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>
### <a name="spanning-rows-or-columns"></a>Satırları veya Sütunları Kapsayan  
 Tablo hücreleri, sırasıyla öznitelikleri kullanarak birden çok <xref:System.Windows.Documents.TableCell.RowSpan%2A> <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> satır veya sütuna yayılacak şekilde yapılandırılabilir.  
  
 Bir hücrenin üç sütuna yayıldığı aşağıdaki örneği göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Aşağıdaki şekil, bu örneğin nasıl işlettigini gösterir.  
  
 ![Ekran görüntüsü: Üç sütunu da kapsayan hücre](./media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>
## <a name="building-a-table-with-code"></a>Kodlu Tablo Oluşturma  
 Aşağıdaki örnekler, programlı bir <xref:System.Windows.Documents.Table> oluşturmak ve içerik ile doldurmak nasıl gösterir. Tablonun içeriği beş satıra (bir <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.Table.RowGroups%2A> nesnede bulunan nesnelerle temsil edilir) ve altı sütuna (nesnelerle <xref:System.Windows.Documents.TableColumn> temsil edilir) ayrılır. Satırlar, tablonun tamamını nismesiyle başlık satırı, tablodaki veri sütunlarını açıklamak için bir üstbilgi satırı ve özet bilgilerini içeren bir altbilgi satırı gibi farklı sunu amaçları için kullanılır.  "Başlık", "üstbilgi" ve "altbilgi" satırları kavramının tablonun doğasında olmadığını unutmayın; bunlar sadece farklı özelliklere sahip satırlar. Tablo hücreleri, metin, resim veya hemen hemen başka [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir öğeden oluşabilen gerçek içeriği içerir.  
  
 İlk olarak, <xref:System.Windows.Documents.FlowDocument> bir ev <xref:System.Windows.Documents.Table>sahipliği yapmak <xref:System.Windows.Documents.Table> için oluşturulur ve yeni <xref:System.Windows.Documents.FlowDocument>oluşturulur ve içeriğini eklenir.  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Ardından, <xref:System.Windows.Documents.TableColumn> altı nesne oluşturulur ve bazı biçimlendirme uygulanarak tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonuna eklenir.  
  
> [!NOTE]
> Tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonunda standart sıfır tabanlı dizin oluşturma nın kullanDığını unutmayın.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Daha sonra, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanarak tabloya eklenir.  Başlık satırı, tablodaki altı sütunun tümine yayılan tek bir hücre içerir.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Daha sonra, bir üstbilgi satırı oluşturulur ve tabloya eklenir ve üstbilgi satırındaki hücreler oluşturulur ve içerikle doldurulur.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Ardından, veri için bir satır oluşturulur ve tabloya eklenir ve bu satırdaki hücreler oluşturulur ve içerikle doldurulur.  Bu satırı oluşturmak, biraz farklı biçimlendirme uygulanarak üstbilgi satırını oluşturmaya benzer.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Son olarak, bir altbilgi satırı oluşturulur, eklenir ve biçimlendirilir.  Başlık satırı gibi, altbilgi de tablodaki altı sütunun tümine yayılan tek bir hücre içerir.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Akış Belgesine Genel Bakış](flow-document-overview.md)
- [XAML ile Tablo Tanımlama](how-to-define-a-table-with-xaml.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Akış İçeriği Öğelerini Kullanma](how-to-use-flow-content-elements.md)
