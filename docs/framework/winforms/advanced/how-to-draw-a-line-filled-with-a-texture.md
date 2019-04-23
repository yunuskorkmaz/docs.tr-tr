---
title: 'Nasıl yapılır: Bir Dokuyla Doldurulmuş Çizgi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: c0f90c298f48aeb96893bb09241faddc08d8a49d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186914"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="714e8-102">Nasıl yapılır: Bir Dokuyla Doldurulmuş Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="714e8-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="714e8-103">Düz renk ile bir çizgiyi çizmek yerine, bir çizgi bir doku ile çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="714e8-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="714e8-104">Çizgiler ve eğrilerle bir doku ile çizmek için oluşturma bir <xref:System.Drawing.TextureBrush> nesne ve, geçmesi <xref:System.Drawing.TextureBrush> nesnesini bir <xref:System.Drawing.Pen.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="714e8-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="714e8-105">Doku fırça ile ilişkili bit eşlem düzlem (görünmez) döşeme için kullanılır ve Kalem bir çizgi veya eğri çizdiğinde kalemin vuruş belirli piksel döşenmiş doku açıklığa kavuşturur.</span><span class="sxs-lookup"><span data-stu-id="714e8-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="714e8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="714e8-106">Example</span></span>  
 <span data-ttu-id="714e8-107">Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Bitmap> dosyasından nesnesi `Texture1.jpg`.</span><span class="sxs-lookup"><span data-stu-id="714e8-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="714e8-108">Bit eşlem oluşturmak için kullanılan bir <xref:System.Drawing.TextureBrush> nesnesi ve <xref:System.Drawing.TextureBrush> nesne oluşturmak için kullanılan bir <xref:System.Drawing.Pen> nesne.</span><span class="sxs-lookup"><span data-stu-id="714e8-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="714e8-109">Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> bit eşlem ile sol üst köşede çizer (0, 0).</span><span class="sxs-lookup"><span data-stu-id="714e8-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="714e8-110">Çağrı <xref:System.Drawing.Graphics.DrawEllipse%2A> kullanan <xref:System.Drawing.Pen> nesne dokulu bir elips çizin.</span><span class="sxs-lookup"><span data-stu-id="714e8-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="714e8-111">Bit eşlem ve dokulu elips aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="714e8-111">The following illustration shows the bitmap and the textured ellipse:</span></span>  
  
 ![Bit eşlem ve dokulu elips gösteren ekran görüntüsü.](./media/how-to-draw-a-line-filled-with-a-texture/bitmap-textured-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="714e8-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="714e8-113">Compiling the Code</span></span>  
 <span data-ttu-id="714e8-114">Bir Windows formu oluşturma ve form ele <xref:System.Windows.Forms.Control.Paint> olay.</span><span class="sxs-lookup"><span data-stu-id="714e8-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="714e8-115">Önceki kodun içine yapıştırın <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="714e8-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="714e8-116">Değiştirin `Texture.jpg` sisteminize göre geçerli görüntü ile.</span><span class="sxs-lookup"><span data-stu-id="714e8-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714e8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="714e8-117">See also</span></span>

- [<span data-ttu-id="714e8-118">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="714e8-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="714e8-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="714e8-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
