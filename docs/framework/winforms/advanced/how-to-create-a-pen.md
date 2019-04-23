---
title: 'Nasıl yapılır: Kalem Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
ms.openlocfilehash: 69fe6157c710ae63df9dbf391a5d355d1c3f9765
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148115"
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="3c702-102">Nasıl yapılır: Kalem Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c702-102">How to: Create a Pen</span></span>
<span data-ttu-id="3c702-103">Bu örnekte bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="3c702-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c702-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c702-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3c702-105">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3c702-105">Robust Programming</span></span>  
 <span data-ttu-id="3c702-106">Gibi sistem kaynağı tüketen nesneleri kullanarak tamamladıktan sonra <xref:System.Drawing.Pen> nesneleri, çağırmalıdır <xref:System.Drawing.Pen.Dispose%2A> bunlar üzerinde.</span><span class="sxs-lookup"><span data-stu-id="3c702-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c702-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c702-107">See also</span></span>

- <xref:System.Drawing.Pen>
- [<span data-ttu-id="3c702-108">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="3c702-108">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="3c702-109">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="3c702-109">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
