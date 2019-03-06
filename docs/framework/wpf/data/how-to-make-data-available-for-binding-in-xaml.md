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
ms.openlocfilehash: 1f024ddd0be023f77408e3106bc0a4465d068074
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358294"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="2ab73-102">Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="2ab73-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="2ab73-103">Bu konuda çeşitli şekillerde yapabilirsiniz verileri için kullanılabilir bağlama anlatılmaktadır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], uygulamanızın ihtiyaçlarına bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="2ab73-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ab73-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ab73-104">Example</span></span>  
 <span data-ttu-id="2ab73-105">Varsa bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] gelen bağlamak istediğiniz nesne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yapabilirsiniz nesne kullanılabilir bir kaynak olarak tanımlayan ve bu bağlama için tek yolu bir `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="2ab73-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="2ab73-106">Aşağıdaki örnekte bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="2ab73-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="2ab73-107">`Person` Nesne (vurgulanan gösterilen satırda içeren `<src>` öğesi) adı verilen ad alanında tanımlanan `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="2ab73-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="2ab73-108">Ardından bağlayabilirsiniz <xref:System.Windows.Controls.TextBlock> denetimi nesneye [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vurgulanan satır gibi içeren `<TextBlock>` öğesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ab73-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="2ab73-109">Alternatif olarak, <xref:System.Windows.Data.ObjectDataProvider> aşağıdaki örnekteki gibi bir sınıfı:</span><span class="sxs-lookup"><span data-stu-id="2ab73-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="2ab73-110">Bağlama tanımlar içeren vurgulanan satırın aynı şekilde `<TextBlock>` öğesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ab73-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="2ab73-111">Bu örnekte sonuç aynıdır: sahip olduğunuz bir <xref:System.Windows.Controls.TextBlock> metin içerikli `Joe`.</span><span class="sxs-lookup"><span data-stu-id="2ab73-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="2ab73-112">Ancak, <xref:System.Windows.Data.ObjectDataProvider> sınıf özelliği bir yöntemin sonucu için bağlama gibi işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab73-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="2ab73-113">Kullanmayı da tercih edebilirsiniz <xref:System.Windows.Data.ObjectDataProvider> sağladığı işlevsellik gerekiyorsa sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2ab73-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="2ab73-114">Önceden oluşturulmuş bir nesne için bağlıyorsanız, ancak ayarlamanız gerekir `DataContext` kodda, aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="2ab73-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="2ab73-115">Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri bağlamasını kullanma <xref:System.Windows.Data.XmlDataProvider> sınıfı [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="2ab73-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="2ab73-116">Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri bağlamasını kullanma <xref:System.Windows.Data.ObjectDataProvider> sınıfı [XML sorgu sonuçları için XDocument, XElement veya LINQ'ya bağlama](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="2ab73-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="2ab73-117">Dosyalar bağladığınız veri birçok yolu hakkında bilgi için bkz. [bağlama kaynağı belirtme](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="2ab73-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="2ab73-118">Hangi veri türlerini adlarınıza bağlayabileceğiniz veya kendi uygulama hakkında bilgi için [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] bağlama nesnelerini görmek [bağlama kaynaklarına genel bakış](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2ab73-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab73-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab73-119">See also</span></span>
- [<span data-ttu-id="2ab73-120">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2ab73-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="2ab73-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="2ab73-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
