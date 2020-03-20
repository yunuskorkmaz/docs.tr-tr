---
title: 'Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142439"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="3f076-102">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f076-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="3f076-103">Çizgiler ve şekiller çizebilmeniz, metni oluşturmadan veya GDI+ ile görüntüleri <xref:System.Drawing.Graphics> görüntülemeden ve işlemeden önce bir nesne oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f076-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3f076-104">Nesne <xref:System.Drawing.Graphics> GDI+ çizim yüzeyini temsil eder ve grafik görüntüler oluşturmak için kullanılan nesnedir.</span><span class="sxs-lookup"><span data-stu-id="3f076-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="3f076-105">Grafiklerle çalışmanın iki adımı vardır:</span><span class="sxs-lookup"><span data-stu-id="3f076-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="3f076-106">Nesne <xref:System.Drawing.Graphics> oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3f076-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="3f076-107"><xref:System.Drawing.Graphics> Nesneleri kullanarak çizgiler ve şekiller çizmek, metni işlemek veya görüntüleri görüntülemek ve işlemek için.</span><span class="sxs-lookup"><span data-stu-id="3f076-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="3f076-108">Grafik Nesnesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f076-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="3f076-109">Grafik nesnesi çeşitli şekillerde oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3f076-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="3f076-110">Grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3f076-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="3f076-111">Bir form veya denetim <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> durumunda bir parçası olarak bir grafik nesnesine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="3f076-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="3f076-112">Denetim için boyama kodu oluştururken genellikle grafik nesnesine başvuru yutmama şekliniz dir.</span><span class="sxs-lookup"><span data-stu-id="3f076-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="3f076-113">Benzer şekilde, bir <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage> . <xref:System.Drawing.Printing.PrintDocument></span><span class="sxs-lookup"><span data-stu-id="3f076-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="3f076-114">-veya-</span><span class="sxs-lookup"><span data-stu-id="3f076-114">-or-</span></span>  
  
- <span data-ttu-id="3f076-115">Bu <xref:System.Windows.Forms.Control.CreateGraphics%2A> denetimveya formun çizim yüzeyini temsil <xref:System.Drawing.Graphics> eden bir nesneye başvuru almak için bir denetim veya form yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="3f076-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="3f076-116">Zaten var olan bir form veya denetim üzerinde çizmek istiyorsanız bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3f076-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="3f076-117">-veya-</span><span class="sxs-lookup"><span data-stu-id="3f076-117">-or-</span></span>  
  
- <span data-ttu-id="3f076-118">Devralan <xref:System.Drawing.Graphics> herhangi bir nesneden <xref:System.Drawing.Image>bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f076-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="3f076-119">Bu yaklaşım, zaten varolan bir görüntüyü değiştirmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3f076-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="3f076-120">Aşağıdaki bölümlerde bu işlemlerin her biri hakkında ayrıntılı bilgi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3f076-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="3f076-121">PaintEventEtkinlikArgs Boya Olay Handleyici</span><span class="sxs-lookup"><span data-stu-id="3f076-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="3f076-122"><xref:System.Windows.Forms.PaintEventHandler> Ne zaman programlama denetimleri <xref:System.Drawing.Printing.PrintDocument.PrintPage> veya <xref:System.Drawing.Printing.PrintDocument>için , bir grafik nesnesi <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>özelliklerinden biri olarak sağlanır veya .</span><span class="sxs-lookup"><span data-stu-id="3f076-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="3f076-123">Paint olayındaki PaintEventArgs'tan grafik nesnesine referans almak için</span><span class="sxs-lookup"><span data-stu-id="3f076-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="3f076-124">Nesneyi <xref:System.Drawing.Graphics> bildirin.</span><span class="sxs-lookup"><span data-stu-id="3f076-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="3f076-125">Değişkeni, bir parçası <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs>olarak geçirilen nesneye başvurmak için ata.</span><span class="sxs-lookup"><span data-stu-id="3f076-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="3f076-126">Formu veya denetimi boyamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3f076-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="3f076-127">Aşağıdaki örnek, <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olaydaki bir nesneye nasıl başvurulsüreceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="3f076-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="3f076-128">CreateGraphics Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f076-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="3f076-129">Denetim veya formun çizim yüzeyini temsil eden <xref:System.Windows.Forms.Control.CreateGraphics%2A> bir <xref:System.Drawing.Graphics> nesneye başvuru almak için denetim veya form yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f076-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="3f076-130">CreateGraphics yöntemiyle grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3f076-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="3f076-131">Grafik <xref:System.Windows.Forms.Control.CreateGraphics%2A> oluşturmak istediğiniz form veya denetim yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="3f076-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="3f076-132">Görüntü Nesnesinden Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f076-132">Create from an Image Object</span></span>  
 <span data-ttu-id="3f076-133">Ayrıca, sınıftan türetilen herhangi bir nesneden bir <xref:System.Drawing.Image> grafik nesnesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f076-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="3f076-134">Görüntüden Grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3f076-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="3f076-135">Bir <xref:System.Drawing.Graphics> <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> nesne oluşturmak istediğiniz Görüntü değişkeninin adını sağlayarak yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="3f076-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="3f076-136">Aşağıdaki örnek, bir <xref:System.Drawing.Bitmap> nesnenin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="3f076-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> <span data-ttu-id="3f076-137">Yalnızca 16 <xref:System.Drawing.Graphics> bit, 24-bit ve 32 bit .bmp dosyaları gibi dizine eklenmemiş .bmp dosyalarından nesneler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f076-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="3f076-138">Dizine eklenmemiş .bmp dosyalarının her pikseli, renk tablosuna dizin tutan dizin ekinli .bmp dosyalarının piksellerinin aksine bir renk tutar.</span><span class="sxs-lookup"><span data-stu-id="3f076-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="3f076-139">Şekil ve Görüntüleri Çizme ve Manipüle Etme</span><span class="sxs-lookup"><span data-stu-id="3f076-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="3f076-140">Oluşturulduktan sonra, <xref:System.Drawing.Graphics> bir nesne çizgiler ve şekiller çizmek, metni işlemek veya görüntüleri görüntülemek ve işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f076-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="3f076-141"><xref:System.Drawing.Graphics> Nesne ile birlikte kullanılan temel nesneler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3f076-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="3f076-142">Sınıf-Çizgiler <xref:System.Drawing.Pen> çizmek, şekilleri özetleme veya diğer geometrik gösterimleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f076-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="3f076-143"><xref:System.Drawing.Brush> Sınıf—Dolu şekiller, resimler veya metin gibi grafik alanlarını doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f076-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="3f076-144">Sınıf—Metni <xref:System.Drawing.Font> işlerken hangi şekillerin kullanılacağının açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f076-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="3f076-145">Yapı-Görüntülenecek <xref:System.Drawing.Color> farklı renkleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3f076-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="3f076-146">Oluşturduğunuz Grafik nesnesini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="3f076-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="3f076-147">İhtiyacınız olanı çizmek için yukarıda listelenen uygun nesneyle çalışın.</span><span class="sxs-lookup"><span data-stu-id="3f076-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="3f076-148">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="3f076-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="3f076-149">Işlemek için</span><span class="sxs-lookup"><span data-stu-id="3f076-149">To render</span></span>|<span data-ttu-id="3f076-150">Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f076-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="3f076-151">Satırlar</span><span class="sxs-lookup"><span data-stu-id="3f076-151">Lines</span></span>|[<span data-ttu-id="3f076-152">Nasıl yapılır: Bir Windows Formunda Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="3f076-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="3f076-153">Şekiller</span><span class="sxs-lookup"><span data-stu-id="3f076-153">Shapes</span></span>|[<span data-ttu-id="3f076-154">Nasıl yapılır: Ana Hatlı Şekil Çizme</span><span class="sxs-lookup"><span data-stu-id="3f076-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="3f076-155">Metin</span><span class="sxs-lookup"><span data-stu-id="3f076-155">Text</span></span>|[<span data-ttu-id="3f076-156">Nasıl yapılır: Bir Windows Formunda Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="3f076-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="3f076-157">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="3f076-157">Images</span></span>|[<span data-ttu-id="3f076-158">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="3f076-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="3f076-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f076-159">See also</span></span>

- [<span data-ttu-id="3f076-160">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="3f076-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="3f076-161">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="3f076-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="3f076-162">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="3f076-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="3f076-163">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="3f076-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
