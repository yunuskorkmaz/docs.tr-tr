---
title: 'Nasıl yapılır: Bağlama Yönünü Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817916"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="2b1ee-102">Nasıl yapılır: Bağlamanın yönünü belirtin</span><span class="sxs-lookup"><span data-stu-id="2b1ee-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="2b1ee-103">Bu örnek, bağlamanın yalnızca bağlama hedefi (hedef) özelliğini, bağlama kaynağını (kaynak) özelliğini veya hem hedef özelliği hem de kaynak özelliğini güncelleştirip güncelleştirmediğini nasıl belirtmeyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b1ee-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b1ee-104">Example</span></span>  
 <span data-ttu-id="2b1ee-105">Bağlamanın yönünü belirtmek <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="2b1ee-106">Güncelleştirmeleri bağlamaya yönelik kullanılabilen seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2b1ee-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="2b1ee-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>Target özelliği ya da Source özelliği değiştiğinde Target özelliğini veya özelliğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="2b1ee-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>hedef özelliği yalnızca kaynak özelliği değiştiğinde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="2b1ee-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>hedef özelliği yalnızca uygulama başladığında veya <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişikliğe uğradığında güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="2b1ee-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>Target özelliği değiştiğinde kaynak özelliğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="2b1ee-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>hedef özelliğin varsayılan <xref:System.Windows.Data.Binding.Mode%2A> değerinin kullanılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="2b1ee-112">Daha fazla bilgi için bkz <xref:System.Windows.Data.BindingMode> . sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="2b1ee-113">Aşağıdaki örnekte, <xref:System.Windows.Data.Binding.Mode%2A> özelliğinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="2b1ee-114">Kaynak değişiklikleri (ve <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları için geçerlidir) algılamak için, kaynak gibi uygun bir özellik <xref:System.ComponentModel.INotifyPropertyChanged>değişikliği bildirim mekanizması gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="2b1ee-115">Bkz. bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulama örneği için [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) .</span><span class="sxs-lookup"><span data-stu-id="2b1ee-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="2b1ee-116"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Veya <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları<xref:System.Windows.Data.BindingMode.OneWayToSource> için, özelliği ayarlayarak kaynak güncelleştirmelerinin zamanlamasını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="2b1ee-117">Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b1ee-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b1ee-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="2b1ee-119">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2b1ee-119">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="2b1ee-120">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="2b1ee-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
