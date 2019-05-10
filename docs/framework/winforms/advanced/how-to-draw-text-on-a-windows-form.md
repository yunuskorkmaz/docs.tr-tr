---
title: 'Nasıl yapılır: Bir Windows Formunda Metin Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: dc99a863765cd617c2ab4a636286f42f5e8daf79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626188"
---
# <a name="how-to-draw-text-on-a-windows-form"></a><span data-ttu-id="684dd-102">Nasıl yapılır: Bir Windows Formunda Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="684dd-102">How to: Draw Text on a Windows Form</span></span>
<span data-ttu-id="684dd-103">Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> bir form üzerinde metin Çiz için.</span><span class="sxs-lookup"><span data-stu-id="684dd-103">The following code example shows how to use the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> to draw text on a form.</span></span> <span data-ttu-id="684dd-104">Alternatif olarak, <xref:System.Windows.Forms.TextRenderer> bir form üzerinde metin çizme.</span><span class="sxs-lookup"><span data-stu-id="684dd-104">Alternatively, you can use <xref:System.Windows.Forms.TextRenderer> for drawing text on a form.</span></span> <span data-ttu-id="684dd-105">Daha fazla bilgi için [nasıl yapılır: GDI ile metin çizme](how-to-draw-text-with-gdi.md).</span><span class="sxs-lookup"><span data-stu-id="684dd-105">For more information, see [How to: Draw Text with GDI](how-to-draw-text-with-gdi.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="684dd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="684dd-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="684dd-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="684dd-107">Compiling the Code</span></span>  
 <span data-ttu-id="684dd-108">Çağıramazsınız <xref:System.Drawing.Graphics.DrawString%2A> yönteminde <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="684dd-108">You cannot call the <xref:System.Drawing.Graphics.DrawString%2A> method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="684dd-109">Formu yeniden boyutlandırılabilir veya başka bir form tarafından engellediği çizilen içeriği yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="684dd-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="684dd-110">İçeriğinizi otomatik olarak repaint yapmak için geçersiz kılmanız <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="684dd-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="684dd-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="684dd-111">Robust Programming</span></span>  
 <span data-ttu-id="684dd-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="684dd-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="684dd-113">Arial yazı tipi yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="684dd-113">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684dd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="684dd-114">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="684dd-115">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="684dd-115">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="684dd-116">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="684dd-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
