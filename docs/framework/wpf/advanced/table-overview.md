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
ms.openlocfilehash: 01ab11d8e3c1d2c84514770816ca9c9eab0835b6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649186"
---
# <a name="table-overview"></a><span data-ttu-id="bff8f-102">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bff8f-102">Table Overview</span></span>
<span data-ttu-id="bff8f-103"><xref:System.Windows.Documents.Table> ızgara tabanlı akış belge içeriği sunumunu destekleyen bir blok düzeyinde öğesidir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="bff8f-104">Bu öğenin esnekliğini çok kullanışlı hale getirir, ancak aynı zamanda, anlamak ve doğru bir şekilde kullanmak için daha karmaşık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="bff8f-105">Bu konuda aşağıdaki bölümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="bff8f-106">Tablo Temelleri</span><span class="sxs-lookup"><span data-stu-id="bff8f-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="bff8f-107">Nasıl tablo farklı sonra kılavuz var mı?</span><span class="sxs-lookup"><span data-stu-id="bff8f-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="bff8f-108">Temel tablo yapısı</span><span class="sxs-lookup"><span data-stu-id="bff8f-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="bff8f-109">Tablo kapsama</span><span class="sxs-lookup"><span data-stu-id="bff8f-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="bff8f-110">Satır grupları</span><span class="sxs-lookup"><span data-stu-id="bff8f-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="bff8f-111">Arka plan işleme önceliği</span><span class="sxs-lookup"><span data-stu-id="bff8f-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="bff8f-112">Satırları veya sütunları yayma</span><span class="sxs-lookup"><span data-stu-id="bff8f-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="bff8f-113">Kod içeren bir tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="bff8f-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="bff8f-114">[İlgili konular]</span><span class="sxs-lookup"><span data-stu-id="bff8f-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="bff8f-115">Tablo Temelleri</span><span class="sxs-lookup"><span data-stu-id="bff8f-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="bff8f-116">Nasıl tablo farklı sonra kılavuz var mı?</span><span class="sxs-lookup"><span data-stu-id="bff8f-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="bff8f-117"><xref:System.Windows.Documents.Table> ve <xref:System.Windows.Controls.Grid> bazı ortak işlevselliği paylaşır, ancak her farklı senaryolar için idealdir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="bff8f-118">A <xref:System.Windows.Documents.Table> akış içeriği içinde kullanmak için tasarlanmıştır (bkz [akış belgesine genel bakış](flow-document-overview.md) akış içeriği hakkında daha fazla bilgi için).</span><span class="sxs-lookup"><span data-stu-id="bff8f-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="bff8f-119">Kılavuzlar formları içinde kullanılan en iyi (temel olarak her yerde dışında içerik akışı).</span><span class="sxs-lookup"><span data-stu-id="bff8f-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="bff8f-120">İçinde bir <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> destekleyen akış içerik davranışları sayfalandırma ve sütun yeniden akış içerik seçimi gibi bir <xref:System.Windows.Controls.Grid> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bff8f-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="bff8f-121">A <xref:System.Windows.Controls.Grid> diğer yandan en iyi dışında kullanılan bir <xref:System.Windows.Documents.FlowDocument> dahil olmak üzere birçok nedenden dolayı <xref:System.Windows.Controls.Grid> öğeleri satır ve sütun dizinini temel alarak ekler <xref:System.Windows.Documents.Table> desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bff8f-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="bff8f-122"><xref:System.Windows.Controls.Grid> Öğesi alt içeriğin tek bir "hücre." mevcut birden fazla öğe izin vererek, katman sağlar.</span><span class="sxs-lookup"><span data-stu-id="bff8f-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="bff8f-123"><xref:System.Windows.Documents.Table> katmanlama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bff8f-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="bff8f-124">Alt öğeleri bir <xref:System.Windows.Controls.Grid> "hücre" sınırlarının alanını göre mutlak konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bff8f-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="bff8f-125"><xref:System.Windows.Documents.Table> Bu özelliği desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bff8f-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="bff8f-126">Son olarak, bir <xref:System.Windows.Controls.Grid> daha az kaynak gerektirir bir <xref:System.Windows.Documents.Table> şekilde kullanmayı bir <xref:System.Windows.Controls.Grid> performansını artırmak için.</span><span class="sxs-lookup"><span data-stu-id="bff8f-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="bff8f-127">Temel tablo yapısı</span><span class="sxs-lookup"><span data-stu-id="bff8f-127">Basic Table Structure</span></span>  
 <span data-ttu-id="bff8f-128"><xref:System.Windows.Documents.Table> sütunlardan oluşan bir kılavuz tabanlı sunu sağlar (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> öğeleri) ve satır (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> öğeleri).</span><span class="sxs-lookup"><span data-stu-id="bff8f-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="bff8f-129"><xref:System.Windows.Documents.TableColumn> Öğe içerik barındırmayan; Bunlar yalnızca sütunları ve sütun özelliklerini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="bff8f-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="bff8f-130"><xref:System.Windows.Documents.TableRow> öğeleri barındırılan, içinde bir <xref:System.Windows.Documents.TableRowGroup> tablosundaki satırları bir gruplandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bff8f-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="bff8f-131"><xref:System.Windows.Documents.TableCell> Tablo tarafından sunulan gerçek içeriği içeren, öğeleri, barındırılan, içinde bir <xref:System.Windows.Documents.TableRow> öğesi.</span><span class="sxs-lookup"><span data-stu-id="bff8f-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="bff8f-132"><xref:System.Windows.Documents.TableCell> yalnızca türetilen öğeler içerebilir <xref:System.Windows.Documents.Block>.</span><span class="sxs-lookup"><span data-stu-id="bff8f-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="bff8f-133">Geçerli alt öğeleri için bir <xref:System.Windows.Documents.TableCell> içerir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
>  <span data-ttu-id="bff8f-134"><xref:System.Windows.Documents.TableCell> öğe metin içeriği doğrudan barındıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="bff8f-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="bff8f-135">Akış için kapsama kuralları hakkında daha fazla bilgi için gibi içerik öğeler <xref:System.Windows.Documents.TableCell>, bkz: [akış belgesine genel bakış](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bff8f-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bff8f-136"><xref:System.Windows.Documents.Table> benzer <xref:System.Windows.Controls.Grid> öğe ancak daha fazla özellik içerir ve bu nedenle büyük kaynağı ek yükü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="bff8f-137">Aşağıdaki örnek, bir basit 2x3lük tabloyla tanımlar [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bff8f-137">The following example defines a simple 2 x 3 table with [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="bff8f-138">Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-138">The following figure shows how this example renders.</span></span>  
  
 ![Temel tablo nasıl işlediğini gösteren ekran görüntüsü.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="bff8f-140">Tablo kapsama</span><span class="sxs-lookup"><span data-stu-id="bff8f-140">Table Containment</span></span>  
 <span data-ttu-id="bff8f-141"><xref:System.Windows.Documents.Table> öğesinden türetilen <xref:System.Windows.Documents.Block> öğesi için genel kurallar aynılarını ve <xref:System.Windows.Documents.Block> düzey öğeleri.</span><span class="sxs-lookup"><span data-stu-id="bff8f-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="bff8f-142">A <xref:System.Windows.Documents.Table> öğesi yer almalıdır herhangi aşağıdaki öğeleri biri:</span><span class="sxs-lookup"><span data-stu-id="bff8f-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="bff8f-143">Satır grupları</span><span class="sxs-lookup"><span data-stu-id="bff8f-143">Row Groupings</span></span>  
 <span data-ttu-id="bff8f-144"><xref:System.Windows.Documents.TableRowGroup> Öğesi rasgele bir tablo içindeki satırları grubu için bir yol sağlar; tablodaki her satır bir satır gruba ait olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="bff8f-145">Bir satır grubu içindeki satır genellikle ortak bir hedefi paylaşın ve bir grup olarak stillenmiş.</span><span class="sxs-lookup"><span data-stu-id="bff8f-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="bff8f-146">Bir satır gruplandırmalarına birincil içerik tablosu tarafından bulunan bir başlık, üstbilgi ve altbilgi satırlar gibi özel amaçlı satırları ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bff8f-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="bff8f-147">Aşağıdaki örnekte [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] stil uygulanmış üstbilgi ve altbilgi satırları içeren bir tablo tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="bff8f-147">The following example uses [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="bff8f-148">Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="bff8f-149">![Ekran: Tablo satır grupları](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="bff8f-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="bff8f-150">Arka plan işleme önceliği</span><span class="sxs-lookup"><span data-stu-id="bff8f-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="bff8f-151">Tablo öğelerini (z düzenini en düşükten yükseğe doğru) aşağıdaki sırayla işlenir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="bff8f-152">Bu sıra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="bff8f-152">This order cannot be changed.</span></span> <span data-ttu-id="bff8f-153">Örneğin, kurulan bu sıralamayı geçersiz kılmak için kullanabileceğiniz bu öğelerin "Z düzenini" özellik yok.</span><span class="sxs-lookup"><span data-stu-id="bff8f-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="bff8f-154">Bir tablo içinde bu öğelerin her biri için arka plan renkleri tanımlar aşağıdaki örneği inceleyin.</span><span class="sxs-lookup"><span data-stu-id="bff8f-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="bff8f-155">Aşağıdaki şekil, bu örneğin (yalnızca gösteren arka plan renkleri) nasıl işlediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="bff8f-156">![Ekran: Tablo z&#45;sipariş](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="bff8f-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="bff8f-157">Satırları veya sütunları yayma</span><span class="sxs-lookup"><span data-stu-id="bff8f-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="bff8f-158">Tablo hücreleri kullanarak birden çok satır veya sütuna yayılmasını yapılandırılabilir <xref:System.Windows.Documents.TableCell.RowSpan%2A> veya <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> öznitelikleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="bff8f-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="bff8f-159">Aşağıdaki örnekte, üç sütun, kapsayan bir hücre göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="bff8f-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="bff8f-160">Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="bff8f-161">![Ekran: Üç sütunu yayılan hücre](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="bff8f-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="bff8f-162">Kod içeren bir tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="bff8f-162">Building a Table With Code</span></span>  
 <span data-ttu-id="bff8f-163">Aşağıdaki örnekler program aracılığıyla nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Documents.Table> ve içerikle doldurur.</span><span class="sxs-lookup"><span data-stu-id="bff8f-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="bff8f-164">Tablosunun beş satır paylaştırıldı (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> bulunan nesneleri bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesi) ve altı sütunları (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> nesneleri).</span><span class="sxs-lookup"><span data-stu-id="bff8f-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="bff8f-165">Satırları tablonun tamamını ve tabloda veri sütunlarının açıklamak için bir üst bilgi satırı özet bilgileri içeren bir alt bilgi satırı başlık yönelik bir başlık satırı da dahil olmak üzere farklı sunu amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bff8f-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="bff8f-166">"Title", "header" ve "alt" satırları kavramı tabloya devralınan değildir; Bunlar, yalnızca satır farklı özelliklere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="bff8f-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="bff8f-167">Tablo hücreleri metinlerin, resimlerin veya her türlü diğer oluşan gerçek içeriği içeren [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesi.</span><span class="sxs-lookup"><span data-stu-id="bff8f-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="bff8f-168">İlk olarak, bir <xref:System.Windows.Documents.FlowDocument> oluşturulan konağa <xref:System.Windows.Documents.Table>ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve içeriği için eklenen <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="bff8f-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="bff8f-169">Ardından, altı <xref:System.Windows.Documents.TableColumn> nesnelerinin oluşturulduğu ve tablonun eklenen <xref:System.Windows.Documents.Table.Columns%2A> bazı biçimlendirme uygulanmış olan koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bff8f-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bff8f-170">Unutmayın tablo <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonun kullandığı standart sıfır tabanlı dizin.</span><span class="sxs-lookup"><span data-stu-id="bff8f-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="bff8f-171">Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanmış tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="bff8f-172">Tablodaki tüm altı sütunu kapsayan tek bir hücre içermesi için başlık satırı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="bff8f-173">Ardından, bir üst bilgi satırı oluşturulur ve tabloya eklenen ve üst bilgi satırı hücrelerde oluşturulur ve içeriği ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="bff8f-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="bff8f-174">Ardından, veriler için bir satır oluşturulur ve tabloya eklenen ve bu satırı hücrelerde oluşturulur ve içerikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="bff8f-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="bff8f-175">Bu satırı oluşturma üst bilgi satırı biraz farklı biçimlendirme uygulanmış oluşturmak için benzer.</span><span class="sxs-lookup"><span data-stu-id="bff8f-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="bff8f-176">Son olarak, bir alt bilgi satırı oluşturulan, eklenen biçimlendirilmiş ve.</span><span class="sxs-lookup"><span data-stu-id="bff8f-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="bff8f-177">Başlık satırı gibi tüm altı sütun kapsayan tek bir hücre alt bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="bff8f-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="bff8f-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bff8f-178">See also</span></span>

- [<span data-ttu-id="bff8f-179">Akış Belgesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bff8f-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="bff8f-180">XAML ile Tablo Tanımlama</span><span class="sxs-lookup"><span data-stu-id="bff8f-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="bff8f-181">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="bff8f-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="bff8f-182">Akış İçeriği Öğelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="bff8f-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
