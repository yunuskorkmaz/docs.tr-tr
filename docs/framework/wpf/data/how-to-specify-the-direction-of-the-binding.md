---
title: 'Nasıl yapılır: Bağlama Yönünü Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 8f7d843382ee3409047d7cf9549267d582883984
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459097"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="f849b-102">Nasıl yapılır: bağlamanın yönünü belirtme</span><span class="sxs-lookup"><span data-stu-id="f849b-102">How to: Specify the direction of the binding</span></span>

<span data-ttu-id="f849b-103">Bu örnek, bağlamanın yalnızca bağlama hedefi (hedef) özelliğini, bağlama kaynağını (kaynak) özelliğini veya hem hedef özelliği hem de kaynak özelliğini güncelleştirip güncelleştirmediğini nasıl belirtmeyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f849b-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f849b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f849b-104">Example</span></span>  
 <span data-ttu-id="f849b-105">Bağlamanın yönünü belirtmek için <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f849b-105">You use the <xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType> property to specify the direction of the binding.</span></span> <span data-ttu-id="f849b-106">Güncelleştirmeleri bağlamaya yönelik kullanılabilen seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f849b-106">The following are the available options for binding updates:</span></span>  
  
- <span data-ttu-id="f849b-107">hedef özellik veya kaynak özelliği değiştiğinde <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> hedef özelliği ya da özelliğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f849b-107"><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
- <span data-ttu-id="f849b-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>, hedef özelliği yalnızca kaynak özelliği değiştiğinde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f849b-108"><xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType> updates the target property only when the source property changes.</span></span>  
  
- <span data-ttu-id="f849b-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>, hedef özelliği yalnızca uygulama başladığında veya <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişikliğe uğradığında güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="f849b-109"><xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
- <span data-ttu-id="f849b-110">hedef özelliği değiştiğinde, kaynak özelliğini güncelleştirir <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f849b-110"><xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType> updates the source property when the target property changes.</span></span>  
  
- <span data-ttu-id="f849b-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>, hedef özelliğin varsayılan <xref:System.Windows.Data.Binding.Mode%2A> değerinin kullanılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f849b-111"><xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="f849b-112">Daha fazla bilgi için <xref:System.Windows.Data.BindingMode> sabit listesine bakın.</span><span class="sxs-lookup"><span data-stu-id="f849b-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="f849b-113">Aşağıdaki örnekte <xref:System.Windows.Data.Binding.Mode%2A> özelliğinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f849b-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="f849b-114">Kaynak değişikliklerini (<xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları için geçerlidir) algılamak için, kaynağın <xref:System.ComponentModel.INotifyPropertyChanged>gibi uygun bir özellik değişim bildirimi mekanizması uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f849b-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="f849b-115">Bkz. <xref:System.ComponentModel.INotifyPropertyChanged> bir uygulama örneği için [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) .</span><span class="sxs-lookup"><span data-stu-id="f849b-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="f849b-116"><xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları için <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliğini ayarlayarak kaynak güncelleştirmelerinin zamanlamasını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f849b-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="f849b-117">Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="f849b-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f849b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f849b-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="f849b-119">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f849b-119">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f849b-120">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f849b-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
