---
title: "Tabloya Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], Table
- documents [WPF], tables
- tables [WPF]
ms.assetid: 5e1105f4-8fc4-473a-ba55-88c8e71386e6
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb9edf0439c985af015d6badd11c026449a82f57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="table-overview"></a>Tabloya Genel Bakış
<xref:System.Windows.Documents.Table>Kılavuz tabanlı sunu akan belgenin içerik destekleyen bir blok düzeyinde öğedir. Bu öğenin esnekliğini çok kullanışlı hale getirir, ancak aynı zamanda anlamak ve doğru bir şekilde kullanmak için daha karmaşık kolaylaştırır.  
  
 Bu konu aşağıdaki bölümleri içerir.  
  
-   [Tablo Temelleri](#table_basics)  
  
-   [Nasıl tablo farklı sonra Kılavuzu mu?](#table_vs_Grid)  
  
-   [Temel tablo yapısı](#basic_table_structure)  
  
-   [Tablo kapsama](#table_containment)  
  
-   [Satır gruplandırmalarına](#row_groupings)  
  
-   [Arka plan işleme önceliği](#rendering_precedence)  
  
-   [Satır ve sütunları yayma](#spanning_rows_or_columns)  
  
-   [Kodu içeren bir tablo oluşturma](#building_a_table_with_code)  
  
-   [İlgili konular] 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a>Tablo Temelleri  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a>Nasıl tablo farklı sonra Kılavuzu mu?  
 <xref:System.Windows.Documents.Table>ve <xref:System.Windows.Controls.Grid> ortak işlevselliğinin paylaşır, ancak her farklı senaryolar için uygundur. A <xref:System.Windows.Documents.Table> akış içeriği içinde kullanılmak üzere tasarlanmış (bkz [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md) akış içeriği hakkında daha fazla bilgi için). Kılavuzları en iyi forms içinde kullanılan (neredeyse her yerden dışında içerik akışı). İçinde bir <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> destekler, sayfa numaralandırma, sütun yeniden akış ve içerik seçimi gibi içerik davranışları akış bir <xref:System.Windows.Controls.Grid> desteklemez. A <xref:System.Windows.Controls.Grid> diğer yandan en iyi dışında kullanılan bir <xref:System.Windows.Documents.FlowDocument> dahil olmak üzere birçok nedenlerle <xref:System.Windows.Controls.Grid> bir satır ve sütun dizini üzerinde temel öğeleri ekler <xref:System.Windows.Documents.Table> desteklemez. <xref:System.Windows.Controls.Grid> Öğesi tek "hücre." mevcut birden fazla öğe izin vererek alt içeriğinin katmanlama sağlar <xref:System.Windows.Documents.Table>katmanlama desteklemez. Alt öğelerinin bir <xref:System.Windows.Controls.Grid> "hücre" sınırlarının alanına göre mutlak olarak konumlandırılmış olabilir. <xref:System.Windows.Documents.Table>Bu özelliği desteklemez. Son olarak, bir <xref:System.Windows.Controls.Grid> daha az kaynak gerektirir sonra bir <xref:System.Windows.Documents.Table> şekilde kullanmayı bir <xref:System.Windows.Controls.Grid> performansını artırmak için.  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a>Temel tablo yapısı  
 <xref:System.Windows.Documents.Table>sütunlardan oluşan bir kılavuz tabanlı sunumu sağlar (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri). <xref:System.Windows.Documents.TableColumn>öğeleri içeriği barındırmayan; Bunlar yalnızca sütunlar ve sütun özelliklerini tanımlar. <xref:System.Windows.Documents.TableRow>öğeleri barındırılan, içinde bir <xref:System.Windows.Documents.TableRowGroup> tablosu için satır gruplandırması tanımlar. <xref:System.Windows.Documents.TableCell>Tablo tarafından sunulacak gerçek içeriği içeren, öğeleri barındırılan, içinde bir <xref:System.Windows.Documents.TableRow> öğesi. <xref:System.Windows.Documents.TableCell>öğesinden türetilen öğeleri yalnızca içerebilir <xref:System.Windows.Documents.Block>.  İçin geçerli alt öğeleri bir <xref:System.Windows.Documents.TableCell> içerir.  
  
-   <xref:System.Windows.Documents.BlockUIContainer>  
  
-   <xref:System.Windows.Documents.List>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <xref:System.Windows.Documents.TableCell>öğeleri metin içeriği doğrudan barındıramazsınız. Akış için kapsama kuralları hakkında daha fazla bilgi için içerik öğeleri ister <xref:System.Windows.Documents.TableCell>, bkz: [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Table>benzer <xref:System.Windows.Controls.Grid> öğesi ancak daha fazla özellik içerir ve bu nedenle, daha yüksek kaynak yükü gerektirir.  
  
 Aşağıdaki örnek, bir basit 2 x 3 tabloyla tanımlar [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 Bu örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: temel tabloyu işleme](../../../../docs/framework/wpf/advanced/media/basictablerrender.png "BasicTablerRender")  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a>Tablo kapsama  
 <xref:System.Windows.Documents.Table>türetilen <xref:System.Windows.Documents.Block> öğesi için genel kurallar aynılarını ve <xref:System.Windows.Documents.Block> düzey öğeleri.  A <xref:System.Windows.Documents.Table> öğesi yer alan aşağıdaki öğeleri biriyle:  
  
-   <xref:System.Windows.Documents.FlowDocument>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a>Satır gruplandırmalarına  
 <xref:System.Windows.Documents.TableRowGroup> Öğesi rasgele bir tablo içindeki Grup satır için bir yol sağlar; tablodaki her satır için bir satır gruplandırma ait olmalıdır.  Bir satır grubunun satırlara genellikle ortak hedefi paylaşabilir ve bir grup olarak biçimlendirilmiş.  Bir ortak satır gruplandırmalarına için bir başlık, üstbilgi ve altbilgi satırları gibi özel amaçlı satır tablo tarafından barındırılan birincil içerik ayırmak için kullanılır.  
  
 Aşağıdaki örnek kullanır [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] stilde üstbilgi ve altbilgi satırları içeren bir tablo tanımlamak için.  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 Bu örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: Tablo satır grupları](../../../../docs/framework/wpf/advanced/media/table-rowgroups.png "Table_RowGroups")  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a>Arka plan işleme önceliği  
 Tablo öğeleri aşağıdaki sırayla (z-düşükten en yüksek düzeye) işleyebilir. Bu sırada değiştirilemez. Örneğin, bu yerleşik sipariş geçersiz kılmak için kullanabileceğiniz bu öğeler için "Z-sırası" özellik yok.  
  
1.  <xref:System.Windows.Documents.Table>  
  
2.  <xref:System.Windows.Documents.TableColumn>  
  
3.  <xref:System.Windows.Documents.TableRowGroup>  
  
4.  <xref:System.Windows.Documents.TableRow>  
  
5.  <xref:System.Windows.Documents.TableCell>  
  
 Bir tablo içinde bu öğelerin her biri için arka plan renklerini tanımlar aşağıdaki örnekte, göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 Bu örneğin (yalnızca gösteren arka plan renklerini) nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: Tablo z &#45; sipariş](../../../../docs/framework/wpf/advanced/media/table-zorder.png "Table_ZOrder")  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a>Satır ve sütunları yayma  
 Tablo hücrelerini, birden çok satır veya sütun kullanarak span için yapılandırılabilir <xref:System.Windows.Documents.TableCell.RowSpan%2A> veya <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> öznitelikleri, sırasıyla.  
  
 Aşağıdaki örnekte, bir hücre üç sütun yayılan göz önünde bulundurun.  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 Bu örneğin nasıl işlediğini aşağıdaki şekilde gösterilmiştir.  
  
 ![Ekran görüntüsü: Hücreli üç sütunu kapsayıcı](../../../../docs/framework/wpf/advanced/media/table-columnspan.png "Table_ColumnSpan")  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a>Kodu içeren bir tablo oluşturma  
 Program aracılığıyla oluşturma Aşağıdaki örnekler bir <xref:System.Windows.Documents.Table> ve içeriği ile doldurabilirsiniz. Tablosunun içeriğini beş satıra paylaştırıldı (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> içinde yer alan nesneler bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesi) ve altı sütunlar (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> nesneleri). Satırları tüm tablo, tablodaki veri sütunlarını açıklamak için bir başlık satırı ve Özet bilgiler ile altbilgi satırı başlık yönelik bir başlık satırı dahil olmak üzere, farklı sunu amaçlarıyla kullanılır.  "Title", "üstbilgi" ve "Altbilgi" satır kavramı tabloya devralınmış değildir; Bunlar yalnızca satır farklı özelliklere sahip olan. Tablo hücrelerini içeren metin, görüntüler veya neredeyse tüm diğer oluşan gerçek içeriği [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesi.  
  
 İlk olarak, bir <xref:System.Windows.Documents.FlowDocument> oluşturulan ana bilgisayara <xref:System.Windows.Documents.Table>ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve içeriğini eklenir <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 Ardından, altı <xref:System.Windows.Documents.TableColumn> nesneleri oluşturulur ve tablonun eklenen <xref:System.Windows.Documents.Table.Columns%2A> bazı uygulanan biçimlendirme içeren koleksiyon.  
  
> [!NOTE]
>  Unutmayın tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu kullanan standart sıfır tabanlı dizin.  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanmış tablosuna eklenir.  Tablodaki tüm altı sütunu kapsayan tek bir hücre içermesi için başlık satırı olur.  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 Ardından, bir başlık satırı oluşturulur ve tabloya eklenir ve üstbilgi satırındaki hücreler oluşturulur ve içerik ile doldurulur.  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 Ardından, veriler için bir satır oluşturulur ve tabloya eklenir ve bu satırda hücreler oluşturulur ve içerik ile doldurulur.  Bu satırı oluşturmak uygulanan biraz farklı biçimlendirme ile üstbilgi satırını oluşturmakla benzerdir.  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 Son olarak, bir altbilgi satırı oluşturulan, eklenen biçimlendirilmiş ve.  Başlık satırı gibi altbilgi tablodaki tüm altı sütunu kapsayan tek bir hücre içerir.  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Akış belgesi genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [XAML içeren bir tablo tanımlayın](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [WPF belgeleri](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Akış içeriği öğeleri kullanma](../../../../docs/framework/wpf/advanced/how-to-use-flow-content-elements.md)
