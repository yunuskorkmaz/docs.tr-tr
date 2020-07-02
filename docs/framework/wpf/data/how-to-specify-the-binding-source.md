---
title: 'Nasıl yapılır: Bağlama Kaynağı Belirtme'
description: Windows Presentation Foundation (WPF) içinde bu örnek aracılığıyla bağlama kaynağını belirtmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 02f27da007ebe8c5985f91b83adfba7d3d00219a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621671"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="92db0-103">Nasıl yapılır: Bağlama Kaynağı Belirtme</span><span class="sxs-lookup"><span data-stu-id="92db0-103">How to: Specify the Binding Source</span></span>
<span data-ttu-id="92db0-104">Veri bağlamada bağlama kaynak nesnesi, verilerinizi elde ettiğiniz nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="92db0-104">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="92db0-105">Bu konuda, bağlama kaynağını belirtmenin farklı yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92db0-105">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92db0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="92db0-106">Example</span></span>  
 <span data-ttu-id="92db0-107">Birkaç özelliği ortak bir kaynağa bağlıyorsanız, `DataContext` tüm veri bağlama özelliklerinin ortak bir kaynağı devraldığı bir kapsam oluşturmak için kullanışlı bir yol sağlayan özelliğini kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="92db0-107">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="92db0-108">Aşağıdaki örnekte, veri bağlamı uygulamanın kök öğesinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="92db0-108">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="92db0-109">Bu, tüm alt öğelerin bu veri bağlamını devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="92db0-109">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="92db0-110">Bağlama verisi, `NetIncome` doğrudan eşleme yoluyla başvurulan ve kaynak anahtarı verilen özel bir veri sınıfından gelir `incomeDataSource` .</span><span class="sxs-lookup"><span data-stu-id="92db0-110">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="92db0-111">Aşağıdaki örnek, sınıfının tanımını gösterir `NetIncome` .</span><span class="sxs-lookup"><span data-stu-id="92db0-111">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> <span data-ttu-id="92db0-112">Yukarıdaki örnekte, biçimlendirme içindeki nesne başlatılır ve kaynak olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92db0-112">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="92db0-113">Zaten kodda örneği oluşturulmuş bir nesneye bağlamak istiyorsanız, `DataContext` özelliği programlı olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="92db0-113">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="92db0-114">Bir örnek için bkz. [xaml 'de bağlama Için verileri kullanılabilir hale getirme](how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="92db0-114">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="92db0-115">Alternatif olarak, tek tek Bağlamalarınızın kaynağını açıkça belirtmek isterseniz, aşağıdaki seçeneklere sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="92db0-115">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="92db0-116">Bu, devralınan veri bağlamına göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="92db0-116">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="92db0-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="92db0-117">Property</span></span>|<span data-ttu-id="92db0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92db0-118">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="92db0-119">Kaynağı bir nesnenin örneğine ayarlamak için bu özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="92db0-119">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="92db0-120">Birçok özelliğin aynı veri bağlamını devraldığı bir kapsam oluşturma işlevselliğine ihtiyaç duymadıysanız özelliği <xref:System.Windows.Data.Binding.Source%2A> yerine özelliğini kullanabilirsiniz `DataContext` .</span><span class="sxs-lookup"><span data-stu-id="92db0-120">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="92db0-121">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="92db0-121">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="92db0-122">Bu, bağlama Hedefinizdeki konuma göre kaynağı belirtmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="92db0-122">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="92db0-123">Bu özelliği kullanabileceğiniz bazı yaygın senaryolar, öğenizin bir özelliğini aynı öğenin başka bir özelliğine bağlamak istediğinizde veya bir stil ya da şablonda bir bağlama tanımlıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="92db0-123">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="92db0-124">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="92db0-124">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="92db0-125">Bağlamak istediğiniz öğeyi temsil eden bir dize belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92db0-125">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="92db0-126">Bu, uygulamanızdaki başka bir öğenin özelliğine bağlamak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="92db0-126">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="92db0-127">Örneğin, <xref:System.Windows.Controls.Slider> uygulamanızda başka bir denetimin yüksekliğini denetlemek için kullanmak istiyorsanız veya <xref:System.Windows.Controls.ContentControl.Content%2A> denetikinizi <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> denetikizin özelliğine bağlamak istiyorsanız <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="92db0-127">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="92db0-128">Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="92db0-128">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92db0-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92db0-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="92db0-130">Özellik Değeri Kalıtımı</span><span class="sxs-lookup"><span data-stu-id="92db0-130">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="92db0-131">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92db0-131">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="92db0-132">Bağlama Bildirimlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92db0-132">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="92db0-133">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="92db0-133">How-to Topics</span></span>](data-binding-how-to-topics.md)
