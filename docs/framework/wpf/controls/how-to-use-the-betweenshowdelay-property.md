---
title: 'Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: 7d48fb859ec6d37abd2490bc718d58cbdaa67f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552720"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="72e97-102">Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma</span><span class="sxs-lookup"><span data-stu-id="72e97-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="72e97-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> araç ipuçları hızlı bir şekilde görünmesini sağlayacak şekilde zaman özelliğinin — çok az kayıpla veya hiç gecikmeyle — zaman kullanıcı hareket fare işaretçisini bir araç ipucu doğrudan diğerine.</span><span class="sxs-lookup"><span data-stu-id="72e97-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72e97-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="72e97-104">Example</span></span>  
 <span data-ttu-id="72e97-105">Aşağıdaki örnekte, <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> özelliği bir saniye (1000 milisaniye cinsinden) ayarlamak ve <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> hem araç ipuçları için iki saniye (2000 milisaniye) olarak ayarlanmış <xref:System.Windows.Shapes.Ellipse> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="72e97-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="72e97-106">Üç nokta birinin araç ipucunu görüntüleyebilirsiniz ve ardından fare işaretçisini başka bir elips iki saniye içinde üzerinde getirip bekletin, ikinci elipsin araç ipucuna hemen görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72e97-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="72e97-107">Aşağıdaki senaryolardan biri, <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> uygular, araç ipucu görünmeden önce bir saniye bekleyin ikinci elipsin neden olur:</span><span class="sxs-lookup"><span data-stu-id="72e97-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="72e97-108">İkinci düğme iki saniyeden fazla ise taşımak için geçen süre.</span><span class="sxs-lookup"><span data-stu-id="72e97-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="72e97-109">Araç İpucu ilk elipsin zaman aralığının başlangıcında görünür değilse.</span><span class="sxs-lookup"><span data-stu-id="72e97-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="72e97-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72e97-110">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="72e97-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="72e97-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="72e97-112">Araç İpucuna Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="72e97-112">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
