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
ms.openlocfilehash: dc067f5a131951bf3af7adc68e11b948d40fc0ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213421"
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="a88a0-102">Nasıl yapılır: Bir Kalemin Rengini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="a88a0-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="a88a0-103">Bu örnek, önceden var olan rengini değiştirir <xref:System.Drawing.Pen> nesnesi</span><span class="sxs-lookup"><span data-stu-id="a88a0-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="a88a0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a88a0-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a88a0-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a88a0-105">Compiling the Code</span></span>  
 <span data-ttu-id="a88a0-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="a88a0-106">This example requires:</span></span>  
  
-   <span data-ttu-id="a88a0-107">A <xref:System.Drawing.Pen> adlı nesne `myPen`.</span><span class="sxs-lookup"><span data-stu-id="a88a0-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a88a0-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="a88a0-108">Robust Programming</span></span>  
 <span data-ttu-id="a88a0-109">Çağırmalısınız <xref:System.Drawing.Pen.Dispose%2A> sistem kaynaklarının kullanılmasına nesneler üzerinde (gibi <xref:System.Drawing.Pen> nesneleri) kullanmadan tamamladıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="a88a0-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88a0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a88a0-110">See also</span></span>

- <xref:System.Drawing.Pen>
- [<span data-ttu-id="a88a0-111">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="a88a0-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="a88a0-112">Nasıl yapılır: Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="a88a0-112">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
- [<span data-ttu-id="a88a0-113">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="a88a0-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="a88a0-114">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="a88a0-114">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
