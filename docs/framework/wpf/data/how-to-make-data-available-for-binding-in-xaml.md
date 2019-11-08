---
title: "Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma"
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 97e878e4932ca9122bf27f76c32d1a56e69f253a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740597"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="3e001-102">Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="3e001-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="3e001-103">Bu konuda, uygulamanızın ihtiyaçlarına bağlı olarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]verileri bağlama için kullanılabilir hale getirmek için kullanabileceğiniz çeşitli yollar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e001-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e001-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e001-104">Example</span></span>  
 <span data-ttu-id="3e001-105">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bağlamak istediğiniz ortak dil çalışma zamanı (CLR) nesneniz varsa, nesneyi bağlama için kullanılabilir hale getirmenin bir yolu kaynak olarak tanımlamak ve buna bir `x:Key`vermektir.</span><span class="sxs-lookup"><span data-stu-id="3e001-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="3e001-106">Aşağıdaki örnekte, `PersonName`adlı dize özelliği olan bir `Person` nesneniz vardır.</span><span class="sxs-lookup"><span data-stu-id="3e001-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="3e001-107">`Person` nesnesi (`<src>` öğesini içeren vurgulanan satırdaki), `SDKSample`adlı ad alanında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e001-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="3e001-108">Daha sonra <xref:System.Windows.Controls.TextBlock> denetimini, `<TextBlock>` öğesi içeren vurgulanmış çizgi gibi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nesneye bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e001-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="3e001-109">Alternatif olarak, aşağıdaki örnekte olduğu gibi <xref:System.Windows.Data.ObjectDataProvider> sınıfını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e001-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="3e001-110">Bağlamayı, `<TextBlock>` öğesi içeren vurgulanmış çizgi ile aynı şekilde tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="3e001-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="3e001-111">Bu örnekte, sonuç aynıdır: metin içeriğine sahip bir <xref:System.Windows.Controls.TextBlock> `Joe`.</span><span class="sxs-lookup"><span data-stu-id="3e001-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="3e001-112">Ancak <xref:System.Windows.Data.ObjectDataProvider> sınıfı, bir yöntemin sonucuna bağlama özelliği gibi işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e001-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="3e001-113">Sağladığı işlevselliğe ihtiyacınız varsa <xref:System.Windows.Data.ObjectDataProvider> sınıfını kullanmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e001-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="3e001-114">Ancak, zaten oluşturulmuş bir nesneye bağlıyorsanız, aşağıdaki örnekte olduğu gibi koddaki `DataContext` ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e001-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="3e001-115"><xref:System.Windows.Data.XmlDataProvider> sınıfını kullanarak bağlamak üzere XML verilerine erişmek için bkz. [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="3e001-115">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="3e001-116"><xref:System.Windows.Data.ObjectDataProvider> sınıfını kullanarak bağlamak üzere XML verilerine erişmek için bkz. [XML sorgu sonuçları Için XDocument, XElement veya LINQ öğesine bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="3e001-116">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="3e001-117">Bağladığınız verileri belirtebileceğiniz birçok yol hakkında daha fazla bilgi için bkz. [bağlama kaynağını belirtme](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="3e001-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="3e001-118">Bağlayacağınız veri türleri veya bağlama için kendi ortak dil çalışma zamanı (CLR) nesnelerinizi uygulama hakkında daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e001-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e001-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e001-119">See also</span></span>

- [<span data-ttu-id="3e001-120">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e001-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3e001-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3e001-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
