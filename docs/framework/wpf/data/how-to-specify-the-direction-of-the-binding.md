---
title: "Nasıl yapılır: Bağlama Yönünü Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9944ff214a9dfe12b21e005c4e1998c249bf72b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-direction-of-the-binding"></a><span data-ttu-id="1888b-102">Nasıl yapılır: Bağlama Yönünü Belirtme</span><span class="sxs-lookup"><span data-stu-id="1888b-102">How to: Specify the Direction of the Binding</span></span>
<span data-ttu-id="1888b-103">Bu örnek, bağlama yalnızca bağlama target (hedef) özelliği, bağlama kaynağı (kaynak) özelliğine veya hedef özelliği hem kaynak özelliği güncelleştirmeleri olup olmadığını belirlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1888b-103">This example shows how to specify whether the binding updates only the binding target (target) property, the binding source (source) property, or both the target property and the source property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1888b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1888b-104">Example</span></span>  
 <span data-ttu-id="1888b-105">Kullandığınız <xref:System.Windows.Data.Binding.Mode%2A> bağlama yönünü belirtmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="1888b-105">You use the <xref:System.Windows.Data.Binding.Mode%2A> property to specify the direction of the binding.</span></span> <span data-ttu-id="1888b-106">Aşağıdaki numaralandırma listesi bağlama güncelleştirmeleri için mevcut seçenekler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1888b-106">The following enumeration list shows the available options for binding updates:</span></span>  
  
-   <span data-ttu-id="1888b-107"><xref:System.Windows.Data.BindingMode.TwoWay>target özelliği ya da kaynak özelliği değiştiğinde hedef özelliği veya özelliği güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1888b-107"><xref:System.Windows.Data.BindingMode.TwoWay> updates the target property or the property whenever either the target property or the source property changes.</span></span>  
  
-   <span data-ttu-id="1888b-108"><xref:System.Windows.Data.BindingMode.OneWay>target özelliği, yalnızca kaynak özelliği değiştiğinde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1888b-108"><xref:System.Windows.Data.BindingMode.OneWay> updates the target property only when the source property changes.</span></span>  
  
-   <span data-ttu-id="1888b-109"><xref:System.Windows.Data.BindingMode.OneTime>target özelliği yalnızca uygulama başladığında veya güncelleştirmeleri <xref:System.Windows.FrameworkElement.DataContext%2A> bir değişikliğe uğradığında.</span><span class="sxs-lookup"><span data-stu-id="1888b-109"><xref:System.Windows.Data.BindingMode.OneTime> updates the target property only when the application starts or when the <xref:System.Windows.FrameworkElement.DataContext%2A> undergoes a change.</span></span>  
  
-   <span data-ttu-id="1888b-110"><xref:System.Windows.Data.BindingMode.OneWayToSource>hedef özelliği değiştiğinde kaynak özelliğini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1888b-110"><xref:System.Windows.Data.BindingMode.OneWayToSource> updates the source property when the target property changes.</span></span>  
  
-   <span data-ttu-id="1888b-111"><xref:System.Windows.Data.BindingMode.Default>Varsayılan neden <xref:System.Windows.Data.Binding.Mode%2A> kullanılacak hedef özelliğinin değeri.</span><span class="sxs-lookup"><span data-stu-id="1888b-111"><xref:System.Windows.Data.BindingMode.Default> causes the default <xref:System.Windows.Data.Binding.Mode%2A> value of target property to be used.</span></span>  
  
 <span data-ttu-id="1888b-112">Daha fazla bilgi için bkz: <xref:System.Windows.Data.BindingMode> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="1888b-112">For more information, see the <xref:System.Windows.Data.BindingMode> enumeration.</span></span>  
  
 <span data-ttu-id="1888b-113">Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.Data.Binding.Mode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1888b-113">The following example shows how to set the <xref:System.Windows.Data.Binding.Mode%2A> property.</span></span>  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 <span data-ttu-id="1888b-114">Kaynak değişikliklerini algılamak için (uygulanabilir <xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları), kaynak gibi uygun bir değişiklik bildirim mekanizması uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="1888b-114">To detect source changes (applicable to <xref:System.Windows.Data.BindingMode.OneWay> and <xref:System.Windows.Data.BindingMode.TwoWay> bindings), the source must implement a suitable property change notification mechanism such as <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span> <span data-ttu-id="1888b-115">Bkz: [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) ilişkin bir örnek bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1888b-115">See [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) for an example of an <xref:System.ComponentModel.INotifyPropertyChanged> implementation.</span></span>  
  
 <span data-ttu-id="1888b-116">İçin <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları ayarlayarak kaynak güncelleştirmelerinin zamanlamasını denetleyebilirsiniz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1888b-116">For <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings, you can control the timing of the source updates by setting the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property.</span></span> <span data-ttu-id="1888b-117">Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.</span><span class="sxs-lookup"><span data-stu-id="1888b-117">See <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1888b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1888b-118">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="1888b-119">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1888b-119">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="1888b-120">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="1888b-120">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
