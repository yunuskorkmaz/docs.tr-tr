---
title: 'Nasıl yapılır: Bir dokuyla doldurulmuş çizgi çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 65d830ca2d01c63288ef73b6b3a3a94f328fe32b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676253"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="39dfc-102">Nasıl yapılır: Bir dokuyla doldurulmuş çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="39dfc-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="39dfc-103">Düz renk ile bir çizgiyi çizmek yerine, bir çizgi bir doku ile çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39dfc-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="39dfc-104">Çizgiler ve eğrilerle bir doku ile çizmek için oluşturma bir <xref:System.Drawing.TextureBrush> nesne ve, geçmesi <xref:System.Drawing.TextureBrush> nesnesini bir <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="39dfc-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="39dfc-105">Doku fırça ile ilişkili bit eşlem düzlem (görünmez) döşeme için kullanılır ve Kalem bir çizgi veya eğri çizdiğinde kalemin vuruş belirli piksel döşenmiş doku açıklığa kavuşturur.</span><span class="sxs-lookup"><span data-stu-id="39dfc-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39dfc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="39dfc-106">Example</span></span>  
 <span data-ttu-id="39dfc-107">Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Bitmap> dosyasından nesnesi `Texture1.jpg`.</span><span class="sxs-lookup"><span data-stu-id="39dfc-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="39dfc-108">Bit eşlem oluşturmak için kullanılan bir <xref:System.Drawing.TextureBrush> nesnesi ve <xref:System.Drawing.TextureBrush> nesne oluşturmak için kullanılan bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="39dfc-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="39dfc-109">Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> bit eşlem ile sol üst köşede çizer (0, 0).</span><span class="sxs-lookup"><span data-stu-id="39dfc-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="39dfc-110">Çağrı <xref:System.Drawing.Graphics.DrawEllipse%2A> kullanan <xref:System.Drawing.Pen> nesne dokulu bir elips çizin.</span><span class="sxs-lookup"><span data-stu-id="39dfc-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="39dfc-111">Aşağıdaki çizim, bit eşlem ve dokulu elips gösterir.</span><span class="sxs-lookup"><span data-stu-id="39dfc-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="39dfc-112">![Kalemler](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="39dfc-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="39dfc-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="39dfc-113">Compiling the Code</span></span>  
 <span data-ttu-id="39dfc-114">Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="39dfc-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="39dfc-115">Önceki kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="39dfc-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="39dfc-116">Değiştirin `Texture.jpg` sisteminize göre geçerli görüntü ile.</span><span class="sxs-lookup"><span data-stu-id="39dfc-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39dfc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39dfc-117">See also</span></span>
- [<span data-ttu-id="39dfc-118">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="39dfc-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="39dfc-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="39dfc-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
