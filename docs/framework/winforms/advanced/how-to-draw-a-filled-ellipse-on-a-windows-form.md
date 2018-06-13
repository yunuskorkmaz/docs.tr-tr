---
title: 'Nasıl yapılır: Bir Windows Formunda Doldurulmuş Elips Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
ms.openlocfilehash: b892670031e795ecd27b194cdf2cf818f4af6254
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521439"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a><span data-ttu-id="3d9c9-102">Nasıl yapılır: Bir Windows Formunda Doldurulmuş Elips Çizme</span><span class="sxs-lookup"><span data-stu-id="3d9c9-102">How to: Draw a Filled Ellipse on a Windows Form</span></span>
<span data-ttu-id="3d9c9-103">Bu örnek bir formunda doldurulmuş elips çizer.</span><span class="sxs-lookup"><span data-stu-id="3d9c9-103">This example draws a filled ellipse on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d9c9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d9c9-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d9c9-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3d9c9-105">Compiling the Code</span></span>  
 <span data-ttu-id="3d9c9-106">Bu yöntem çağıramazsınız <xref:System.Windows.Forms.Form.Load> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="3d9c9-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="3d9c9-107">Formu yeniden boyutlandırılmış veya başka bir form tarafından getirilmemeli çizilmiş içeriği yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="3d9c9-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="3d9c9-108">İçeriğinizi otomatik olarak yeniden boyamak yapmak için geçersiz kılmalıdır <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3d9c9-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3d9c9-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3d9c9-109">Robust Programming</span></span>  
 <span data-ttu-id="3d9c9-110">Her zaman çağırmalıdır <xref:System.IDisposable.Dispose%2A> sistem kaynakları gibi kullanabilecek tüm nesneler üzerinde <xref:System.Drawing.Brush> ve <xref:System.Drawing.Graphics> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3d9c9-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9c9-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d9c9-111">See Also</span></span>  
 [<span data-ttu-id="3d9c9-112">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="3d9c9-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="3d9c9-113">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="3d9c9-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="3d9c9-114">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="3d9c9-114">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="3d9c9-115">Şekilleri Doldurmak için Fırça Kullanma</span><span class="sxs-lookup"><span data-stu-id="3d9c9-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
