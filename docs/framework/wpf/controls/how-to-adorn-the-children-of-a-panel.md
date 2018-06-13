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
ms.openlocfilehash: 4babbf1df57f340a3f6be218f213ad1c868ec9f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550225"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="9bc2e-102">Nasıl yapılır: Panelin Alt Öğelerini Donatma</span><span class="sxs-lookup"><span data-stu-id="9bc2e-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="9bc2e-103">Bu örnek belirtilen bir alt öğeleri için bir donatıcıyı programlı olarak bağlamak nasıl gösterir <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc2e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9bc2e-104">Example</span></span>  
 <span data-ttu-id="9bc2e-105">Alt öğelerinin donatıcı bağlamak için bir <xref:System.Windows.Controls.Panel>, şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9bc2e-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9bc2e-106">Yeni bir bildirme <xref:System.Windows.Documents.AdornerLayer> nesne ve çağrı `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> alt öğeleri olan donatılacak öğe için donatıcı katmanı bulmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="9bc2e-107">Çağrı ve üst öğenin alt öğeleri listeleme <xref:System.Windows.Documents.AdornerLayer.Add%2A> donatıcı her alt öğeye bağlamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="9bc2e-108">Aşağıdaki örnek bir SimpleCircleAdorner (yukarıda alt öğelerinin gösterilen) bağlanır bir <xref:System.Windows.Controls.StackPanel> adlı *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  <span data-ttu-id="9bc2e-109">Kullanarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] donatıcı başka bir öğeye bağlamak için şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc2e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bc2e-110">See Also</span></span>  
 [<span data-ttu-id="9bc2e-111">Donatıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9bc2e-111">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
