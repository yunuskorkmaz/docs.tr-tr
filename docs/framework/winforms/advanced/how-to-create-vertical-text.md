---
title: 'Nasıl yapılır: Dikey metin oluşturma'
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
ms.openlocfilehash: 720e343f1b3b20fe3df96a03fbd67ee473ec13f6
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125414"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="13779-102">Nasıl yapılır: Dikey metin oluşturma</span><span class="sxs-lookup"><span data-stu-id="13779-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="13779-103">Kullanabileceğiniz bir <xref:System.Drawing.StringFormat> metin dikey yerine yatay olarak çizilecek belirtmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="13779-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13779-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="13779-104">Example</span></span>  
 <span data-ttu-id="13779-105">Aşağıdaki örnek değeri atar <xref:System.Drawing.StringFormatFlags.DirectionVertical> için <xref:System.Drawing.StringFormat.FormatFlags%2A> özelliği bir <xref:System.Drawing.StringFormat> nesne.</span><span class="sxs-lookup"><span data-stu-id="13779-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="13779-106">Olduğunu <xref:System.Drawing.StringFormat> nesnesi <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="13779-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="13779-107">Değer <xref:System.Drawing.StringFormatFlags.DirectionVertical> üyesi <xref:System.Drawing.StringFormatFlags> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="13779-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="13779-108">Dikey metin aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="13779-108">The following illustration shows the vertical text:</span></span> 
  
 ![Dikey yazı tipi, metin gösteren grafik.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13779-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="13779-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="13779-111">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e` , parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="13779-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13779-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13779-112">See also</span></span>
- [<span data-ttu-id="13779-113">Nasıl yapılır: GDI ile metin çizme</span><span class="sxs-lookup"><span data-stu-id="13779-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
