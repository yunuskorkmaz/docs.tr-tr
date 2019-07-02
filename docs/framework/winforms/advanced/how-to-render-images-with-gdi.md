---
title: 'Nasıl yapılır: GDI+ ile Resim İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: da637152737510847830e885fdcd065ab92f16b3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505753"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="d3d54-102">Nasıl yapılır: GDI+ ile Resim İşleme</span><span class="sxs-lookup"><span data-stu-id="d3d54-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="d3d54-103">Uygulamalarınızda dosyaları olarak mevcut görüntülerini işlemek için GDI +'da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3d54-103">You can use GDI+ to render images that exist as files in your applications.</span></span> <span data-ttu-id="d3d54-104">Yeni bir nesne oluşturarak bunu bir <xref:System.Drawing.Image> sınıfı (gibi <xref:System.Drawing.Bitmap>), oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyi başvuran nesne ve çağırma <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="d3d54-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="d3d54-105">Görüntü grafik sınıfı tarafından temsil edilen çizim yüzeyine boyanacak.</span><span class="sxs-lookup"><span data-stu-id="d3d54-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="d3d54-106">Oluşturma ve tasarım zamanında resim dosyalarını düzenlemek için görüntü Düzenleyicisi'ni kullanın ve bunları GDI + ile çalışma zamanında oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d3d54-106">You can use the Image Editor to create and edit image files at design time, and render them with GDI+ at run time.</span></span> <span data-ttu-id="d3d54-107">Daha fazla bilgi için [simgeler için görüntü Düzenleyicisi](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="d3d54-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="d3d54-108">GDI + ile görüntü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d3d54-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="d3d54-109">Görüntülemek istediğiniz görüntüyü temsil eden bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3d54-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="d3d54-110">Bu nesne öğesinden devralınan bir sınıf üyesi olmalıdır <xref:System.Drawing.Image>, gibi <xref:System.Drawing.Bitmap> veya <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="d3d54-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="d3d54-111">Bir örnek gösterilir:</span><span class="sxs-lookup"><span data-stu-id="d3d54-111">An example is shown:</span></span>  
  
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
  
2. <span data-ttu-id="d3d54-112">Oluşturma bir <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="d3d54-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="d3d54-113">Daha fazla bilgi için [nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="d3d54-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3. <span data-ttu-id="d3d54-114">Çağrı <xref:System.Drawing.Graphics.DrawImage%2A> görüntüsünü işlemek için grafik nesne.</span><span class="sxs-lookup"><span data-stu-id="d3d54-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="d3d54-115">Çizilecek görüntü hem çizilecek olduğu koordinatları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3d54-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d3d54-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3d54-116">See also</span></span>

- [<span data-ttu-id="d3d54-117">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="d3d54-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="d3d54-118">Nasıl yapılır: Çizim için grafik nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3d54-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="d3d54-119">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="d3d54-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="d3d54-120">Nasıl yapılır: Bir Windows formunda metin çizme</span><span class="sxs-lookup"><span data-stu-id="d3d54-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="d3d54-121">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="d3d54-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="d3d54-122">Çizim çizgi veya kapalı şekiller</span><span class="sxs-lookup"><span data-stu-id="d3d54-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="d3d54-123">Simgeler için Görüntü Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="d3d54-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
