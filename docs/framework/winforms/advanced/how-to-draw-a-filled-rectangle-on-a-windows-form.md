---
title: "Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme"
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
- cpp
f1_keywords: Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dce1a8d1070ed1d016da0c94c1f3ecc1ed9df389
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="6ee18-102">Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme</span><span class="sxs-lookup"><span data-stu-id="6ee18-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="6ee18-103">Bu örnek bir formunda doldurulmuş dikdörtgen çizer.</span><span class="sxs-lookup"><span data-stu-id="6ee18-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ee18-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ee18-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6ee18-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6ee18-105">Compiling the Code</span></span>  
 <span data-ttu-id="6ee18-106">Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="6ee18-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="6ee18-107">Formu yeniden boyutlandırılmış veya başka bir form tarafından getirilmemeli çizilmiş içeriği yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="6ee18-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="6ee18-108">İçeriğinizi otomatik olarak yeniden boyamak yapmak için geçersiz kılmalıdır <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6ee18-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6ee18-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6ee18-109">Robust Programming</span></span>  
 <span data-ttu-id="6ee18-110">Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> sistem kaynakları gibi kullanabilecek tüm nesneler üzerinde <xref:System.Drawing.Brush> ve <xref:System.Drawing.Graphics> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6ee18-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee18-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ee18-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.FillRectangle%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="6ee18-112">Grafik programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="6ee18-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="6ee18-113">Grafikler ve Windows Forms'ta çizme</span><span class="sxs-lookup"><span data-stu-id="6ee18-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="6ee18-114">Çizgiler ve şekiller çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="6ee18-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="6ee18-115">Fırçalar ve dolgulu şekiller GDI +'da</span><span class="sxs-lookup"><span data-stu-id="6ee18-115">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
