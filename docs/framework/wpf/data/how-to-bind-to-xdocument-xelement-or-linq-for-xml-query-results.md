---
title: "Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama"
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
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b39c45a7c85155a0fb46e8e176da5979e52e6e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="7c3ae-102">Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama</span><span class="sxs-lookup"><span data-stu-id="7c3ae-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="7c3ae-103">Bu örnek XML verinin nasıl bağlanacağını gösterir bir <xref:System.Windows.Controls.ItemsControl> kullanarak <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c3ae-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c3ae-104">Example</span></span>  
 <span data-ttu-id="7c3ae-105">Aşağıdaki XAML kodu tanımlayan bir <xref:System.Windows.Controls.ItemsControl> ve veri türü veri şablonu içerir `Planet` içinde `http://planetsNS` XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="7c3ae-106">Bir ad alanı kaplayan bir XML veri türü ayraçlar içinde ad içermelidir ve XAML biçimlendirme uzantısı göründüğü görünürse, bir küme parantezi kaçış sırası içeren ad gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="7c3ae-107">Bu kod karşılık dinamik özellikleri bağlar <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemlerinin <xref:System.Xml.Linq.XElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="7c3ae-108">Dinamik özellikler yöntemlerin adlarını paylaşan dinamik özellikleri bağlamak XAML etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="7c3ae-109">Daha fazla bilgi için bkz: [LINQ-XML dinamik özellikleri](/visualstudio/designers/linq-to-xml-dynamic-properties).</span><span class="sxs-lookup"><span data-stu-id="7c3ae-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="7c3ae-110">XML için varsayılan ad alanı bildiriminin nasıl öznitelik adları için geçerli değildir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="7c3ae-111">Aşağıdaki C# kod çağrıları <xref:System.Xml.Linq.XDocument.Load%2A> ve yığın paneli veri içeriğinin adlı öğesinin tüm alt öğeleri için ayarlar `SolarSystemPlanets` içinde `http://planetsNS` XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="7c3ae-112">XML verilerini kullanan XAML kaynağı olarak depolanabilir <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="7c3ae-113">Tam bir örnek için bkz: [L2DBForm.xaml kaynak kodu](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e).</span><span class="sxs-lookup"><span data-stu-id="7c3ae-113">For a complete example, see  [L2DBForm.xaml Source Code](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e).</span></span> <span data-ttu-id="7c3ae-114">Aşağıdaki örnek kod bir nesne kaynak veri bağlamı nasıl ayarlayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="7c3ae-115">Eşle dinamik özellikleri <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> XAML içinde esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="7c3ae-116">Kodunuzu XML sorgu için bir LINQ sonuçlarını de bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="7c3ae-117">Bu örnek öğe değeri tarafından istenen sorgu sonuçlarına bağlar.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="7c3ae-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c3ae-118">See Also</span></span>  
 [<span data-ttu-id="7c3ae-119">Bağlama kaynaklarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="7c3ae-119">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="7c3ae-120">WPF veri bağlama ile LINQ-XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="7c3ae-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [<span data-ttu-id="7c3ae-121">LINQ-XML örneği kullanarak WPF veri bağlama</span><span class="sxs-lookup"><span data-stu-id="7c3ae-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [<span data-ttu-id="7c3ae-122">LINQ-XML Dinamik Özellikler</span><span class="sxs-lookup"><span data-stu-id="7c3ae-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
