---
title: 'Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: dfa0f9264247f7585c1743e40fd980906556efd0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454953"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="d34fc-102">Nasıl yapılır: Bağlama Güncelleştirmeleri Bildirimini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="d34fc-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="d34fc-103">Bu örnek, bağlama hedefi (hedef) veya bir bağlamanın bağlama kaynağı (kaynak) özelliği güncelleştirildikten sonra bildirim yapılacak şekilde nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d34fc-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d34fc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d34fc-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="d34fc-105">, bağlama kaynağı veya hedefi her güncelleştirildiği zaman bir veri güncelleştirme olayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="d34fc-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="d34fc-106">Bu olay, bağlantılı veriler değiştiğinden, güncelleştirilmesi gereken [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bilgilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d34fc-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="d34fc-107">Bu olayların çalışması ve aynı zamanda tek yönlü veya iki yönlü bağlamanın düzgün şekilde çalışması için, <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini kullanarak veri sınıfınızı uygulamanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d34fc-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="d34fc-108">Daha fazla bilgi için bkz. [özellik değişiklik bildirimini uygulama](how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="d34fc-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="d34fc-109"><xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> veya <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> özelliğini (ya da her ikisi) bağlamadaki `true` ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d34fc-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="d34fc-110">Bu olayı dinlemek için sağladığınız işleyicinin, değişiklikler hakkında bilgi almak istediğiniz öğeye doğrudan iliştirilmeli veya bağlamdaki herhangi bir şeyin değiştiği farkında olmak istiyorsanız genel veri bağlamına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d34fc-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="d34fc-111">Bir hedef özellik güncelleştirildiği zaman bildirim için ayarlamayı gösteren bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d34fc-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="d34fc-112">Daha sonra, olayı işlemek için bu örnekteki *OnTargetUpdated*\<t > temsilcisine göre bir işleyici atayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d34fc-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="d34fc-113">Olayın parametreleri, tek bir öğede birden fazla bağlı özellik olması halinde, değiştirilen Özellik (örneğin, tür veya aynı işleyici birden fazla öğeye eklenmişse) hakkındaki ayrıntıları belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d34fc-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d34fc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d34fc-114">See also</span></span>

- [<span data-ttu-id="d34fc-115">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d34fc-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="d34fc-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="d34fc-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
