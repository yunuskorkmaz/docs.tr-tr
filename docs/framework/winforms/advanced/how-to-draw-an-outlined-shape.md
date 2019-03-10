---
title: 'Nasıl yapılır: Anahatlı şekil çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.DrawEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- drawing [Windows Forms], shapes
- circular shapes
- forms [Windows Forms], drawing circular shapes
- circles
- outlined shapes [Windows Forms], examples
- outlined shapes [Windows Forms], drawing
- drawing [Windows Forms], circular shapes
- shapes [Windows Forms], drawing
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
ms.openlocfilehash: 598706b381d12b8e820747ca872146bdb5e300c7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722639"
---
# <a name="how-to-draw-an-outlined-shape"></a><span data-ttu-id="36e36-102">Nasıl yapılır: Anahatlı şekil çizme</span><span class="sxs-lookup"><span data-stu-id="36e36-102">How to: Draw an Outlined Shape</span></span>
<span data-ttu-id="36e36-103">Bu örnek, bir form üzerinde Anahatlı elips ve dikdörtgen çizer.</span><span class="sxs-lookup"><span data-stu-id="36e36-103">This example draws outlined ellipses and rectangles on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36e36-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="36e36-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="36e36-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="36e36-105">Compiling the Code</span></span>  
 <span data-ttu-id="36e36-106">Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="36e36-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="36e36-107">Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="36e36-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="36e36-108">İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="36e36-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="36e36-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="36e36-109">Robust Programming</span></span>  
 <span data-ttu-id="36e36-110">Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> gibi sistem kaynaklarının kullanan herhangi bir nesne üzerinde <xref:System.Drawing.Pen> ve <xref:System.Drawing.Graphics> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="36e36-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e36-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36e36-111">See also</span></span>
- <xref:System.Drawing.Graphics.DrawEllipse%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Graphics.DrawRectangle%2A>
- [<span data-ttu-id="36e36-112">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="36e36-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="36e36-113">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="36e36-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="36e36-114">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="36e36-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
