---
title: 'Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: e0653fbcb8eb052b12be7344ffe239431b67a951
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370988"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="fcb17-102">Nasıl yapılır: BetweenShowDelay Özelliğini Kullanma</span><span class="sxs-lookup"><span data-stu-id="fcb17-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="fcb17-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> zaman özelliğinin araç ipuçları hızlı bir şekilde görünür: çok az kayıpla veya hiç gecikmeyle — ne zaman bir kullanıcı hareket fare işaretçisi bir araç ipucu doğrudan diğerine.</span><span class="sxs-lookup"><span data-stu-id="fcb17-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcb17-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcb17-104">Example</span></span>  
 <span data-ttu-id="fcb17-105">Aşağıdaki örnekte, <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> özelliği, bir saniye (1000 milisaniye) için ayarlanır ve <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> araç ipuçları her ikisi için iki saniye (2000 milisaniye cinsinden) olarak ayarlanmış <xref:System.Windows.Shapes.Ellipse> denetimleri.</span><span class="sxs-lookup"><span data-stu-id="fcb17-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="fcb17-106">Üç nokta simgesini biri için araç ipucunu görüntülemek ve sonra fare işaretçisi için başka bir elips iki saniye içinde üzerine getirip bekletin, araç ipucu ikinci elipsin hemen görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fcb17-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="fcb17-107">Aşağıdaki senaryolardan birini <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> uygular, araç ipucu ikinci bir elipsin görünmeden önce bir saniye beklemeniz neden olur:</span><span class="sxs-lookup"><span data-stu-id="fcb17-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="fcb17-108">İkinci düğme iki saniyeden fazla ise taşımak için geçen süre.</span><span class="sxs-lookup"><span data-stu-id="fcb17-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="fcb17-109">Araç İpucu elips ilk zaman aralığının başlangıcında görünür değilse.</span><span class="sxs-lookup"><span data-stu-id="fcb17-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="fcb17-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcb17-110">See also</span></span>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="fcb17-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="fcb17-111">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="fcb17-112">Araç İpucuna Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fcb17-112">ToolTip Overview</span></span>](tooltip-overview.md)
