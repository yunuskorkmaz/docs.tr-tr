---
title: 'Nasıl Yapılsın: Titremeyi Azaltmak için Pikselleri Kopyala'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182581"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="99917-102">Nasıl yapılır: Windows Formlarında Titreşimi Azaltmak için Piksel Kopyalama</span><span class="sxs-lookup"><span data-stu-id="99917-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="99917-103">Basit bir grafiği animasyona aldığınızda, kullanıcılar bazen titreme veya diğer istenmeyen görsel efektlerle karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="99917-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="99917-104">Bu sorunu sınırlamanın bir yolu grafiküzerinde bir "bitblt" işlemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="99917-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="99917-105">Bitblt, renk verilerinin piksellerin başlangıç dikdörtgeninden piksellerin hedef dikdörtgenine "bit bloğu aktarımı"dır.</span><span class="sxs-lookup"><span data-stu-id="99917-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="99917-106">Windows Forms ile bitblt <xref:System.Drawing.Graphics.CopyFromScreen%2A> <xref:System.Drawing.Graphics> sınıfın yöntemi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="99917-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="99917-107">Yöntemin parametrelerinde, kaynak ve hedef (nokta olarak), kopyalanacak alanın boyutunu ve yeni şekli çizmek için kullanılan grafik nesnesini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99917-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="99917-108">Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.Paint> olay işleyicisindeki forma bir şekil çizilir.</span><span class="sxs-lookup"><span data-stu-id="99917-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="99917-109">Daha sonra, <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntem şekli çoğaltmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="99917-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99917-110">Formun <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğinin, `true` <xref:System.Windows.Forms.Control.Paint> grafik tabanlı kodun çift arabelleğe alınmasını sağlayacak şekilde ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="99917-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="99917-111">Bu, aşağıdaki kodu kullanırken herhangi bir fark performans kazanımları olmayacak olsa da, daha karmaşık grafik işleme kodu ile çalışırken akılda tutulması gereken bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="99917-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99917-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="99917-112">Example</span></span>  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99917-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="99917-113">Compiling the Code</span></span>  
 <span data-ttu-id="99917-114">Yukarıdaki kod, form <xref:System.Windows.Forms.Control.Paint> yeniden çizildiğinde grafiklerin devam edilebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99917-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="99917-115">Bu nedenle, form yeniden boyutlandırılırveya <xref:System.Windows.Forms.Form.Load> başka bir form tarafından gizlenmişse, çizilen içerik yeniden çizilmeyecektir, çünkü olay işleyicisinde grafikle ilgili yöntemleri aramayın.</span><span class="sxs-lookup"><span data-stu-id="99917-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99917-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99917-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="99917-117">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="99917-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="99917-118">Çizgiler ve Şekiller Çizmek için Kalem Kullanma</span><span class="sxs-lookup"><span data-stu-id="99917-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
