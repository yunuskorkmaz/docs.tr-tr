---
title: 'Nasıl yapılır: Dikey Metin Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182556"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="a8b30-102">Nasıl yapılır: Dikey Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8b30-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="a8b30-103">Bir <xref:System.Drawing.StringFormat> nesneyi, metnin yatay değil dikey olarak çizildiğini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8b30-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8b30-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8b30-104">Example</span></span>  
 <span data-ttu-id="a8b30-105">Aşağıdaki örnek, değeri <xref:System.Drawing.StringFormatFlags.DirectionVertical> bir <xref:System.Drawing.StringFormat.FormatFlags%2A> <xref:System.Drawing.StringFormat> nesnenin özelliğine atar.</span><span class="sxs-lookup"><span data-stu-id="a8b30-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="a8b30-106">Bu <xref:System.Drawing.StringFormat> nesne <xref:System.Drawing.Graphics> sınıfın <xref:System.Drawing.Graphics.DrawString%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a8b30-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="a8b30-107">Değer <xref:System.Drawing.StringFormatFlags.DirectionVertical> numaralandırmanın <xref:System.Drawing.StringFormatFlags> bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="a8b30-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="a8b30-108">Aşağıdaki resimde dikey metin gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a8b30-108">The following illustration shows the vertical text:</span></span>
  
 ![Dikey yazı tipi metnini gösteren grafik.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8b30-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a8b30-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="a8b30-111">Önceki örnek Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e` tasarlanmıştır ve gerektirir , <xref:System.Windows.Forms.PaintEventHandler>hangi bir parametre .</span><span class="sxs-lookup"><span data-stu-id="a8b30-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8b30-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8b30-112">See also</span></span>

- [<span data-ttu-id="a8b30-113">Nasıl yapılır: GDI ile Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="a8b30-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
