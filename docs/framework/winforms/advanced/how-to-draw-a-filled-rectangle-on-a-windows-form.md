---
title: 'Nasıl yapılır: Bir Windows formunda doldurulmuş dikdörtgen çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: a9722b2939e77282453743a4dea165a340412a21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587040"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="1bb5e-102">Nasıl yapılır: Bir Windows formunda doldurulmuş dikdörtgen çizme</span><span class="sxs-lookup"><span data-stu-id="1bb5e-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="1bb5e-103">Bu örnek, bir form üzerinde doldurulmuş bir dikdörtgen çizer.</span><span class="sxs-lookup"><span data-stu-id="1bb5e-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bb5e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bb5e-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1bb5e-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1bb5e-105">Compiling the Code</span></span>  
 <span data-ttu-id="1bb5e-106">Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="1bb5e-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="1bb5e-107">Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="1bb5e-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="1bb5e-108">İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1bb5e-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1bb5e-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="1bb5e-109">Robust Programming</span></span>  
 <span data-ttu-id="1bb5e-110">Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> gibi sistem kaynaklarının kullanan herhangi bir nesne üzerinde <xref:System.Drawing.Brush> ve <xref:System.Drawing.Graphics> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1bb5e-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb5e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bb5e-111">See also</span></span>
- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="1bb5e-112">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="1bb5e-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="1bb5e-113">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="1bb5e-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1bb5e-114">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="1bb5e-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="1bb5e-115">GDI+'da Fırçalar ve Dolgulu Şekiller</span><span class="sxs-lookup"><span data-stu-id="1bb5e-115">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
