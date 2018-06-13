---
title: 'Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 74f16935a496e4315038cc7c5ea37efef3e5f2f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544312"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="a4403-102">Nasıl yapılır: Program Aracılığıyla Tablo Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4403-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="a4403-103">Program aracılığıyla oluşturma Aşağıdaki örnekler bir <xref:System.Windows.Documents.Table> ve içeriği ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4403-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="a4403-104">Tablosunun içeriğini beş satıra paylaştırıldı (tarafından temsil edilen <xref:System.Windows.Documents.TableRow> içinde yer alan nesneler bir <xref:System.Windows.Documents.Table.RowGroups%2A> nesnesi) ve altı sütunlar (tarafından temsil edilen <xref:System.Windows.Documents.TableColumn> nesneleri).</span><span class="sxs-lookup"><span data-stu-id="a4403-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="a4403-105">Satırları tüm tablo, tablodaki veri sütunlarını açıklamak için bir başlık satırı ve Özet bilgiler ile altbilgi satırı başlık yönelik bir başlık satırı dahil olmak üzere, farklı sunu amaçlarıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4403-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="a4403-106">"Title", "üstbilgi" ve "Altbilgi" satır kavramı tabloya devralınmış değildir; Bunlar yalnızca satır farklı özelliklere sahip olan.</span><span class="sxs-lookup"><span data-stu-id="a4403-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="a4403-107">Tablo hücrelerini içeren metin, görüntüler veya neredeyse tüm diğer oluşan gerçek içeriği [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] öğesi.</span><span class="sxs-lookup"><span data-stu-id="a4403-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4403-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4403-108">Example</span></span>  
 <span data-ttu-id="a4403-109">İlk olarak, bir <xref:System.Windows.Documents.FlowDocument> oluşturulan ana bilgisayara <xref:System.Windows.Documents.Table>ve yeni bir <xref:System.Windows.Documents.Table> oluşturulur ve içeriğini eklenir <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="a4403-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="a4403-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4403-110">Example</span></span>  
 <span data-ttu-id="a4403-111">Ardından, altı <xref:System.Windows.Documents.TableColumn> nesneleri oluşturulur ve tablonun eklenen <xref:System.Windows.Documents.Table.Columns%2A> bazı uygulanan biçimlendirme içeren koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="a4403-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4403-112">Unutmayın tablonun <xref:System.Windows.Documents.Table.Columns%2A> koleksiyonu kullanan standart sıfır tabanlı dizin.</span><span class="sxs-lookup"><span data-stu-id="a4403-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="a4403-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4403-113">Example</span></span>  
 <span data-ttu-id="a4403-114">Ardından, bir başlık satırı oluşturulur ve bazı biçimlendirme uygulanmış tablosuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="a4403-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="a4403-115">Tablodaki tüm altı sütunu kapsayan tek bir hücre içermesi için başlık satırı olur.</span><span class="sxs-lookup"><span data-stu-id="a4403-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="a4403-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4403-116">Example</span></span>  
 <span data-ttu-id="a4403-117">Ardından, bir başlık satırı oluşturulur ve tabloya eklenir ve üstbilgi satırındaki hücreler oluşturulur ve içerik ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a4403-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="a4403-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4403-118">Example</span></span>  
 <span data-ttu-id="a4403-119">Ardından, veriler için bir satır oluşturulur ve tabloya eklenir ve bu satırda hücreler oluşturulur ve içerik ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a4403-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="a4403-120">Bu satırı oluşturmak uygulanan biraz farklı biçimlendirme ile üstbilgi satırını oluşturmakla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="a4403-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="a4403-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4403-121">Example</span></span>  
 <span data-ttu-id="a4403-122">Son olarak, bir altbilgi satırı oluşturulan, eklenen biçimlendirilmiş ve.</span><span class="sxs-lookup"><span data-stu-id="a4403-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="a4403-123">Başlık satırı gibi altbilgi tablodaki tüm altı sütunu kapsayan tek bir hücre içerir.</span><span class="sxs-lookup"><span data-stu-id="a4403-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="a4403-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4403-124">See Also</span></span>  
 [<span data-ttu-id="a4403-125">Tabloya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a4403-125">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
