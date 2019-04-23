---
title: "Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: afecb87dcfce1a8c48f1b2108edeae3cfd2aa16f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209664"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="197a6-102">Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama</span><span class="sxs-lookup"><span data-stu-id="197a6-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="197a6-103">Bu örnek XML verilerine bağlama yapmayı gösteren bir <xref:System.Windows.Controls.ItemsControl> kullanarak <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="197a6-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="197a6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="197a6-104">Example</span></span>  
 <span data-ttu-id="197a6-105">Aşağıdaki XAML kodu tanımlayan bir <xref:System.Windows.Controls.ItemsControl> ve veri türü için veri şablonu içerir `Planet` içinde `http://planetsNS` XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="197a6-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="197a6-106">Bir ad alanı kaplayan bir XML veri türü, küme ayraçları içine ad alanını içermeli ve bir XAML işaretleme uzantısı yeri görünebilir görüntülenirse, ad alanı ile bir küme ayracı kaçış sırası gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="197a6-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="197a6-107">Bu kod karşılık gelen dinamik özellikleri bağlar <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemlerinin <xref:System.Xml.Linq.XElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="197a6-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="197a6-108">Dinamik özellikler yöntemlerin adlarını paylaşan dinamik özellikleri bağlamak XAML etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="197a6-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="197a6-109">Daha fazla bilgi için bkz. [LINQ to XML dinamik özellikleri](/visualstudio/designers/linq-to-xml-dynamic-properties).</span><span class="sxs-lookup"><span data-stu-id="197a6-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="197a6-110">XML için varsayılan ad alanı bildiriminin nasıl öznitelik adları için geçerli değildir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="197a6-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="197a6-111">Aşağıdaki C# kod çağrıları <xref:System.Xml.Linq.XDocument.Load%2A> ve yığın paneli veri bağlamı adlı bir öğe tüm alt öğelerini ayarlar `SolarSystemPlanets` içinde `http://planetsNS` XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="197a6-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="197a6-112">XML verileri, XAML kullanarak kaynak olarak depolanabilir <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="197a6-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="197a6-113">Tam bir örnek için bkz. [L2DBForm.xaml kaynak kodu](/visualstudio/designers/l2dbform-xaml-source-code).</span><span class="sxs-lookup"><span data-stu-id="197a6-113">For a complete example, see  [L2DBForm.xaml source code](/visualstudio/designers/l2dbform-xaml-source-code).</span></span> <span data-ttu-id="197a6-114">Aşağıdaki örnek kod için bir nesne kaynak veri bağlamı nasıl ayarlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="197a6-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="197a6-115">Eşleyen dinamik Özellikler <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> XAML içinde esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="197a6-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="197a6-116">Kodunuz LINQ to XML sorgu sonuçları da bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="197a6-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="197a6-117">Bu örnekte öğe değeri tarafından istenen sorgu sonuçlarına bağlar.</span><span class="sxs-lookup"><span data-stu-id="197a6-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="197a6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="197a6-118">See also</span></span>

- [<span data-ttu-id="197a6-119">Bağlama Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="197a6-119">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="197a6-120">LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="197a6-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [<span data-ttu-id="197a6-121">LINQ to XML Kullanarak WPF Verilerini Bağlama Örneği</span><span class="sxs-lookup"><span data-stu-id="197a6-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [<span data-ttu-id="197a6-122">LINQ to XML Dinamik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="197a6-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
