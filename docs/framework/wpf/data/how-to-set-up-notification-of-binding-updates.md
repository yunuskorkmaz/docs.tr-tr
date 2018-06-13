---
title: 'Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 896ce103361590dceecccf8534fd330aabe18086
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555848"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="6ce7a-102">Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="6ce7a-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="6ce7a-103">Bu örnek, bağlama hedefinin (hedef) veya bir bağlama bağlama source (kaynak) özelliğini güncelleştirildiğinde bildirim almak için nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ce7a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ce7a-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="6ce7a-105"> Veri güncelleştirme her zaman bağlama kaynak veya hedef güncelleştirildi olayını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-105"> raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="6ce7a-106">Bu olay bildirmek için dahili olarak kullanılan [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ilişkili veri değiştiğinden, bu, güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="6ce7a-107">Bu olayların çalışmak ve ayrıca düzgün çalışması için tek veya çift yönlü bağlama, sınıf kullanarak verilerinizi uygulamak gerektiğini unutmayın <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="6ce7a-108">Daha fazla bilgi için bkz: [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="6ce7a-108">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="6ce7a-109">Ayarlama <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> veya <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> özelliği (veya her ikisi de) `true` bağlamada.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="6ce7a-110">Bağlamda herhangi bir şey değiştiğini unutmayın istiyorsanız, bu olay için dinleme sağlamak işleyicisine doğrudan değişikliklerden haberdar olmak istediğiniz öğe veya genel veri bağlamı bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="6ce7a-111">Burada, bildirim için bir hedef özellik güncelleştirildiği ayarlamak nasıl oluşturulduğunu gösteren bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="6ce7a-112">Ardından OnTargetUpdated, bağlı bir işleyici atayabilirsiniz\<T > temsilci, *EventHandler* olayını işlemek için bu örnekte:</span><span class="sxs-lookup"><span data-stu-id="6ce7a-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="6ce7a-113">Olay parametrelerinin (türü ya da aynı işleyici birden fazla öğeye bağlı olduğu belirli öğe gibi) değiştirilmiş özellik ayrıntılarını belirlemek için kullanılabilir olan tek bir öğede birden çok ilişkili özellikleri varsa yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce7a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ce7a-114">See Also</span></span>  
 [<span data-ttu-id="6ce7a-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6ce7a-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="6ce7a-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="6ce7a-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
