---
title: 'Nasıl yapılır: GDI+ ile Görüntü İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: 6f5b139c6831a065c85e9d9889c259c859a649cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524612"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="05621-102">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="05621-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="05621-103">Kullanabileceğiniz [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] uygulamalarınızdaki dosyaları olarak mevcut resimleri işlemek için.</span><span class="sxs-lookup"><span data-stu-id="05621-103">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render images that exist as files in your applications.</span></span> <span data-ttu-id="05621-104">Yeni bir nesne oluşturarak bunu bir <xref:System.Drawing.Image> sınıfı (gibi <xref:System.Drawing.Bitmap>), oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyini başvuruyor nesne ve çağırma <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="05621-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="05621-105">Görüntü grafik sınıfı tarafından temsil edilen çizim yüzeyine boyandığında.</span><span class="sxs-lookup"><span data-stu-id="05621-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="05621-106">Oluşturma ve tasarım zamanında resim dosyalarını düzenlemek için görüntü düzenleyicisi kullanın ve bunları işlemek [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="05621-106">You can use the Image Editor to create and edit image files at design time, and render them with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] at run time.</span></span> <span data-ttu-id="05621-107">Daha fazla bilgi için bkz: [simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="05621-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="05621-108">GDI + ile görüntü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="05621-108">To render an image with GDI+</span></span>  
  
1.  <span data-ttu-id="05621-109">Görüntülemek istediğiniz görüntüyü temsil eden bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05621-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="05621-110">Bu nesne öğesinden devralınan bir sınıf üyesi olmalıdır <xref:System.Drawing.Image>, gibi <xref:System.Drawing.Bitmap> veya <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="05621-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="05621-111">Bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="05621-111">An example is shown:</span></span>  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the   
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the   
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2.  <span data-ttu-id="05621-112">Oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="05621-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="05621-113">Daha fazla bilgi için bkz: [nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="05621-113">For more information, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of   
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of   
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3.  <span data-ttu-id="05621-114">Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> görüntü oluşturmak için grafik nesnenizin.</span><span class="sxs-lookup"><span data-stu-id="05621-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="05621-115">Çizilecek görüntü hem çizilecek olduğu koordinatları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05621-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="05621-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05621-116">See Also</span></span>  
 [<span data-ttu-id="05621-117">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="05621-117">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="05621-118">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="05621-118">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="05621-119">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="05621-119">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [<span data-ttu-id="05621-120">Nasıl yapılır: Bir Windows Formunda Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="05621-120">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [<span data-ttu-id="05621-121">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="05621-121">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="05621-122">Çizim çizgi veya kapalı şekiller</span><span class="sxs-lookup"><span data-stu-id="05621-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [<span data-ttu-id="05621-123">Simgeler için Görüntü Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="05621-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
