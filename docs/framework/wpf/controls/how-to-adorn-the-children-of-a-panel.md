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
ms.openlocfilehash: ae039243ded93eb2bc7f85f9f07fad1dbe0eac2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544984"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="5beea-102">Nasıl yapılır: Panelin Alt Öğelerini Donatma</span><span class="sxs-lookup"><span data-stu-id="5beea-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="5beea-103">Bu örnekte, program aracılığıyla belirli bir alt öğelere donatıcıyı bağlama işlemi gösterilmektedir <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="5beea-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5beea-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5beea-104">Example</span></span>  
 <span data-ttu-id="5beea-105">Alt öğeye bir donatıcı bağlama için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5beea-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5beea-106">Yeni bir <xref:System.Windows.Documents.AdornerLayer> nesne ve çağrı `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri olan donatılmış için öğeye bir donatıcı katmanı bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5beea-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="5beea-107">Çağrı ve üst öğenin alt öğelerini numaralandırın <xref:System.Windows.Documents.AdornerLayer.Add%2A> her alt öğeye bir donatıcı bağlama için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5beea-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="5beea-108">Aşağıdaki örnek SimpleCircleAdorner (yukarıda alt için gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="5beea-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="5beea-109">Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] başka bir öğeye bir donatıcı bağlamak için şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5beea-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5beea-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5beea-110">See also</span></span>
- [<span data-ttu-id="5beea-111">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5beea-111">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
