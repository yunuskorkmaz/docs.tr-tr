---
title: 'Nasıl yapılır: Yüklü bir Olayı İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: 6f3520fc3bc2a64d76083af415588ff819890eb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544202"
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="378bb-102">Nasıl yapılır: Yüklü bir Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="378bb-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="378bb-103">Bu örnek nasıl işleneceğini gösterir <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> olay ve olayın işlenmesi için uygun bir senaryoyu.</span><span class="sxs-lookup"><span data-stu-id="378bb-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="378bb-104">İşleyici oluşturur bir <xref:System.Windows.Controls.Button> Sayfa yüklediğinde.</span><span class="sxs-lookup"><span data-stu-id="378bb-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="378bb-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="378bb-105">Example</span></span>  
 <span data-ttu-id="378bb-106">Aşağıdaki örnek kullanır [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir arka plan kod dosyası ile birlikte.</span><span class="sxs-lookup"><span data-stu-id="378bb-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="378bb-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="378bb-107">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 [<span data-ttu-id="378bb-108">Nesne Yaşam Süresi Olayları</span><span class="sxs-lookup"><span data-stu-id="378bb-108">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [<span data-ttu-id="378bb-109">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="378bb-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="378bb-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="378bb-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
