---
title: "Nasıl Yapılır: Açık Şekilleri Doldurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c020e5f7306e73ee97dff0b492b04b5a153059cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="98a67-102">Nasıl Yapılır: Açık Şekilleri Doldurma</span><span class="sxs-lookup"><span data-stu-id="98a67-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="98a67-103">Geçirerek bir yolu doldurabilir bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesinin <xref:System.Drawing.Graphics.FillPath%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98a67-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="98a67-104"><xref:System.Drawing.Graphics.FillPath%2A> Yöntemi yolunu ayarlanmış yolun dolgu modunu (alternatif veya sarma) göre doldurur.</span><span class="sxs-lookup"><span data-stu-id="98a67-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="98a67-105">Tüm açık şekilleri yol varsa, bu rakamları kapatılan gibi yolun girilir.</span><span class="sxs-lookup"><span data-stu-id="98a67-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="98a67-106">bir şekil, başlangıç noktası bitiş noktasından bir çizgide çizerek kapatır.</span><span class="sxs-lookup"><span data-stu-id="98a67-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98a67-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="98a67-107">Example</span></span>  
 <span data-ttu-id="98a67-108">Aşağıdaki örnek, bir açık şekli (yay) ve bir kapalı şekli (elips) sahip bir yol oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98a67-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="98a67-109"><xref:System.Drawing.Graphics.FillPath%2A> Yöntemi doldurur olan varsayılan doldurma modu göre yolu <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span><span class="sxs-lookup"><span data-stu-id="98a67-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="98a67-110">Aşağıdaki çizimde örnek kod çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98a67-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="98a67-111">Yolun girilir unutmayın (göre <xref:System.Drawing.Drawing2D.FillMode.Alternate>) sanki açık şekilde bir çizgide bitiş noktasından, başlangıç noktası tarafından kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="98a67-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="98a67-112">![Dolgu açma yolu](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="98a67-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98a67-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="98a67-113">Compiling the Code</span></span>  
 <span data-ttu-id="98a67-114">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="98a67-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a67-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98a67-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="98a67-116">GDI+'da Grafik Yolları</span><span class="sxs-lookup"><span data-stu-id="98a67-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
