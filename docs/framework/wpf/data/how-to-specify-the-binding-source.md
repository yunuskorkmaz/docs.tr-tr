---
title: 'Nasıl yapılır: Bağlama Kaynağı Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 8c866502300c50e00f1393b9e3fb64099f027c43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931436"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="e32a5-102">Nasıl yapılır: Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="e32a5-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="e32a5-103">Veri bağlamasında bağlama kaynak nesnesi verilerinizden elde ettiğiniz nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="e32a5-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="e32a5-104">Bu konu, bağlama kaynağı belirtme farklı yollarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e32a5-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e32a5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e32a5-105">Example</span></span>  
 <span data-ttu-id="e32a5-106">Çeşitli özellikler için ortak bir kaynaktan bağlanıyorsanız, kullanmak istediğiniz `DataContext` tüm veri bağlı özelliklerinin içinde ortak bir kaynaktan devralındığı bir kapsamı'kurmak için kullanışlı bir yol sağlayan bir özellik.</span><span class="sxs-lookup"><span data-stu-id="e32a5-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="e32a5-107">Aşağıdaki örnekte, uygulamanın kök öğe üzerinde veri bağlamı kuruldu.</span><span class="sxs-lookup"><span data-stu-id="e32a5-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="e32a5-108">Bu, söz konusu veri bağlamı devralan tüm alt öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e32a5-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="e32a5-109">Veri bağlama için gelen bir özel veri sınıftan `NetIncome`, doğrudan bir eşlemesi aracılığıyla başvurulan ve kaynak anahtarı verilen `incomeDataSource`.</span><span class="sxs-lookup"><span data-stu-id="e32a5-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="e32a5-110">Aşağıdaki örnek tanımı gösterilmektedir `NetIncome` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e32a5-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  <span data-ttu-id="e32a5-111">Yukarıdaki örnek biçimlendirmede nesnesini başlatır ve bir kaynak olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="e32a5-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="e32a5-112">Ayarlamak gereken kodu zaten oluşturulmuş bir nesneyi bağlamak istiyorsanız, `DataContext` özelliğini program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="e32a5-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="e32a5-113">Bir örnek için bkz. [olun veri kullanılabilir için XAML bağlamasında](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="e32a5-113">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="e32a5-114">Alternatif olarak, kaynak belirtmek istiyorsanız, ayrı ayrı oturumdaki bağlamalarda açıkça aşağıdaki seçenekleriniz vardır.</span><span class="sxs-lookup"><span data-stu-id="e32a5-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="e32a5-115">Bunlar devralınan veri bağlamından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="e32a5-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="e32a5-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="e32a5-116">Property</span></span>|<span data-ttu-id="e32a5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e32a5-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="e32a5-118">Bir nesnenin örneğine kaynağı ayarlamak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e32a5-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="e32a5-119">Bir kapsamda oluşturma işlevselliğini gerekmiyorsa çeşitli özelliklerin aynı veri bağlamını devralır, kullanabileceğiniz <xref:System.Windows.Data.Binding.Source%2A> özelliği yerine `DataContext` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e32a5-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="e32a5-120">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="e32a5-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="e32a5-121">Bu, bağlama hedefi olduğu göre kaynak belirtmek istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e32a5-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="e32a5-122">Burada, bu özelliği kullanabilirsiniz bazı yaygın senaryolar öğenizin bir özellik aynı öğenin başka bir özelliğine bağlamak istediğinizde veya bir bağlama bir stil veya şablonun içinde tanımlıyorsanız olur.</span><span class="sxs-lookup"><span data-stu-id="e32a5-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="e32a5-123">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="e32a5-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="e32a5-124">Bağlamak istediğiniz öğeyi temsil eden bir dize belirtin.</span><span class="sxs-lookup"><span data-stu-id="e32a5-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="e32a5-125">Uygulamanızdaki başka bir öğenin özelliğe bağlamak istediğinizde bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e32a5-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="e32a5-126">Örneğin kullanmak istiyorsanız, bir <xref:System.Windows.Controls.Slider> uygulamanızın başka bir denetimin yüksekliği denetlemek için veya bağlamak istiyorsanız <xref:System.Windows.Controls.ContentControl.Content%2A> denetiminizin için <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği, <xref:System.Windows.Controls.ListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e32a5-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="e32a5-127">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="e32a5-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e32a5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e32a5-128">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e32a5-129">Özellik Değeri Devralma</span><span class="sxs-lookup"><span data-stu-id="e32a5-129">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="e32a5-130">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e32a5-130">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="e32a5-131">Bağlama Bildirimlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e32a5-131">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="e32a5-132">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e32a5-132">How-to Topics</span></span>](data-binding-how-to-topics.md)
