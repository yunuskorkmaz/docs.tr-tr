---
title: 'Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 9c9061d3c4d6b3de5e1ab42a6b98c20813835ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964154"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="3b6f9-102">Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b6f9-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="3b6f9-103">Aşağıdaki örneklerde, programlama yoluyla nasıl bir <xref:System.Windows.Documents.Table> oluşturma ve içerikle doldurma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="3b6f9-104">Tablonun içerikleri beş satıra (bir <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.Table.RowGroups%2A> nesnede bulunan nesnelerle gösterilir) ve altı sütuna (nesnelere göre <xref:System.Windows.Documents.TableColumn> gösterilen) dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="3b6f9-105">Satırlar, tablonun tamamına başlık eklemek amaçlanan bir başlık satırı, tablodaki verilerin sütunlarını tanımlayacak bir başlık satırı ve Özet bilgileri içeren bir altbilgi satırı gibi farklı sunum amaçları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="3b6f9-106">"Title", "Header" ve "Footer" satırları kavramı tabloya ait değildir; Bunlar yalnızca farklı özelliklere sahip olan satırlardır.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="3b6f9-107">Tablo hücreleri, metin, resim veya neredeyse herhangi bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğeden oluşan gerçek içeriği içerir.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b6f9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6f9-108">Example</span></span>  
 <span data-ttu-id="3b6f9-109">İlk olarak, <xref:System.Windows.Documents.FlowDocument> bir <xref:System.Windows.Documents.Table>barındırmak için oluşturulur ve yeni <xref:System.Windows.Documents.Table> bir <xref:System.Windows.Documents.FlowDocument>oluşturulur ve içeriğine eklenir.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="3b6f9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6f9-110">Example</span></span>  
 <span data-ttu-id="3b6f9-111">Sonra, altı <xref:System.Windows.Documents.TableColumn> nesne oluşturulur ve <xref:System.Windows.Documents.Table.Columns%2A> tablonun koleksiyonuna eklenir, bazı biçimlendirmeler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b6f9-112">Tablo <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonunun standart sıfır tabanlı dizin oluşturmayı kullandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="3b6f9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6f9-113">Example</span></span>  
 <span data-ttu-id="3b6f9-114">Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirmeler uygulanmış tabloya eklenir.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="3b6f9-115">Başlık satırı, tablodaki altı sütunu kapsayan tek bir hücre içeriyor olur.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="3b6f9-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6f9-116">Example</span></span>  
 <span data-ttu-id="3b6f9-117">Ardından, başlık satırı oluşturulur ve tabloya eklenir ve üst bilgi satırındaki hücreler oluşturulur ve içerikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="3b6f9-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6f9-118">Example</span></span>  
 <span data-ttu-id="3b6f9-119">Daha sonra, veriler için bir satır oluşturulur ve tabloya eklenir ve bu satırdaki hücreler oluşturulur ve içerikle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="3b6f9-120">Bu satırı oluşturmak, biraz farklı biçimlendirme uygulanmış olan üst bilgi satırını oluşturmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="3b6f9-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6f9-121">Example</span></span>  
 <span data-ttu-id="3b6f9-122">Son olarak, bir altbilgi satırı oluşturulur, eklenir ve biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="3b6f9-123">Başlık satırı gibi, alt bilgi, tablodaki altı sütunu kapsayan tek bir hücre içerir.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="3b6f9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b6f9-124">See also</span></span>

- [<span data-ttu-id="3b6f9-125">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b6f9-125">Table Overview</span></span>](table-overview.md)
