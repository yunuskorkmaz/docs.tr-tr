---
title: "Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma"
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
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c342f0d635a9220a88a2af79c76e2c1580dee2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="01415-102">Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="01415-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="01415-103">Bu konuda yapabilirsiniz verileri için kullanılabilir bağlama farklı yolları açıklanmaktadır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], uygulamanızın gereksinimlerine bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="01415-103">This topic discusses the different ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01415-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="01415-104">Example</span></span>  
 <span data-ttu-id="01415-105">Varsa bir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] gelen bağlamak istediğiniz nesne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]yapabilirsiniz nesne kullanılabilir bir kaynak olarak tanımlamak ve buna vermek için bağlama için tek yolu bir `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="01415-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="01415-106">Aşağıdaki örnekte, sahip olduğunuz bir `Person` adlı bir dize özelliği nesnesiyle `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="01415-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="01415-107">`Person` Nesne adı verilen ad alanında tanımlanan `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="01415-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="01415-108">Nesne sonra bağlayabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="01415-108">You can then bind to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as shown in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="01415-109">Alternatif olarak, kullanabileceğiniz <xref:System.Windows.Data.ObjectDataProvider> aşağıdaki örnekteki gibi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01415-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 <span data-ttu-id="01415-110">Bağlama tanımladığınız aynı şekilde:</span><span class="sxs-lookup"><span data-stu-id="01415-110">You define the binding the same way:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="01415-111">Bu örnekte, sonuç aynıdır: elinizde bir <xref:System.Windows.Controls.TextBlock> metin içeriği ile `Joe`.</span><span class="sxs-lookup"><span data-stu-id="01415-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="01415-112">Ancak, <xref:System.Windows.Data.ObjectDataProvider> sınıfı, bir yöntemin sonucu bağlamak özelliği gibi işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="01415-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="01415-113">Kullanmayı tercih edebileceğiniz <xref:System.Windows.Data.ObjectDataProvider> sağladığı işlevselliğe gerekiyorsa sınıfı.</span><span class="sxs-lookup"><span data-stu-id="01415-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="01415-114">Önceden oluşturulmuş bir nesneye bağlıyorsanız, ancak ayarlamak gerekir `DataContext` kodda, aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="01415-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="01415-115">Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bağlama kullanmak için veri <xref:System.Windows.Data.XmlDataProvider> sınıfı için bkz: [XML verileri kullanarak bir XMLDataProvider ve XPath sorguları bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="01415-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="01415-116">Erişim için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] bağlama kullanmak için veri <xref:System.Windows.Data.ObjectDataProvider> sınıfı için bkz: [XDocument, XElement veya LINQ XML sorgu sonuçları için bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="01415-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="01415-117">Veri bağlama için farklı yollar hakkında bilgi için bkz [bağlama kaynak](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="01415-117">For information about the different ways you can specify the data you are binding to, see [Specify the Binding Source](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="01415-118">Hangi veri türlerini bağlayabileceğiniz veya kendi uygulama hakkında bilgi için [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneleri bağlama için bkz: [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="01415-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01415-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01415-119">See Also</span></span>  
 [<span data-ttu-id="01415-120">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="01415-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="01415-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="01415-121">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
