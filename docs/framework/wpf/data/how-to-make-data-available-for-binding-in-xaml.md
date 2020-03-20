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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174192"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="52aba-102">Nasıl yapılır: XAML'de Bağlama için Veriyi Kullanılabilir Yapma</span><span class="sxs-lookup"><span data-stu-id="52aba-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="52aba-103">Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]konu, uygulamanızın gereksinimlerine bağlı olarak, verileri bağlamak için kullanılabilir hale getirebileceğiniz çeşitli yolları tartışır.</span><span class="sxs-lookup"><span data-stu-id="52aba-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52aba-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="52aba-104">Example</span></span>  
 <span data-ttu-id="52aba-105">Bağlamak istediğiniz ortak bir dil çalışma zamanı (CLR) nesneniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]varsa, nesneyi bağlama için kullanılabilir hale getirmenin bir yolu, `x:Key`nesneyi kaynak olarak tanımlamak ve bir .</span><span class="sxs-lookup"><span data-stu-id="52aba-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="52aba-106">Aşağıdaki örnekte, dize `Person` özelliği ne adlandırılmış `PersonName`bir nesne var.</span><span class="sxs-lookup"><span data-stu-id="52aba-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="52aba-107">Nesne `Person` `<src>` (öğeyi içeren vurgulanan çizgide) adlı `SDKSample`ad alanında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="52aba-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="52aba-108">Daha sonra, <xref:System.Windows.Controls.TextBlock> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `<TextBlock>` öğeyi içeren vurgulanmış satırda olduğu gibi denetimi nesneye bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52aba-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="52aba-109">Alternatif olarak, aşağıdaki <xref:System.Windows.Data.ObjectDataProvider> örnekte olduğu gibi sınıfı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52aba-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="52aba-110">Öğeyi içeren vurgulanmış satır ın gösterdiği gibi, `<TextBlock>` bağlamayı aynı şekilde tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="52aba-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="52aba-111">Bu özel örnekte, sonuç aynıdır: metin <xref:System.Windows.Controls.TextBlock> içeriği `Joe`ile bir var.</span><span class="sxs-lookup"><span data-stu-id="52aba-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="52aba-112">Ancak, <xref:System.Windows.Data.ObjectDataProvider> sınıf bir yöntemin sonucuna bağlama yeteneği gibi işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="52aba-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="52aba-113">Sağladığı işlevselliğe ihtiyacınız <xref:System.Windows.Data.ObjectDataProvider> varsa sınıfı kullanmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52aba-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="52aba-114">Ancak, zaten oluşturulmuş bir nesneye bağlanınca, aşağıdaki örnekte olduğu gibi `DataContext` kodu ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="52aba-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="52aba-115">Sınıfı kullanarak bağlamak için XML verilerine <xref:System.Windows.Data.XmlDataProvider> erişmek için, [XMLDataProvider ve XPath Sorguları kullanarak XML Veri bind](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="52aba-115">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="52aba-116">Sınıfı kullanarak bağlamak için XML verilerine <xref:System.Windows.Data.ObjectDataProvider> erişmek için [XML Sorgu Sonuçları için XDocument, XElement veya LINQ'a](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)bağlan'a bakın.</span><span class="sxs-lookup"><span data-stu-id="52aba-116">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="52aba-117">Bağlandığınız verileri belirtmenin birçok yolu hakkında bilgi için [bkz.](how-to-specify-the-binding-source.md)</span><span class="sxs-lookup"><span data-stu-id="52aba-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="52aba-118">Bağlama için ne tür veri bağlayabilirsiniz veya kendi ortak dil çalışma zamanı (CLR) nesneleri nasıl uygulayacağınız hakkında bilgi [için](binding-sources-overview.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="52aba-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52aba-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52aba-119">See also</span></span>

- [<span data-ttu-id="52aba-120">Veri Bağlama Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="52aba-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="52aba-121">Nasıl Dır Konular</span><span class="sxs-lookup"><span data-stu-id="52aba-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
