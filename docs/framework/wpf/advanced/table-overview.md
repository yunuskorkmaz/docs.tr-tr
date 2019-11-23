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
# <a name="table-overview"></a><span data-ttu-id="9ecaa-102">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9ecaa-102">Table Overview</span></span>
<span data-ttu-id="9ecaa-103"><xref:System.Windows.Documents.Table>, akış belge içeriğinin Kılavuz tabanlı sunumunu destekleyen bir blok düzeyi öğesidir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-103"><xref:System.Windows.Documents.Table> is a block level element that supports grid-based presentation of Flow document content.</span></span> <span data-ttu-id="9ecaa-104">Bu öğenin esnekliği çok yararlı hale gelir, ancak doğru şekilde anlaşılması ve kullanılması daha karmaşık hale gelir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-104">The flexibility of this element makes it very useful, but also makes it more complicated to understand and use correctly.</span></span>  
  
 <span data-ttu-id="9ecaa-105">Bu konuda aşağıdaki bölümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-105">This topic contains the following sections.</span></span>  
  
- [<span data-ttu-id="9ecaa-106">Tablo Temelleri</span><span class="sxs-lookup"><span data-stu-id="9ecaa-106">Table Basics</span></span>](#table_basics)  
  
- [<span data-ttu-id="9ecaa-107">Tablo nasıl farklı olur?</span><span class="sxs-lookup"><span data-stu-id="9ecaa-107">How is Table Different then Grid?</span></span>](#table_vs_Grid)  
  
- [<span data-ttu-id="9ecaa-108">Temel tablo yapısı</span><span class="sxs-lookup"><span data-stu-id="9ecaa-108">Basic Table Structure</span></span>](#basic_table_structure)  
  
- [<span data-ttu-id="9ecaa-109">Tablo kapsama</span><span class="sxs-lookup"><span data-stu-id="9ecaa-109">Table Containment</span></span>](#table_containment)  
  
- [<span data-ttu-id="9ecaa-110">Satır gruplandırmaları</span><span class="sxs-lookup"><span data-stu-id="9ecaa-110">Row Groupings</span></span>](#row_groupings)  
  
- [<span data-ttu-id="9ecaa-111">Arka plan Işleme önceliği</span><span class="sxs-lookup"><span data-stu-id="9ecaa-111">Background Rendering Precedence</span></span>](#rendering_precedence)  
  
- [<span data-ttu-id="9ecaa-112">Satırları veya sütunları yayma</span><span class="sxs-lookup"><span data-stu-id="9ecaa-112">Spanning Rows or Columns</span></span>](#spanning_rows_or_columns)  
  
- [<span data-ttu-id="9ecaa-113">Kodla tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ecaa-113">Building a Table With Code</span></span>](#building_a_table_with_code)  
  
- <span data-ttu-id="9ecaa-114">[İlgili konular]</span><span class="sxs-lookup"><span data-stu-id="9ecaa-114">[Related Topics]</span></span> 
  
<a name="table_basics"></a>   
## <a name="table-basics"></a><span data-ttu-id="9ecaa-115">Tablo Temelleri</span><span class="sxs-lookup"><span data-stu-id="9ecaa-115">Table Basics</span></span>  
  
<a name="table_vs_Grid"></a>   
### <a name="how-is-table-different-then-grid"></a><span data-ttu-id="9ecaa-116">Tablo nasıl farklı olur?</span><span class="sxs-lookup"><span data-stu-id="9ecaa-116">How is Table Different then Grid?</span></span>  
 <span data-ttu-id="9ecaa-117"><xref:System.Windows.Documents.Table> ve <xref:System.Windows.Controls.Grid> bazı yaygın işlevleri paylaşır, ancak her biri farklı senaryolar için idealdir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-117"><xref:System.Windows.Documents.Table> and <xref:System.Windows.Controls.Grid> share some common functionality, but each is best suited for different scenarios.</span></span> <span data-ttu-id="9ecaa-118">Bir <xref:System.Windows.Documents.Table> akış içeriği içinde kullanılmak üzere tasarlanmıştır (akış içeriği hakkında daha fazla bilgi için bkz. [akış belgesine genel bakış](flow-document-overview.md) ).</span><span class="sxs-lookup"><span data-stu-id="9ecaa-118">A <xref:System.Windows.Documents.Table> is designed for use within flow content (see [Flow Document Overview](flow-document-overview.md) for more information on flow content).</span></span> <span data-ttu-id="9ecaa-119">Kılavuzlar, formların içinde en iyi şekilde kullanılır (temel olarak, akış içeriğinin dışında herhangi bir yerde).</span><span class="sxs-lookup"><span data-stu-id="9ecaa-119">Grids are best used inside of forms (basically anywhere outside of flow content).</span></span> <span data-ttu-id="9ecaa-120">Bir <xref:System.Windows.Documents.FlowDocument>içinde, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Controls.Grid> olmadığı sürece sayfalandırma, sütun yeniden akışı ve içerik seçimi gibi akış içeriği davranışlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-120">Within a <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> supports flow content behaviors like pagination, column reflow, and content selection while a <xref:System.Windows.Controls.Grid> does not.</span></span> <span data-ttu-id="9ecaa-121">Diğer taraftan bir <xref:System.Windows.Controls.Grid>, bir dizi ve sütun dizinine göre <xref:System.Windows.Controls.Grid> öğe ekleyen bir <xref:System.Windows.Documents.FlowDocument> dışında en iyi şekilde kullanılır <xref:System.Windows.Documents.Table> değildir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-121">A <xref:System.Windows.Controls.Grid> on the other hand is best used outside of a <xref:System.Windows.Documents.FlowDocument> for many reasons including <xref:System.Windows.Controls.Grid> adds elements based on a row and column index, <xref:System.Windows.Documents.Table> does not.</span></span> <span data-ttu-id="9ecaa-122"><xref:System.Windows.Controls.Grid> öğesi, alt içeriğin katmanlanışını sağlar ve tek bir "hücresinde" birden fazla öğenin var olmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-122">The <xref:System.Windows.Controls.Grid> element allows layering of child content, allowing more than one element to exist within a single "cell."</span></span> <span data-ttu-id="9ecaa-123"><xref:System.Windows.Documents.Table> katmanlanın desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-123"><xref:System.Windows.Documents.Table> does not support layering.</span></span> <span data-ttu-id="9ecaa-124">Bir <xref:System.Windows.Controls.Grid> alt öğeleri, "hücre" sınırlarının alanına göre mutlak olarak konumlandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-124">Child elements of a <xref:System.Windows.Controls.Grid> can be absolutely positioned relative to the area of their "cell" boundaries.</span></span> <span data-ttu-id="9ecaa-125"><xref:System.Windows.Documents.Table> bu özelliği desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-125"><xref:System.Windows.Documents.Table> does not support this feature.</span></span> <span data-ttu-id="9ecaa-126">Son olarak, bir <xref:System.Windows.Controls.Grid> daha az kaynak gerektirir <xref:System.Windows.Documents.Table> daha sonra performansı artırmak için <xref:System.Windows.Controls.Grid> kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-126">Finally, a <xref:System.Windows.Controls.Grid> requires less resources then a <xref:System.Windows.Documents.Table> so consider using a <xref:System.Windows.Controls.Grid> to improve performance.</span></span>  
  
<a name="basic_table_structure"></a>   
### <a name="basic-table-structure"></a><span data-ttu-id="9ecaa-127">Temel tablo yapısı</span><span class="sxs-lookup"><span data-stu-id="9ecaa-127">Basic Table Structure</span></span>  
 <span data-ttu-id="9ecaa-128"><xref:System.Windows.Documents.Table> sütunları (<xref:System.Windows.Documents.TableColumn> öğeleri tarafından temsil edilen) ve satırları (<xref:System.Windows.Documents.TableRow> öğeleri tarafından gösterilen) içeren kılavuza dayalı bir sunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-128"><xref:System.Windows.Documents.Table> provides a grid-based presentation consisting of columns (represented by <xref:System.Windows.Documents.TableColumn> elements) and rows (represented by <xref:System.Windows.Documents.TableRow> elements).</span></span> <span data-ttu-id="9ecaa-129"><xref:System.Windows.Documents.TableColumn> öğeler içerik barındırmaz; yalnızca sütunların sütunlarını ve özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-129"><xref:System.Windows.Documents.TableColumn> elements do not host content; they simply define columns and characteristics of columns.</span></span> <span data-ttu-id="9ecaa-130"><xref:System.Windows.Documents.TableRow> öğeler, tablo için bir satır gruplandırması tanımlayan bir <xref:System.Windows.Documents.TableRowGroup> öğesinde barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-130"><xref:System.Windows.Documents.TableRow> elements must be hosted in a <xref:System.Windows.Documents.TableRowGroup> element, which defines a grouping of rows for the table.</span></span> <span data-ttu-id="9ecaa-131">tablo tarafından sunulacak gerçek içeriği içeren <xref:System.Windows.Documents.TableCell> öğeleri, bir <xref:System.Windows.Documents.TableRow> öğesinde barındırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-131"><xref:System.Windows.Documents.TableCell> elements, which contain the actual content to be presented by the table, must be hosted in a <xref:System.Windows.Documents.TableRow> element.</span></span> <span data-ttu-id="9ecaa-132"><xref:System.Windows.Documents.TableCell>, yalnızca <xref:System.Windows.Documents.Block>türetilen öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-132"><xref:System.Windows.Documents.TableCell> may only contain elements that derive from <xref:System.Windows.Documents.Block>.</span></span>  <span data-ttu-id="9ecaa-133">Bir <xref:System.Windows.Documents.TableCell> için geçerli alt öğeler içerir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-133">Valid child elements for a <xref:System.Windows.Documents.TableCell> include.</span></span>  
  
- <xref:System.Windows.Documents.BlockUIContainer>  
  
- <xref:System.Windows.Documents.List>  
  
- <xref:System.Windows.Documents.Paragraph>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Table>  
  
> [!NOTE]
> <span data-ttu-id="9ecaa-134"><xref:System.Windows.Documents.TableCell> öğeler metin içeriğini doğrudan barındırmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-134"><xref:System.Windows.Documents.TableCell> elements may not directly host text content.</span></span> <span data-ttu-id="9ecaa-135"><xref:System.Windows.Documents.TableCell>gibi akış içeriği öğelerinin kapsama kuralları hakkında daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9ecaa-135">For more information about the containment rules for flow content elements like <xref:System.Windows.Documents.TableCell>, see [Flow Document Overview](flow-document-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ecaa-136"><xref:System.Windows.Documents.Table>, <xref:System.Windows.Controls.Grid> öğesi ile benzerdir, ancak daha fazla özelliğe sahiptir ve bu nedenle daha fazla kaynak yükü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-136"><xref:System.Windows.Documents.Table> is similar to the <xref:System.Windows.Controls.Grid> element but has more capabilities and, therefore, requires greater resource overhead.</span></span>  
  
 <span data-ttu-id="9ecaa-137">Aşağıdaki örnekte, XAML ile basit bir 2 x 3 tablosu tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-137">The following example defines a simple 2 x 3 table with XAML.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_BasicLayout](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_basiclayout)]  
  
 <span data-ttu-id="9ecaa-138">Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-138">The following figure shows how this example renders.</span></span>  
  
 ![Temel bir tablonun nasıl işlediğini gösteren ekran görüntüsü.](./media/table-overview/basic-table-render-example.png)  
  
<a name="table_containment"></a>   
### <a name="table-containment"></a><span data-ttu-id="9ecaa-140">Tablo kapsama</span><span class="sxs-lookup"><span data-stu-id="9ecaa-140">Table Containment</span></span>  
 <span data-ttu-id="9ecaa-141"><xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.Block> öğeden türetilir ve <xref:System.Windows.Documents.Block> Level öğeleri için ortak kurallara uyar.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-141"><xref:System.Windows.Documents.Table> derives from the <xref:System.Windows.Documents.Block> element, and adheres to the common rules for <xref:System.Windows.Documents.Block> level elements.</span></span>  <span data-ttu-id="9ecaa-142">Bir <xref:System.Windows.Documents.Table> öğesi aşağıdaki öğelerden herhangi biri tarafından içerilmeyebilir:</span><span class="sxs-lookup"><span data-stu-id="9ecaa-142">A <xref:System.Windows.Documents.Table> element may be contained by any of the following elements:</span></span>  
  
- <xref:System.Windows.Documents.FlowDocument>  
  
- <xref:System.Windows.Documents.TableCell>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Documents.Section>  
  
- <xref:System.Windows.Documents.Floater>  
  
- <xref:System.Windows.Documents.Figure>  
  
<a name="row_groupings"></a>   
### <a name="row-groupings"></a><span data-ttu-id="9ecaa-143">Satır gruplandırmaları</span><span class="sxs-lookup"><span data-stu-id="9ecaa-143">Row Groupings</span></span>  
 <span data-ttu-id="9ecaa-144"><xref:System.Windows.Documents.TableRowGroup> öğesi tablo içindeki satırları rastgele gruplamak için bir yol sağlar; bir tablodaki her satır bir satır gruplandırmasına ait olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-144">The <xref:System.Windows.Documents.TableRowGroup> element provides a way to arbitrarily group rows within a table; every row in a table must belong to a row grouping.</span></span>  <span data-ttu-id="9ecaa-145">Satır grubu içindeki satırlar genellikle ortak bir amacı paylaşır ve bir grup olarak Stillenebilir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-145">Rows within a row group often share a common intent, and may be styled as a group.</span></span>  <span data-ttu-id="9ecaa-146">Satır gruplandırmaları için ortak bir kullanım, tablo tarafından içerilen birincil içerikten bir başlık, üstbilgi ve altbilgi satırları gibi özel amaçlı satırları ayıramaktır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-146">A common use for row groupings is to separate special-purpose rows, such as a title, header, and footer rows, from the primary content contained by the table.</span></span>  
  
 <span data-ttu-id="9ecaa-147">Aşağıdaki örnek, stilli üstbilgi ve altbilgi satırları içeren bir tablo tanımlamak için XAML kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-147">The following example uses XAML to define a table with styled header and footer rows.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_RowGroups](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_rowgroups)]  
  
 <span data-ttu-id="9ecaa-148">Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-148">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="9ecaa-149">![Ekran görüntüsü: tablo satır grupları](./media/table-rowgroups.png "Table_RowGroups")</span><span class="sxs-lookup"><span data-stu-id="9ecaa-149">![Screenshot: Table row groups](./media/table-rowgroups.png "Table_RowGroups")</span></span>  
  
<a name="rendering_precedence"></a>   
### <a name="background-rendering-precedence"></a><span data-ttu-id="9ecaa-150">Arka plan Işleme önceliği</span><span class="sxs-lookup"><span data-stu-id="9ecaa-150">Background Rendering Precedence</span></span>  
 <span data-ttu-id="9ecaa-151">Tablo öğeleri aşağıdaki sırada (z-Order küçükten en büyüğe) işlenir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-151">Table elements render in the following order (z-order from lowest to highest).</span></span> <span data-ttu-id="9ecaa-152">Bu sıra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-152">This order cannot be changed.</span></span> <span data-ttu-id="9ecaa-153">Örneğin, bu öğeler için, bu belirlenen sırayı geçersiz kılmak için kullanabileceğiniz "Z-Order" özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-153">For example, there is no "Z-order" property for these elements that you can use to override this established order.</span></span>  
  
1. <xref:System.Windows.Documents.Table>  
  
2. <xref:System.Windows.Documents.TableColumn>  
  
3. <xref:System.Windows.Documents.TableRowGroup>  
  
4. <xref:System.Windows.Documents.TableRow>  
  
5. <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="9ecaa-154">Bir tablo içindeki bu öğelerin her biri için arka plan renklerini tanımlayan aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-154">Consider the following example, which defines background colors for each of these elements within a table.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ZOrder](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_zorder)]  
  
 <span data-ttu-id="9ecaa-155">Aşağıdaki şekil, bu örneğin nasıl işlediğini gösterir (yalnızca arka plan renklerini gösterir).</span><span class="sxs-lookup"><span data-stu-id="9ecaa-155">The following figure shows how this example renders (showing background colors only).</span></span>  
  
 <span data-ttu-id="9ecaa-156">![Ekran görüntüsü: tablo&#45;z sırası](./media/table-zorder.png "Table_ZOrder")</span><span class="sxs-lookup"><span data-stu-id="9ecaa-156">![Screenshot: Table z&#45;order](./media/table-zorder.png "Table_ZOrder")</span></span>  
  
<a name="spanning_rows_or_columns"></a>   
### <a name="spanning-rows-or-columns"></a><span data-ttu-id="9ecaa-157">Satırları veya sütunları yayma</span><span class="sxs-lookup"><span data-stu-id="9ecaa-157">Spanning Rows or Columns</span></span>  
 <span data-ttu-id="9ecaa-158">Tablo hücreleri, sırasıyla <xref:System.Windows.Documents.TableCell.RowSpan%2A> veya <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> öznitelikleri kullanılarak birden çok satır veya sütunu kapsayacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-158">Table cells may be configured to span multiple rows or columns by using the <xref:System.Windows.Documents.TableCell.RowSpan%2A> or <xref:System.Windows.Documents.TableCell.ColumnSpan%2A> attributes, respectively.</span></span>  
  
 <span data-ttu-id="9ecaa-159">Bir hücrenin üç sütuna yaydığı aşağıdaki örneği göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-159">Consider the following example, in which a cell spans three columns.</span></span>  
  
 [!code-xaml[TableSnippets2#_Table_ColumnSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml#_table_columnspan)]  
  
 <span data-ttu-id="9ecaa-160">Aşağıdaki şekilde, bu örneğin nasıl işlediğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-160">The following figure shows how this example renders.</span></span>  
  
 <span data-ttu-id="9ecaa-161">![Ekran görüntüsü: üç sütunun hepsini kapsayan hücre](./media/table-columnspan.png "Table_ColumnSpan")</span><span class="sxs-lookup"><span data-stu-id="9ecaa-161">![Screenshot: Cell spanning all three columns](./media/table-columnspan.png "Table_ColumnSpan")</span></span>  
  
<a name="building_a_table_with_code"></a>   
## <a name="building-a-table-with-code"></a><span data-ttu-id="9ecaa-162">Kodla tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ecaa-162">Building a Table With Code</span></span>  
 <span data-ttu-id="9ecaa-163">Aşağıdaki örneklerde, programlı olarak bir <xref:System.Windows.Documents.Table> oluşturma ve içerikle doldurma işlemlerinin nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-163">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="9ecaa-164">Tablonun içerikleri, beş satıra (bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesinde bulunan <xref:System.Windows.Documents.TableRow> nesneleri tarafından temsil edilir) ve altı sütun (<xref:System.Windows.Documents.TableColumn> nesneleri tarafından temsil edilir) olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-164">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="9ecaa-165">Satırlar, tablonun tamamına başlık eklemek amaçlanan bir başlık satırı, tablodaki verilerin sütunlarını tanımlayacak bir başlık satırı ve Özet bilgileri içeren bir altbilgi satırı gibi farklı sunum amaçları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-165">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="9ecaa-166">"Title", "Header" ve "Footer" satırları kavramı tabloya ait değildir; Bunlar yalnızca farklı özelliklere sahip olan satırlardır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-166">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="9ecaa-167">Tablo hücreleri, metin, resim veya neredeyse tüm diğer [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğelerden oluşan gerçek içeriği içerir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-167">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
 <span data-ttu-id="9ecaa-168">İlk olarak, <xref:System.Windows.Documents.Table>barındırmak için bir <xref:System.Windows.Documents.FlowDocument> oluşturulur ve <xref:System.Windows.Documents.FlowDocument>içeriğine yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve eklenir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-168">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
 <span data-ttu-id="9ecaa-169">Sonra, altı <xref:System.Windows.Documents.TableColumn> nesne oluşturulur ve tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonuna eklenir, bazı biçimlendirmeler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-169">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ecaa-170">Tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonunun standart sıfır tabanlı dizin oluşturmayı kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-170">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
 <span data-ttu-id="9ecaa-171">Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirmeler uygulanmış tabloya eklenir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-171">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="9ecaa-172">Başlık satırı, tablodaki altı sütunu kapsayan tek bir hücre içeriyor olur.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-172">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
 <span data-ttu-id="9ecaa-173">Ardından, başlık satırı oluşturulur ve tabloya eklenir ve üst bilgi satırındaki hücreler oluşturulur ve içerikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-173">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
 <span data-ttu-id="9ecaa-174">Daha sonra, veriler için bir satır oluşturulur ve tabloya eklenir ve bu satırdaki hücreler oluşturulur ve içerikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-174">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="9ecaa-175">Bu satırı oluşturmak, biraz farklı biçimlendirme uygulanmış olan üst bilgi satırını oluşturmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-175">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
 <span data-ttu-id="9ecaa-176">Son olarak, bir altbilgi satırı oluşturulur, eklenir ve biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-176">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="9ecaa-177">Başlık satırı gibi, alt bilgi, tablodaki altı sütunu kapsayan tek bir hücre içerir.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-177">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="9ecaa-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ecaa-178">See also</span></span>

- [<span data-ttu-id="9ecaa-179">Akış Belgesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9ecaa-179">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="9ecaa-180">XAML ile Tablo Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9ecaa-180">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="9ecaa-181">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="9ecaa-181">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="9ecaa-182">Akış İçeriği Öğelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="9ecaa-182">Use Flow Content Elements</span></span>](how-to-use-flow-content-elements.md)
