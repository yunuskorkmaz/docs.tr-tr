---
title: "Nasıl yapılır: Bir Gradyana Gama Düzeltmesi Uygulama"
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
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2721a45381f2d0befe82d6d0db2630f3eae08d51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="6aea0-102">Nasıl yapılır: Bir Gradyana Gama Düzeltmesi Uygulama</span><span class="sxs-lookup"><span data-stu-id="6aea0-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="6aea0-103">Gama düzeltme doğrusal gradyan fırçası için fırça ayarlayarak etkinleştirebilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="6aea0-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="6aea0-104">Ayarlayarak gama düzeltmesi devre dışı bırakabilirsiniz <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="6aea0-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="6aea0-105">Gama düzeltme varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="6aea0-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6aea0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6aea0-106">Example</span></span>  
 <span data-ttu-id="6aea0-107">Örnek doğrusal gradyan fırçası oluşturur ve o fırça iki dikdörtgen doldurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="6aea0-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="6aea0-108">İlk dikdörtgen gama düzeltmesi girilir ve İkinci dikdörtgeni gama düzeltmesi ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="6aea0-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="6aea0-109">Aşağıdaki çizimde iki doldurulmuş dikdörtgen gösterir.</span><span class="sxs-lookup"><span data-stu-id="6aea0-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="6aea0-110">Gama düzeltme yok, üst dikdörtgen ortadaki koyu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6aea0-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="6aea0-111">Gama düzeltme varsa, alt kısımdaki dikdörtgeni daha fazla Tekdüzen yoğunluğu olan görünüyor.</span><span class="sxs-lookup"><span data-stu-id="6aea0-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="6aea0-112">![Gradyan](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="6aea0-112">![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6aea0-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6aea0-113">Compiling the Code</span></span>  
 <span data-ttu-id="6aea0-114">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6aea0-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aea0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6aea0-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [<span data-ttu-id="6aea0-116">Şekilleri doldurmak için gradyan fırçası kullanma</span><span class="sxs-lookup"><span data-stu-id="6aea0-116">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
