---
title: 'Nasıl yapılır: Bir Kalemin Rengini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
ms.openlocfilehash: 37bc289fa1eeb7ef5510474dff062ae76be5fc65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522388"
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="c0cbd-102">Nasıl yapılır: Bir Kalemin Rengini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c0cbd-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="c0cbd-103">Bu örnek önceden var olan rengini değiştirir <xref:System.Drawing.Pen> nesnesi</span><span class="sxs-lookup"><span data-stu-id="c0cbd-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0cbd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0cbd-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c0cbd-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c0cbd-105">Compiling the Code</span></span>  
 <span data-ttu-id="c0cbd-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c0cbd-106">This example requires:</span></span>  
  
-   <span data-ttu-id="c0cbd-107">A <xref:System.Drawing.Pen> adlı nesne `myPen`.</span><span class="sxs-lookup"><span data-stu-id="c0cbd-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c0cbd-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c0cbd-108">Robust Programming</span></span>  
 <span data-ttu-id="c0cbd-109">Çağırmalısınız <xref:System.Drawing.Pen.Dispose%2A> sistem kaynaklarını tüketebilir nesneler üzerinde (gibi <xref:System.Drawing.Pen> nesneler) kullanmadan tamamladıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="c0cbd-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0cbd-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0cbd-110">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="c0cbd-111">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="c0cbd-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="c0cbd-112">Nasıl yapılır: Kalem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0cbd-112">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="c0cbd-113">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="c0cbd-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="c0cbd-114">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="c0cbd-114">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
