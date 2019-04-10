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
ms.openlocfilehash: 5682b2f0183cbeb8bae377423bb76caa0fbaf7cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223634"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="1a625-102">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a625-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="1a625-103">Çizgiler ve şekiller çizmek önce metin işlemek veya görüntülemek ve görüntülerle işlemek [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], oluşturmak gereken bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-103">Before you can draw lines and shapes, render text, or display and manipulate images with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="1a625-104"><xref:System.Drawing.Graphics> Nesnesini temsil eder bir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çizim yüzeyi ve grafik görüntüleri oluşturmak için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-104">The <xref:System.Drawing.Graphics> object represents a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="1a625-105">Grafiklerle çalışma iki adımı vardır:</span><span class="sxs-lookup"><span data-stu-id="1a625-105">There are two steps in working with graphics:</span></span>  
  
1.  <span data-ttu-id="1a625-106">Oluşturma bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="1a625-107">Kullanarak <xref:System.Drawing.Graphics> çizgiler ve şekiller çizmek, metin, işleme veya görüntülemek ve görüntüleri işlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="1a625-108">Bir grafik nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a625-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="1a625-109">Bir grafik nesnesinin çeşitli yollarla oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1a625-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="1a625-110">Bir grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1a625-110">To create a graphics object</span></span>  
  
-   <span data-ttu-id="1a625-111">Bir parçası olarak bir grafik nesnesine bir başvuru alma <xref:System.Windows.Forms.PaintEventArgs> içinde <xref:System.Windows.Forms.Control.Paint> bir form veya denetim olayı.</span><span class="sxs-lookup"><span data-stu-id="1a625-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="1a625-112">Bu, genellikle bir denetim boyama kodu oluştururken bir grafik nesnesine başvuru nasıl elde olur.</span><span class="sxs-lookup"><span data-stu-id="1a625-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="1a625-113">Benzer şekilde, ayrıca bir grafik nesnesinin bir özelliği olarak alabilirsiniz <xref:System.Drawing.Printing.PrintPageEventArgs> işlerken <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay için bir <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="1a625-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="1a625-114">-veya-</span><span class="sxs-lookup"><span data-stu-id="1a625-114">-or-</span></span>  
  
-   <span data-ttu-id="1a625-115">Çağrı <xref:System.Windows.Forms.Control.CreateGraphics%2A> denetim veya formun bir başvuru almak için yöntemi bir <xref:System.Drawing.Graphics> çizim yüzeyi bu denetim veya formun temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="1a625-116">Bir form veya zaten bir denetim çizmek istiyorsanız bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a625-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="1a625-117">-veya-</span><span class="sxs-lookup"><span data-stu-id="1a625-117">-or-</span></span>  
  
-   <span data-ttu-id="1a625-118">Oluşturma bir <xref:System.Drawing.Graphics> nesne öğesinden devralınan herhangi bir nesneden <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="1a625-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="1a625-119">Bu yaklaşım, zaten mevcut bir görüntüyü değiştirmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a625-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="1a625-120">Aşağıdaki bölümlerde, bu işlemlerin her biri hakkında ayrıntılar verir.</span><span class="sxs-lookup"><span data-stu-id="1a625-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="1a625-121">Boya olay işleyicisinde PaintEventArgs</span><span class="sxs-lookup"><span data-stu-id="1a625-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="1a625-122">Programlamada <xref:System.Windows.Forms.PaintEventHandler> denetimleri için veya <xref:System.Drawing.Printing.PrintDocument.PrintPage> için bir <xref:System.Drawing.Printing.PrintDocument>, bir grafik nesnesinin özelliklerinden biri olarak sağlanan <xref:System.Windows.Forms.PaintEventArgs> veya <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="1a625-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="1a625-123">Boyama olayını içinde PaintEventArgs grafik nesnesine başvuru almak için</span><span class="sxs-lookup"><span data-stu-id="1a625-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1.  <span data-ttu-id="1a625-124">Bildirme <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="1a625-125">Başvurmak için değişkenine atayın <xref:System.Drawing.Graphics> nesnesinin bir parçası olarak geçirilen <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="1a625-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3.  <span data-ttu-id="1a625-126">Form veya denetim boyama için kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a625-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="1a625-127">Aşağıdaki örnek nasıl başvurulacağını gösterir bir <xref:System.Drawing.Graphics> nesnesinden <xref:System.Windows.Forms.PaintEventArgs> içinde <xref:System.Windows.Forms.Control.Paint> olay:</span><span class="sxs-lookup"><span data-stu-id="1a625-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="1a625-128">CreateGraphics metodu</span><span class="sxs-lookup"><span data-stu-id="1a625-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="1a625-129">Ayrıca <xref:System.Windows.Forms.Control.CreateGraphics%2A> denetim veya formun bir başvuru almak için yöntemi bir <xref:System.Drawing.Graphics> çizim yüzeyi bu denetim veya formun temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="1a625-130">CreateGraphics metodu bir grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1a625-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
-   <span data-ttu-id="1a625-131">Çağrı <xref:System.Windows.Forms.Control.CreateGraphics%2A> üzerinde grafik işleme almak istediğiniz form veya denetim yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1a625-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="1a625-132">Bir görüntü nesneden oluşturun</span><span class="sxs-lookup"><span data-stu-id="1a625-132">Create from an Image Object</span></span>  
 <span data-ttu-id="1a625-133">Ayrıca, türetilen herhangi bir nesneden bir grafik nesnesinin oluşturabilirsiniz <xref:System.Drawing.Image> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a625-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="1a625-134">Bir görüntüden bir grafik nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1a625-134">To create a Graphics object from an Image</span></span>  
  
-   <span data-ttu-id="1a625-135">Çağrı <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> oluşturmak istediğiniz görüntü değişken adını sağlama yöntemi, bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="1a625-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="1a625-136">Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Drawing.Bitmap> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="1a625-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
>  <span data-ttu-id="1a625-137">Yalnızca oluşturabilirsiniz <xref:System.Drawing.Graphics> 16-bit, 24-bit ve 32-bit .bmp dosyaları gibi dizinlenmemiş .bmp dosyaları nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1a625-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="1a625-138">Her bir pikseli dizinlenmemiş .bmp dosyaları piksel bir renk tablosu için dizin tutun dizinli .bmp dosyaların aksine, bir renk tutar.</span><span class="sxs-lookup"><span data-stu-id="1a625-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="1a625-139">Çizim ve şekiller ve resimler düzenleme</span><span class="sxs-lookup"><span data-stu-id="1a625-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="1a625-140">Oluşturulduktan sonra bir <xref:System.Drawing.Graphics> nesne, çizgiler ve şekiller çizmek, metin, işleme veya görüntülemek ve görüntüleri işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a625-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="1a625-141">İle kullanılan asıl nesneleri <xref:System.Drawing.Graphics> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="1a625-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
-   <span data-ttu-id="1a625-142"><xref:System.Drawing.Pen> Sınıfı — satırlar çizme, şekiller anahat oluşturma veya diğer geometrik gösterimleri işleme için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="1a625-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
-   <span data-ttu-id="1a625-143"><xref:System.Drawing.Brush> Sınıfı — dolgulu şekiller, görüntü veya metin gibi grafik alanlarını doldurmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a625-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
-   <span data-ttu-id="1a625-144"><xref:System.Drawing.Font> Sınıfı — ne metin işlenirken kullanılacak şekilleri açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a625-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
-   <span data-ttu-id="1a625-145"><xref:System.Drawing.Color> Yapısı — görüntülemek için farklı renkler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a625-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="1a625-146">Oluşturduğunuz grafik nesnesini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1a625-146">To use the Graphics object you have created</span></span>  
  
-   <span data-ttu-id="1a625-147">Aradığınızı çizmek için yukarıda listelenen uygun nesne ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="1a625-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="1a625-148">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="1a625-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="1a625-149">İşlemek için</span><span class="sxs-lookup"><span data-stu-id="1a625-149">To render</span></span>|<span data-ttu-id="1a625-150">Bkz. </span><span class="sxs-lookup"><span data-stu-id="1a625-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="1a625-151">satırları</span><span class="sxs-lookup"><span data-stu-id="1a625-151">Lines</span></span>|[<span data-ttu-id="1a625-152">Nasıl yapılır: Windows Formunda Çizgi Çizme</span><span class="sxs-lookup"><span data-stu-id="1a625-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="1a625-153">Şekiller</span><span class="sxs-lookup"><span data-stu-id="1a625-153">Shapes</span></span>|[<span data-ttu-id="1a625-154">Nasıl yapılır: Anahatlı Şekil Çizme</span><span class="sxs-lookup"><span data-stu-id="1a625-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="1a625-155">Metin</span><span class="sxs-lookup"><span data-stu-id="1a625-155">Text</span></span>|[<span data-ttu-id="1a625-156">Nasıl yapılır: Bir Windows Formunda Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="1a625-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="1a625-157">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="1a625-157">Images</span></span>|[<span data-ttu-id="1a625-158">Nasıl yapılır: GDI+ ile Resim İşleme</span><span class="sxs-lookup"><span data-stu-id="1a625-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1a625-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a625-159">See also</span></span>

- [<span data-ttu-id="1a625-160">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="1a625-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="1a625-161">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="1a625-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="1a625-162">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="1a625-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="1a625-163">Nasıl yapılır: GDI+ ile Resim İşleme</span><span class="sxs-lookup"><span data-stu-id="1a625-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
