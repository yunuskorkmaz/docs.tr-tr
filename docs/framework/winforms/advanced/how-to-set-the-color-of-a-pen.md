---
title: "Nasıl yapılır: Bir Kalemin Rengini Ayarlama"
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
helpviewer_keywords:
- pens [Windows Forms], setting color
- colored pens
ms.assetid: a9df06f9-a6d5-4d9b-a2d1-583943540775
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 452e88b4b41a22cc78f73e120e49468e4f4dad56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-color-of-a-pen"></a><span data-ttu-id="8f1e3-102">Nasıl yapılır: Bir Kalemin Rengini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="8f1e3-102">How to: Set the Color of a Pen</span></span>
<span data-ttu-id="8f1e3-103">Bu örnek önceden var olan rengini değiştirir <xref:System.Drawing.Pen> nesnesi</span><span class="sxs-lookup"><span data-stu-id="8f1e3-103">This example changes the color of a pre-existing <xref:System.Drawing.Pen> object</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f1e3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f1e3-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#9)]
 [!code-csharp[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#9)]
 [!code-vb[System.Drawing.ConceptualHowTos#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f1e3-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8f1e3-105">Compiling the Code</span></span>  
 <span data-ttu-id="8f1e3-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8f1e3-106">This example requires:</span></span>  
  
-   <span data-ttu-id="8f1e3-107">A <xref:System.Drawing.Pen> adlı nesne `myPen`.</span><span class="sxs-lookup"><span data-stu-id="8f1e3-107">A <xref:System.Drawing.Pen> object named `myPen`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8f1e3-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8f1e3-108">Robust Programming</span></span>  
 <span data-ttu-id="8f1e3-109">Çağırmalısınız <xref:System.Drawing.Pen.Dispose%2A> sistem kaynaklarını tüketebilir nesneler üzerinde (gibi <xref:System.Drawing.Pen> nesneler) kullanmadan tamamladıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="8f1e3-109">You should call <xref:System.Drawing.Pen.Dispose%2A> on objects that consume system resources (such as <xref:System.Drawing.Pen> objects) after you are finished using them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1e3-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f1e3-110">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="8f1e3-111">Grafik programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="8f1e3-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="8f1e3-112">Nasıl yapılır: Kalem oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f1e3-112">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [<span data-ttu-id="8f1e3-113">Çizgiler ve şekiller çizmek için kalem kullanma</span><span class="sxs-lookup"><span data-stu-id="8f1e3-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="8f1e3-114">Kalemler, çizgiler ve dikdörtgenler GDI +'da</span><span class="sxs-lookup"><span data-stu-id="8f1e3-114">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
