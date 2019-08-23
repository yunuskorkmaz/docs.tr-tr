---
title: 'Nasıl yapılır: Panelin Alt Öğelerini Donatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 739ccaa0273e66c4650c35217a1156d64336dbbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923520"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="bdba0-102">Nasıl yapılır: Panelin Alt Öğelerini Donatma</span><span class="sxs-lookup"><span data-stu-id="bdba0-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="bdba0-103">Bu örnekte, bir donatıcının, belirtilen <xref:System.Windows.Controls.Panel>bir alt öğeye programlı bir şekilde nasıl bağlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bdba0-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdba0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdba0-104">Example</span></span>  
 <span data-ttu-id="bdba0-105">Bir donatıcıyı a <xref:System.Windows.Controls.Panel>'nın alt öğelerine bağlamak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bdba0-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="bdba0-106">Yeni <xref:System.Windows.Documents.AdornerLayer> bir nesne bildirin ve alt öğeleri `static` donatılacak olan öğe için bir donatıcı katmanı bulmak üzere <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="bdba0-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="bdba0-107">Üst öğenin alt öğelerini numaralandırın ve her bir alt öğeye bir <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı bağlamak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="bdba0-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="bdba0-108">Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda gösterilen) <xref:System.Windows.Controls.StackPanel> adlı bir *myStackPanel*alt öğesine bağlar.</span><span class="sxs-lookup"><span data-stu-id="bdba0-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
> <span data-ttu-id="bdba0-109">Bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcıyı başka bir öğeye bağlamak için kullanılması şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="bdba0-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdba0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdba0-110">See also</span></span>

- [<span data-ttu-id="bdba0-111">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bdba0-111">Adorners Overview</span></span>](adorners-overview.md)
