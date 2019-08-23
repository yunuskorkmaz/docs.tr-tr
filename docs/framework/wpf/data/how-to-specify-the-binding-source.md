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
ms.openlocfilehash: 418dc77ce7638698d4850b06dafcea57787e1015
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959696"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="202c9-102">Nasıl yapılır: Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="202c9-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="202c9-103">Veri bağlamada bağlama kaynak nesnesi, verilerinizi elde ettiğiniz nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="202c9-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="202c9-104">Bu konuda, bağlama kaynağını belirtmenin farklı yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="202c9-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="202c9-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="202c9-105">Example</span></span>  
 <span data-ttu-id="202c9-106">Birkaç özelliği ortak bir kaynağa bağlıyorsanız, tüm veri bağlama özelliklerinin ortak bir kaynağı devraldığı bir `DataContext` kapsam oluşturmak için kullanışlı bir yol sağlayan özelliğini kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="202c9-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="202c9-107">Aşağıdaki örnekte, veri bağlamı uygulamanın kök öğesinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="202c9-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="202c9-108">Bu, tüm alt öğelerin bu veri bağlamını devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="202c9-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="202c9-109">Bağlama verisi, doğrudan eşleme yoluyla başvurulan ve kaynak `NetIncome` `incomeDataSource`anahtarı verilen özel bir veri sınıfından gelir.</span><span class="sxs-lookup"><span data-stu-id="202c9-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="202c9-110">Aşağıdaki örnek, `NetIncome` sınıfının tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="202c9-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> <span data-ttu-id="202c9-111">Yukarıdaki örnekte, biçimlendirme içindeki nesne başlatılır ve kaynak olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="202c9-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="202c9-112">Zaten kodda örneği oluşturulmuş bir nesneye bağlamak istiyorsanız, `DataContext` özelliği programlı olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="202c9-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="202c9-113">Bir örnek için bkz. [xaml 'de bağlama Için verileri kullanılabilir hale getirme](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="202c9-113">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="202c9-114">Alternatif olarak, tek tek Bağlamalarınızın kaynağını açıkça belirtmek isterseniz, aşağıdaki seçeneklere sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="202c9-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="202c9-115">Bu, devralınan veri bağlamına göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="202c9-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="202c9-116">Özellik</span><span class="sxs-lookup"><span data-stu-id="202c9-116">Property</span></span>|<span data-ttu-id="202c9-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="202c9-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="202c9-118">Kaynağı bir nesnenin örneğine ayarlamak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="202c9-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="202c9-119">Birçok özelliğin aynı veri bağlamını devraldığı bir kapsam oluşturma işlevselliğine ihtiyaç duymadıysanız özelliği yerine <xref:System.Windows.Data.Binding.Source%2A> `DataContext` özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="202c9-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="202c9-120">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="202c9-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="202c9-121">Bu, bağlama Hedefinizdeki konuma göre kaynağı belirtmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="202c9-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="202c9-122">Bu özelliği kullanabileceğiniz bazı yaygın senaryolar, öğenizin bir özelliğini aynı öğenin başka bir özelliğine bağlamak istediğinizde veya bir stil ya da şablonda bir bağlama tanımlıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="202c9-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="202c9-123">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="202c9-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="202c9-124">Bağlamak istediğiniz öğeyi temsil eden bir dize belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="202c9-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="202c9-125">Bu, uygulamanızdaki başka bir öğenin özelliğine bağlamak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="202c9-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="202c9-126">Örneğin, uygulamanızda başka bir <xref:System.Windows.Controls.Slider> denetimin yüksekliğini denetlemek için kullanmak istiyorsanız veya denetikinizi <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ListBox> denetikizin özelliğine bağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="202c9-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="202c9-127">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="202c9-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="202c9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="202c9-128">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="202c9-129">Özellik Değeri Devralma</span><span class="sxs-lookup"><span data-stu-id="202c9-129">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="202c9-130">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="202c9-130">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="202c9-131">Bağlama Bildirimlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="202c9-131">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="202c9-132">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="202c9-132">How-to Topics</span></span>](data-binding-how-to-topics.md)
