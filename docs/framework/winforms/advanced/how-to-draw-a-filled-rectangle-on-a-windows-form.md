---
title: 'Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme'
description: Windows form 'da program aracılığıyla doldurulmuş bir dikdörtgen çizmeyi öğrenin. Ayrıca, kodunuzun derlenmesi hakkında bilgi edinin.
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
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621645"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="cd03d-104">Nasıl yapılır: Bir Windows Formunda Doldurulmuş Dikdörtgen Çizme</span><span class="sxs-lookup"><span data-stu-id="cd03d-104">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="cd03d-105">Bu örnek, bir form üzerinde doldurulmuş bir dikdörtgen çizer.</span><span class="sxs-lookup"><span data-stu-id="cd03d-105">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd03d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd03d-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd03d-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cd03d-107">Compiling the Code</span></span>  
 <span data-ttu-id="cd03d-108">Olay işleyicisinde bu yöntemi çağrılamaz <xref:System.Windows.Forms.Form.Load> .</span><span class="sxs-lookup"><span data-stu-id="cd03d-108">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="cd03d-109">Form başka bir form tarafından yeniden boyutlandırılmışsa veya gizlendiyse çizilen içerik yeniden çizilmez.</span><span class="sxs-lookup"><span data-stu-id="cd03d-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="cd03d-110">İçeriğinizi otomatik olarak yeniden çizmeyi sağlamak için yöntemini geçersiz kılmanız gerekir <xref:System.Windows.Forms.Control.OnPaint%2A> .</span><span class="sxs-lookup"><span data-stu-id="cd03d-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cd03d-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="cd03d-111">Robust Programming</span></span>  
 <span data-ttu-id="cd03d-112"><xref:System.IDisposable.Dispose%2A>Ve nesneleri gibi sistem kaynaklarını kullanan tüm nesneleri her zaman çağırmanız gerekir <xref:System.Drawing.Brush> <xref:System.Drawing.Graphics> .</span><span class="sxs-lookup"><span data-stu-id="cd03d-112">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd03d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd03d-113">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="cd03d-114">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="cd03d-114">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="cd03d-115">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="cd03d-115">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="cd03d-116">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="cd03d-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="cd03d-117">GDI+'da Fırçalar ve Dolgulu Şekiller</span><span class="sxs-lookup"><span data-stu-id="cd03d-117">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
