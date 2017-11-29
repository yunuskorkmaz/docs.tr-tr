---
title: "Nasıl yapılır: Bağlama Kaynağı Belirtme"
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
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05f77e8939b9b81a9e3861df6a44bc3585a0a504
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="3b6a5-102">Nasıl yapılır: Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="3b6a5-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="3b6a5-103">Veri bağlama bağlama kaynak nesnesi verilerinizden elde ettiğiniz nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="3b6a5-104">Bu konuda bağlama kaynağını belirterek, farklı yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b6a5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b6a5-105">Example</span></span>  
 <span data-ttu-id="3b6a5-106">Ortak bir kaynağa çeşitli özellikler bağlıyorsanız, kullanmak istediğiniz `DataContext` tüm veri bağlama özellikleri devralındığı ortak bir kaynaktan kapsamı oluşturmak için kullanışlı bir yol sağlayan özelliği.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="3b6a5-107">Aşağıdaki örnekte, veri bağlamı uygulama kök öğe üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="3b6a5-108">Bu, veri bağlamı devralmak tüm alt öğeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="3b6a5-109">Veri bağlama için gelen bir özel veri sınıftan `NetIncome`, doğrudan bir eşleme aracılığıyla başvurulan ve kaynak anahtarı verilen `incomeDataSource`.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="3b6a5-110">Aşağıdaki örnek tanımını gösterir `NetIncome` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  <span data-ttu-id="3b6a5-111">Yukarıdaki örnek biçimlendirme nesnesinde oluşturur ve bir kaynak olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="3b6a5-112">Kodda bir zaten örneği bir nesneyi bağlamak istiyorsanız, ayarlamanız gerekir `DataContext` özelliği programlı olarak.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="3b6a5-113">Bir örnek için bkz: [veri kullanılabilir yap XAML'de bağlama için](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3b6a5-113">For an example, see [Make Data Available for Binding in XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="3b6a5-114">Alternatif olarak, kaynak belirtmek istiyorsanız, tek tek bağlantılarına açıkça aşağıdaki seçenekleriniz vardır.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="3b6a5-115">Bunlar devralınan veri bağlamı üzerinde önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="3b6a5-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="3b6a5-116">Property</span></span>|<span data-ttu-id="3b6a5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b6a5-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="3b6a5-118">Bir nesnenin örneğine kaynak ayarlamak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="3b6a5-119">Bir kapsamda oluşturma işlevselliğini gerekmiyorsa çeşitli özelliklerin aynı veri bağlamından devralınan, kullanabileceğiniz <xref:System.Windows.Data.Binding.Source%2A> özelliği yerine `DataContext` özelliği.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="3b6a5-120">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="3b6a5-121">Bağlamanın hedef olduğu göre kaynak belirtmek istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="3b6a5-122">Bu özellik burada kullanabilir bazı yaygın senaryolar, öğesinin bir özelliğini aynı öğenin başka bir özelliği Bağla istediğinizde veya bir bağlama stil veya şablonunda tanımlıyorsanız olur.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="3b6a5-123">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="3b6a5-124">Bağlamak istediğiniz öğeyi temsil eden bir dize belirtin.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="3b6a5-125">Bu, uygulamanızın üzerinde başka bir öğenin özelliği bağlamak istediğiniz durumunda faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="3b6a5-126">Kullanmak istiyorsanız, örneğin, bir <xref:System.Windows.Controls.Slider> , uygulamanızda başka bir denetimin yüksekliğini denetlemek için veya bağlamak istiyorsanız <xref:System.Windows.Controls.ContentControl.Content%2A> için denetiminizin <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> özelliği, <xref:System.Windows.Controls.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="3b6a5-127">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b6a5-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b6a5-128">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3b6a5-129">Özellik değeri devralma</span><span class="sxs-lookup"><span data-stu-id="3b6a5-129">Property Value Inheritance</span></span>](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)  
 [<span data-ttu-id="3b6a5-130">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="3b6a5-130">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="3b6a5-131">Bağlama bildirimleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="3b6a5-131">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="3b6a5-132">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="3b6a5-132">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
