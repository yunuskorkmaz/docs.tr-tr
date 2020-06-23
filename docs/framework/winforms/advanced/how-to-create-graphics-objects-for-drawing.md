---
title: 'Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma'
description: Çizgiler ve şekiller çizmek, metin oluşturmak veya GDI+ ile görüntüleri görüntülemek ve işlemek için gereken bir grafik nesnesi oluşturmayı öğrenin.
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
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903213"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="1e7d9-103">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e7d9-103">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="1e7d9-104">Çizgiler ve şekiller çizmeden, metin oluşturmadan veya GDI+ ile görüntüleri görüntüleyip işleyebilmeniz için önce bir nesnesi oluşturmanız gerekir <xref:System.Drawing.Graphics> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-104">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="1e7d9-105"><xref:System.Drawing.Graphics>Nesnesi BIR GDI+ çizim yüzeyini temsil eder ve grafik görüntüleri oluşturmak için kullanılan nesnedir.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-105">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="1e7d9-106">Grafiklerle çalışırken iki adım vardır:</span><span class="sxs-lookup"><span data-stu-id="1e7d9-106">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="1e7d9-107">Nesne oluşturma <xref:System.Drawing.Graphics> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-107">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="1e7d9-108"><xref:System.Drawing.Graphics>Çizgi ve şekil çizmek, metin oluşturmak veya görüntüleri görüntülemek ve işlemek için nesnesini kullanma.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-108">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="1e7d9-109">Grafik nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e7d9-109">Creating a Graphics Object</span></span>  
 <span data-ttu-id="1e7d9-110">Grafik nesnesi çeşitli yollarla oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-110">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="1e7d9-111">Grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e7d9-111">To create a graphics object</span></span>  
  
- <span data-ttu-id="1e7d9-112">Bir <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> form veya denetim olayında bir grafik nesnesine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-112">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="1e7d9-113">Bu, genellikle bir denetim için boyama kodu oluştururken bir grafik nesnesine başvuru elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-113">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="1e7d9-114">Benzer şekilde, bir grafik nesnesini, <xref:System.Drawing.Printing.PrintPageEventArgs> için olayını işlerken bir özelliği olarak da elde edebilirsiniz <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-114">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="1e7d9-115">-veya-</span><span class="sxs-lookup"><span data-stu-id="1e7d9-115">-or-</span></span>  
  
- <span data-ttu-id="1e7d9-116">Denetim veya formun <xref:System.Windows.Forms.Control.CreateGraphics%2A> <xref:System.Drawing.Graphics> çizim yüzeyini temsil eden bir nesneye başvuru almak için bir denetimin veya formun yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-116">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="1e7d9-117">Zaten var olan bir form veya denetim üzerine çizim yapmak istiyorsanız bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-117">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="1e7d9-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="1e7d9-118">-or-</span></span>  
  
- <span data-ttu-id="1e7d9-119"><xref:System.Drawing.Graphics>Öğesinden devralan herhangi bir nesneden bir nesne oluşturun <xref:System.Drawing.Image> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-119">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="1e7d9-120">Bu yaklaşım, zaten varolan bir görüntüyü değiştirmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-120">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="1e7d9-121">Aşağıdaki bölümler, bu işlemlerin her biri hakkında ayrıntılı bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-121">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="1e7d9-122">Paint olay Işleyicisindeki PaintEventArgs</span><span class="sxs-lookup"><span data-stu-id="1e7d9-122">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="1e7d9-123"><xref:System.Windows.Forms.PaintEventHandler>Denetimleri için veya için programlama yaparken, <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> veya özelliklerinden biri olarak bir grafik nesnesi sağlanır <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-123">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="1e7d9-124">Paint olaydaki PaintEventArgs 'dan bir grafik nesnesine başvuru almak için</span><span class="sxs-lookup"><span data-stu-id="1e7d9-124">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="1e7d9-125">Nesneyi bildirin <xref:System.Drawing.Graphics> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-125">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="1e7d9-126"><xref:System.Drawing.Graphics>Öğesinin bir parçası olarak geçirilen nesneye başvuracak değişkeni atayın <xref:System.Windows.Forms.PaintEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-126">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="1e7d9-127">Formu veya denetimi boyamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-127">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="1e7d9-128">Aşağıdaki örnek, <xref:System.Drawing.Graphics> olaydaki öğesinden bir nesnesine nasıl başvurulacağını gösterir <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> :</span><span class="sxs-lookup"><span data-stu-id="1e7d9-128">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="1e7d9-129">CreateGraphics yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e7d9-129">CreateGraphics Method</span></span>  
 <span data-ttu-id="1e7d9-130"><xref:System.Windows.Forms.Control.CreateGraphics%2A> <xref:System.Drawing.Graphics> Bu denetim veya formun çizim yüzeyini temsil eden bir nesneye başvuru almak için bir denetimin veya formun yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-130">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="1e7d9-131">CreateGraphics yöntemiyle bir grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e7d9-131">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="1e7d9-132"><xref:System.Windows.Forms.Control.CreateGraphics%2A>Grafikleri işlemek istediğiniz formun veya denetimin yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-132">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="1e7d9-133">Bir görüntü nesnesinden oluştur</span><span class="sxs-lookup"><span data-stu-id="1e7d9-133">Create from an Image Object</span></span>  
 <span data-ttu-id="1e7d9-134">Ayrıca, sınıfından türetilen herhangi bir nesneden bir grafik nesnesi oluşturabilirsiniz <xref:System.Drawing.Image> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-134">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="1e7d9-135">Görüntüden bir grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1e7d9-135">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="1e7d9-136"><xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>Nesne oluşturmak Istediğiniz görüntü değişkeninin adını sağlayarak yöntemini çağırın <xref:System.Drawing.Graphics> .</span><span class="sxs-lookup"><span data-stu-id="1e7d9-136">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="1e7d9-137">Aşağıdaki örnek, bir nesnesinin nasıl kullanılacağını gösterir <xref:System.Drawing.Bitmap> :</span><span class="sxs-lookup"><span data-stu-id="1e7d9-137">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="1e7d9-138">Yalnızca <xref:System.Drawing.Graphics> dizinli olmayan. bmp dosyalarından (16 bit, 24 bit ve 32-bit. bmp dosyaları gibi) nesneler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-138">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="1e7d9-139">Dizinlenmemiş. bmp dosyalarının her pikseli, bir renk tablosuna bir dizin tutan dizinli. bmp dosyalarının piksel cinsinden bir renk tutar.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-139">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="1e7d9-140">Şekilleri ve görüntüleri çizme ve düzenleme</span><span class="sxs-lookup"><span data-stu-id="1e7d9-140">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="1e7d9-141">Oluşturulduktan sonra, bir <xref:System.Drawing.Graphics> nesne çizgiler ve şekiller çizmek, metin oluşturmak veya görüntü görüntülemek ve işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-141">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="1e7d9-142">Nesnesiyle kullanılan asıl nesneler <xref:System.Drawing.Graphics> şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1e7d9-142">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="1e7d9-143"><xref:System.Drawing.Pen>Sınıfı — çizgi çizme, şekil seviyelendirme veya diğer geometrik gösterimleri işleme Için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-143">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="1e7d9-144"><xref:System.Drawing.Brush>Sınıfı — dolgulu şekiller, görüntüler veya metin gibi grafik alanlarının doldurulması Için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-144">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="1e7d9-145"><xref:System.Drawing.Font>Sınıfı — metin işlenirken hangi şekillerin kullanılacağı hakkında bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-145">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="1e7d9-146"><xref:System.Drawing.Color>Yapı — görüntülenecek farklı renkleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-146">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="1e7d9-147">Oluşturduğunuz grafik nesnesini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1e7d9-147">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="1e7d9-148">İhtiyacınız olan öğeleri çizmek için yukarıda listelenen uygun nesneyle çalışın.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-148">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="1e7d9-149">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="1e7d9-149">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="1e7d9-150">İşlemek için</span><span class="sxs-lookup"><span data-stu-id="1e7d9-150">To render</span></span>|<span data-ttu-id="1e7d9-151">Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-151">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="1e7d9-152">Satırlar</span><span class="sxs-lookup"><span data-stu-id="1e7d9-152">Lines</span></span>|[<span data-ttu-id="1e7d9-153">Nasıl yapılır: Bir Windows Formunda Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="1e7d9-153">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="1e7d9-154">Şekiller</span><span class="sxs-lookup"><span data-stu-id="1e7d9-154">Shapes</span></span>|[<span data-ttu-id="1e7d9-155">Nasıl yapılır: Ana Hatlı Şekil Çizme</span><span class="sxs-lookup"><span data-stu-id="1e7d9-155">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="1e7d9-156">Metin</span><span class="sxs-lookup"><span data-stu-id="1e7d9-156">Text</span></span>|[<span data-ttu-id="1e7d9-157">Nasıl yapılır: Bir Windows Formunda Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="1e7d9-157">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="1e7d9-158">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="1e7d9-158">Images</span></span>|[<span data-ttu-id="1e7d9-159">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="1e7d9-159">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1e7d9-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e7d9-160">See also</span></span>

- [<span data-ttu-id="1e7d9-161">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="1e7d9-161">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="1e7d9-162">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="1e7d9-162">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1e7d9-163">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="1e7d9-163">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="1e7d9-164">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="1e7d9-164">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
