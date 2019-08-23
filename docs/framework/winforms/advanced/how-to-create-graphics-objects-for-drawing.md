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
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964336"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="18472-102">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="18472-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="18472-103">Çizgiler ve şekiller çizmeden, metin oluşturmadan veya GDI+ ile görüntüleri görüntüleyip işleyebilmeniz için önce bir <xref:System.Drawing.Graphics> nesnesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="18472-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="18472-104"><xref:System.Drawing.Graphics> Nesnesi bir GDI+ çizim yüzeyini temsil eder ve grafik görüntüleri oluşturmak için kullanılan nesnedir.</span><span class="sxs-lookup"><span data-stu-id="18472-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="18472-105">Grafiklerle çalışırken iki adım vardır:</span><span class="sxs-lookup"><span data-stu-id="18472-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="18472-106"><xref:System.Drawing.Graphics> Nesne oluşturma.</span><span class="sxs-lookup"><span data-stu-id="18472-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="18472-107">Çizgi ve şekil çizmek, metin oluşturmak veya görüntüleri görüntülemek ve işlemek için nesnesinikullanma.<xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="18472-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="18472-108">Grafik nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="18472-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="18472-109">Grafik nesnesi çeşitli yollarla oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="18472-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="18472-110">Grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="18472-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="18472-111">Bir form veya denetim <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olayında bir grafik nesnesine bir başvuru alın.</span><span class="sxs-lookup"><span data-stu-id="18472-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="18472-112">Bu, genellikle bir denetim için boyama kodu oluştururken bir grafik nesnesine başvuru elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="18472-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="18472-113">Benzer şekilde, bir <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument>grafik nesnesini, için <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayını işlerken bir özelliği olarak da elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18472-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="18472-114">-veya-</span><span class="sxs-lookup"><span data-stu-id="18472-114">-or-</span></span>  
  
- <span data-ttu-id="18472-115">Denetim veya formun çizim yüzeyini temsil eden bir <xref:System.Drawing.Graphics> nesneye başvuru almak için bir denetimin veya formun yönteminiçağırın.<xref:System.Windows.Forms.Control.CreateGraphics%2A></span><span class="sxs-lookup"><span data-stu-id="18472-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="18472-116">Zaten var olan bir form veya denetim üzerine çizim yapmak istiyorsanız bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="18472-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="18472-117">-veya-</span><span class="sxs-lookup"><span data-stu-id="18472-117">-or-</span></span>  
  
- <span data-ttu-id="18472-118"><xref:System.Drawing.Graphics> Öğesinden<xref:System.Drawing.Image>devralan herhangi bir nesneden bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="18472-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="18472-119">Bu yaklaşım, zaten varolan bir görüntüyü değiştirmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="18472-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="18472-120">Aşağıdaki bölümler, bu işlemlerin her biri hakkında ayrıntılı bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="18472-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="18472-121">Paint olay Işleyicisindeki PaintEventArgs</span><span class="sxs-lookup"><span data-stu-id="18472-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="18472-122">Denetimleri <xref:System.Windows.Forms.PaintEventHandler> için <xref:System.Windows.Forms.PaintEventArgs> veya <xref:System.Drawing.Printing.PrintDocument.PrintPage> için<xref:System.Drawing.Printing.PrintDocument>programlama yaparken, veya<xref:System.Drawing.Printing.PrintPageEventArgs>özelliklerinden biri olarak bir grafik nesnesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="18472-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="18472-123">Paint olaydaki PaintEventArgs 'dan bir grafik nesnesine başvuru almak için</span><span class="sxs-lookup"><span data-stu-id="18472-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="18472-124"><xref:System.Drawing.Graphics> Nesneyi bildirin.</span><span class="sxs-lookup"><span data-stu-id="18472-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="18472-125">Öğesinin bir parçası olarak geçirilen <xref:System.Drawing.Graphics> nesneye başvuracak değişkeni atayın. <xref:System.Windows.Forms.PaintEventArgs></span><span class="sxs-lookup"><span data-stu-id="18472-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="18472-126">Formu veya denetimi boyamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="18472-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="18472-127">Aşağıdaki örnek, <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olaydaki öğesinden bir nesnesine nasıl başvurulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="18472-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="18472-128">CreateGraphics yöntemi</span><span class="sxs-lookup"><span data-stu-id="18472-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="18472-129">Bu denetim veya formun çizim <xref:System.Windows.Forms.Control.CreateGraphics%2A> yüzeyini temsil eden bir <xref:System.Drawing.Graphics> nesneye başvuru almak için bir denetimin veya formun yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18472-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="18472-130">CreateGraphics yöntemiyle bir grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="18472-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="18472-131">Grafikleri işlemek istediğiniz formun veya denetimin yönteminiçağırın.<xref:System.Windows.Forms.Control.CreateGraphics%2A></span><span class="sxs-lookup"><span data-stu-id="18472-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="18472-132">Bir görüntü nesnesinden oluştur</span><span class="sxs-lookup"><span data-stu-id="18472-132">Create from an Image Object</span></span>  
 <span data-ttu-id="18472-133">Ayrıca, <xref:System.Drawing.Image> sınıfından türetilen herhangi bir nesneden bir grafik nesnesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18472-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="18472-134">Görüntüden bir grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="18472-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="18472-135">Nesne oluşturmak istediğiniz görüntü değişkeninin adını sağlayarak yönteminiçağırın.<xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> <xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="18472-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="18472-136">Aşağıdaki örnek, bir <xref:System.Drawing.Bitmap> nesnesinin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="18472-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="18472-137">Yalnızca dizinli olmayan. <xref:System.Drawing.Graphics> BMP dosyalarından (16 bit, 24 bit ve 32-bit. bmp dosyaları gibi) nesneler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18472-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="18472-138">Dizinlenmemiş. bmp dosyalarının her pikseli, bir renk tablosuna bir dizin tutan dizinli. bmp dosyalarının piksel cinsinden bir renk tutar.</span><span class="sxs-lookup"><span data-stu-id="18472-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="18472-139">Şekilleri ve görüntüleri çizme ve düzenleme</span><span class="sxs-lookup"><span data-stu-id="18472-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="18472-140">Oluşturulduktan sonra, bir <xref:System.Drawing.Graphics> nesne çizgiler ve şekiller çizmek, metin oluşturmak veya görüntü görüntülemek ve işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18472-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="18472-141"><xref:System.Drawing.Graphics> Nesnesiyle kullanılan asıl nesneler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="18472-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="18472-142"><xref:System.Drawing.Pen> Sınıfı — çizgi çizme, şekil seviyelendirme veya diğer geometrik gösterimleri işleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18472-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="18472-143"><xref:System.Drawing.Brush> Sınıfı — dolgulu şekiller, görüntüler veya metin gibi grafik alanlarının doldurulması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18472-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="18472-144"><xref:System.Drawing.Font> Sınıfı — metin işlenirken hangi şekillerin kullanılacağı hakkında bir açıklama sağlar.</span><span class="sxs-lookup"><span data-stu-id="18472-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="18472-145"><xref:System.Drawing.Color> Yapı — görüntülenecek farklı renkleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="18472-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="18472-146">Oluşturduğunuz grafik nesnesini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="18472-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="18472-147">İhtiyacınız olan öğeleri çizmek için yukarıda listelenen uygun nesneyle çalışın.</span><span class="sxs-lookup"><span data-stu-id="18472-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="18472-148">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="18472-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="18472-149">İşlemek için</span><span class="sxs-lookup"><span data-stu-id="18472-149">To render</span></span>|<span data-ttu-id="18472-150">Bkz.</span><span class="sxs-lookup"><span data-stu-id="18472-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="18472-151">Satırları</span><span class="sxs-lookup"><span data-stu-id="18472-151">Lines</span></span>|[<span data-ttu-id="18472-152">Nasıl yapılır: Bir Windows formunda çizgi çizme</span><span class="sxs-lookup"><span data-stu-id="18472-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="18472-153">Şekiller</span><span class="sxs-lookup"><span data-stu-id="18472-153">Shapes</span></span>|[<span data-ttu-id="18472-154">Nasıl yapılır: Anahatları belirlenmiş bir şekil çiz</span><span class="sxs-lookup"><span data-stu-id="18472-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="18472-155">Metin</span><span class="sxs-lookup"><span data-stu-id="18472-155">Text</span></span>|[<span data-ttu-id="18472-156">Nasıl yapılır: Bir Windows formunda metin çizme</span><span class="sxs-lookup"><span data-stu-id="18472-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="18472-157">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="18472-157">Images</span></span>|[<span data-ttu-id="18472-158">Nasıl yapılır: GDI+ ile görüntü işleme</span><span class="sxs-lookup"><span data-stu-id="18472-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="18472-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18472-159">See also</span></span>

- [<span data-ttu-id="18472-160">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="18472-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="18472-161">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="18472-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="18472-162">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="18472-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="18472-163">Nasıl yapılır: GDI+ ile görüntü işleme</span><span class="sxs-lookup"><span data-stu-id="18472-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
