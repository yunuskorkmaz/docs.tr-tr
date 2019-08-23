---
title: 'Nasıl yapılır: Öğeye bir Donatıcı Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923490"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a><span data-ttu-id="2dccd-102">Nasıl yapılır: Öğeye bir Donatıcı Bağlama</span><span class="sxs-lookup"><span data-stu-id="2dccd-102">How to: Bind an Adorner to an Element</span></span>
<span data-ttu-id="2dccd-103">Bu örnekte, bir donatıcının programlı olarak belirtilen <xref:System.Windows.UIElement>bir şekilde nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2dccd-103">This example shows how to programmatically bind an adorner to a specified <xref:System.Windows.UIElement>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dccd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dccd-104">Example</span></span>  
 <span data-ttu-id="2dccd-105">Bir donatıcıyı belirli <xref:System.Windows.UIElement>bir nesneye bağlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2dccd-105">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1. <span data-ttu-id="2dccd-106">' Nin donatılacak bir <xref:System.Windows.Documents.AdornerLayer> nesne <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> <xref:System.Windows.UIElement> almak için yönteminiçağırın.`static`</span><span class="sxs-lookup"><span data-stu-id="2dccd-106">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="2dccd-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>görsel ağacı, belirtilen **UIElement**'den başlayıp, bulduğu ilk donatıcı katmanını geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2dccd-107"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified **UIElement**, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="2dccd-108">(Bir donatıcı katmanı bulunmazsa, yöntem null döndürür.)</span><span class="sxs-lookup"><span data-stu-id="2dccd-108">(If no adorner layers are found, the method returns null.)</span></span>  
  
2. <span data-ttu-id="2dccd-109">Donatıcıyı hedef **UIElement**'e bağlamak için yönteminiçağırın.<xref:System.Windows.Documents.AdornerLayer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="2dccd-109">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target **UIElement**.</span></span>  
  
 <span data-ttu-id="2dccd-110">Aşağıdaki örnek, bir SimpleCircleAdorner 'ı (yukarıda gösterilen) adlandırılmış bir <xref:System.Windows.Controls.TextBox> *myTextBox*öğesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="2dccd-110">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> <span data-ttu-id="2dccd-111">Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2dccd-111">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dccd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dccd-112">See also</span></span>

- [<span data-ttu-id="2dccd-113">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2dccd-113">Adorners Overview</span></span>](adorners-overview.md)
