---
title: "Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma"
description: Windows Presentation Foundation (WPF) uygulamasındaki uygulamanızın gereksinimlerine göre verileri kullanılabilir hale getirmek için kullanabileceğiniz çeşitli yollar bulun.
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620800"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="5a57a-103">Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="5a57a-103">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="5a57a-104">Bu konuda [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , uygulamanızın gereksinimlerine bağlı olarak verileri bağlama için kullanılabilir hale getirmek için kullanabileceğiniz çeşitli yollar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a57a-104">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a57a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a57a-105">Example</span></span>  
 <span data-ttu-id="5a57a-106">' Den bağlamak istediğiniz ortak dil çalışma zamanı (CLR) nesneniz varsa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , nesneyi bağlama için kullanılabilir hale getirmenin bir yolu kaynak olarak tanımlamak ve ona vermektir `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="5a57a-106">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="5a57a-107">Aşağıdaki örnekte, bir `Person` String özelliği adlı bir nesneniz vardır `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="5a57a-107">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="5a57a-108">`Person`Nesnesi (öğesi içeren vurgulanmış olan satırdaki `<src>` ) adlı ad alanında tanımlanır `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="5a57a-108">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="5a57a-109">Daha sonra <xref:System.Windows.Controls.TextBlock> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , öğeyi içeren vurgulanan çizgi gösterildiği gibi denetimi içindeki nesnesine bağlayabilirsiniz `<TextBlock>` .</span><span class="sxs-lookup"><span data-stu-id="5a57a-109">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="5a57a-110">Alternatif olarak, <xref:System.Windows.Data.ObjectDataProvider> Aşağıdaki örnekte olduğu gibi sınıfını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5a57a-110">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="5a57a-111">Bağlamayı, öğeyi içeren vurgulanmış çizgi ile aynı şekilde tanımlarsınız `<TextBlock>` .</span><span class="sxs-lookup"><span data-stu-id="5a57a-111">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="5a57a-112">Bu örnekte, sonuç aynıdır: metin içeriğine sahip olduğunuz bir <xref:System.Windows.Controls.TextBlock> `Joe` .</span><span class="sxs-lookup"><span data-stu-id="5a57a-112">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="5a57a-113">Ancak sınıfı, <xref:System.Windows.Data.ObjectDataProvider> bir yöntemin sonucuna bağlama özelliği gibi işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a57a-113">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="5a57a-114"><xref:System.Windows.Data.ObjectDataProvider>Sınıfının sağladığı işlevselliğe gereksinim duyuyorsanız, sınıfını kullanmayı tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5a57a-114">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="5a57a-115">Ancak, zaten oluşturulmuş bir nesneye bağlıyorsanız, `DataContext` Aşağıdaki örnekte olduğu gibi kodu olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a57a-115">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="5a57a-116">Sınıfını kullanarak bağlamak üzere XML verilerine erişmek için <xref:System.Windows.Data.XmlDataProvider> bkz. [XmlDataProvider ve XPath SORGULARıNı kullanarak XML verilerine bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="5a57a-116">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="5a57a-117">Sınıfını kullanarak bağlamak üzere XML verilerine erişmek için <xref:System.Windows.Data.ObjectDataProvider> bkz. [XML sorgu sonuçları için XDocument, XElement veya LINQ 'a bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="5a57a-117">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="5a57a-118">Bağladığınız verileri belirtebileceğiniz birçok yol hakkında daha fazla bilgi için bkz. [bağlama kaynağını belirtme](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="5a57a-118">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="5a57a-119">Bağlayacağınız veri türleri veya bağlama için kendi ortak dil çalışma zamanı (CLR) nesnelerinizi uygulama hakkında daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5a57a-119">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a57a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a57a-120">See also</span></span>

- [<span data-ttu-id="5a57a-121">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5a57a-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5a57a-122">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5a57a-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
