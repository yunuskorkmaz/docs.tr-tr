---
title: 'Nasıl yapılır: Bağlama Yönünü Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 4334ed178e7f2ed90928db6b434eb8c9fee77bf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206440"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="32b07-102">Nasıl yapılır: Bağlama Yönünü Belirtme</span><span class="sxs-lookup"><span data-stu-id="32b07-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="32b07-103">Bu örnek, bağlama yalnızca bağlama target (hedef) özelliği, bağlama (kaynak) kaynak özelliği veya hedef özelliği hem kaynak özelliği güncelleştirmeler olup olmadığını belirlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="32b07-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b07-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="32b07-104">Example</span></span>  
 <span data-ttu-id="32b07-105">Kullandığınız <xref:System.Windows.Data.Binding.Mode%2A> bağlama yönünü belirtme özelliği.</span><span class="sxs-lookup"><span data-stu-id="32b07-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="32b07-106">Aşağıdaki numaralandırma listesi bağlama güncelleştirmeleri için mevcut seçenekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="32b07-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="32b07-107"><xref:System.Windows.Data.BindingMode.TwoWay> hedef özelliği ya da kaynak özelliği değiştiğinde hedef özelliği veya özelliğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="32b07-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="32b07-108"><xref:System.Windows.Data.BindingMode.OneWay> yalnızca kaynak özelliği değiştiğinde hedef özelliğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="32b07-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="32b07-109"><xref:System.Windows.Data.BindingMode.OneTime> hedef özelliği yalnızca uygulama başladığında veya güncelleştirmeleri <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişiklik uygulanır.</span><span class="sxs-lookup"><span data-stu-id="32b07-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="32b07-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> Hedef özelliği değiştiğinde kaynak özelliğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="32b07-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="32b07-111"><xref:System.Windows.Data.BindingMode.Default> Varsayılan neden <xref:System.Windows.Data.Binding.Mode%2A> kullanılacak hedef özelliğinin değeri.</span><span class="sxs-lookup"><span data-stu-id="32b07-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="32b07-112">Daha fazla bilgi için <xref:System.Windows.Data.BindingMode> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="32b07-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="32b07-113">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Data.Binding.Mode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="32b07-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="32b07-114">Kaynak değişikliklerini algılamak için (uygulanabilir <xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları), kaynak gibi uygun bir değişiklik bildirimi mekanizması uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="32b07-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="32b07-115">Bkz: [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) örneği için bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="32b07-115">See [Implement Property Change Notification](how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="32b07-116">İçin <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları, kaynak güncelleştirmelerinin zamanlaması ayarlayarak denetleyebilirsiniz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="32b07-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="32b07-117">Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="32b07-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b07-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32b07-118">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="32b07-119">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="32b07-119">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="32b07-120">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="32b07-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
