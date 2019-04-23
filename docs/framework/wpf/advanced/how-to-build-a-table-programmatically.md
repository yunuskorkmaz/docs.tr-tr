---
title: 'Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 315154b37218c0a6845f0a46149fc056780ee650
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172633"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="4b177-102">Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4b177-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="4b177-103">Aşağıdaki örnekler program aracılığıyla nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Documents.Table> ve içerikle doldurur.</span><span class="sxs-lookup"><span data-stu-id="4b177-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="4b177-104">Tablosunun beş satır paylaştırıldı (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> bulunan nesneleri bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesi) ve altı sütunları (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> nesneleri).</span><span class="sxs-lookup"><span data-stu-id="4b177-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="4b177-105">Satırları tablonun tamamını ve tabloda veri sütunlarının açıklamak için bir üst bilgi satırı özet bilgileri içeren bir alt bilgi satırı başlık yönelik bir başlık satırı da dahil olmak üzere farklı sunu amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4b177-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="4b177-106">"Title", "header" ve "alt" satırları kavramı tabloya devralınan değildir; Bunlar, yalnızca satır farklı özelliklere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="4b177-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="4b177-107">Tablo hücreleri metinlerin, resimlerin veya her türlü diğer oluşan gerçek içeriği içeren [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesi.</span><span class="sxs-lookup"><span data-stu-id="4b177-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b177-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b177-108">Example</span></span>  
 <span data-ttu-id="4b177-109">İlk olarak, bir <xref:System.Windows.Documents.FlowDocument> oluşturulan konağa <xref:System.Windows.Documents.Table>ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve içeriği için eklenen <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="4b177-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="4b177-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b177-110">Example</span></span>  
 <span data-ttu-id="4b177-111">Ardından, altı <xref:System.Windows.Documents.TableColumn> nesnelerinin oluşturulduğu ve tablonun eklenen <xref:System.Windows.Documents.Table.Columns%2A> bazı biçimlendirme uygulanmış olan koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4b177-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b177-112">Unutmayın tablo <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonun kullandığı standart sıfır tabanlı dizin.</span><span class="sxs-lookup"><span data-stu-id="4b177-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="4b177-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b177-113">Example</span></span>  
 <span data-ttu-id="4b177-114">Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanmış tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="4b177-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="4b177-115">Tablodaki tüm altı sütunu kapsayan tek bir hücre içermesi için başlık satırı gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4b177-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="4b177-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b177-116">Example</span></span>  
 <span data-ttu-id="4b177-117">Ardından, bir üst bilgi satırı oluşturulur ve tabloya eklenen ve üst bilgi satırı hücrelerde oluşturulur ve içeriği ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="4b177-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="4b177-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b177-118">Example</span></span>  
 <span data-ttu-id="4b177-119">Ardından, veriler için bir satır oluşturulur ve tabloya eklenen ve bu satırı hücrelerde oluşturulur ve içerikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="4b177-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="4b177-120">Bu satırı oluşturma üst bilgi satırı biraz farklı biçimlendirme uygulanmış oluşturmak için benzer.</span><span class="sxs-lookup"><span data-stu-id="4b177-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="4b177-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b177-121">Example</span></span>  
 <span data-ttu-id="4b177-122">Son olarak, bir alt bilgi satırı oluşturulan, eklenen biçimlendirilmiş ve.</span><span class="sxs-lookup"><span data-stu-id="4b177-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="4b177-123">Başlık satırı gibi tüm altı sütun kapsayan tek bir hücre alt bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4b177-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="4b177-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b177-124">See also</span></span>

- [<span data-ttu-id="4b177-125">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4b177-125">Table Overview</span></span>](table-overview.md)
