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
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182512"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="0dff1-102">Nasıl yapılır: GDI+ ile Resim İşleme</span><span class="sxs-lookup"><span data-stu-id="0dff1-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="0dff1-103">Uygulamalarınızda dosya olarak var olan görüntüleri işlemek için GDI+'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dff1-103">You can use GDI+ to render images that exist as files in your applications.</span></span> <span data-ttu-id="0dff1-104">Bunu, bir sınıfın yeni bir <xref:System.Drawing.Image> nesnesini <xref:System.Drawing.Bitmap>(örneğin), <xref:System.Drawing.Graphics> kullanmak istediğiniz çizim yüzeyine başvuran bir nesne <xref:System.Drawing.Graphics.DrawImage%2A> oluşturarak <xref:System.Drawing.Graphics> ve nesnenin yöntemini çağırarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="0dff1-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="0dff1-105">Görüntü grafik sınıfı tarafından temsil edilen çizim yüzeyine boyanacaktır.</span><span class="sxs-lookup"><span data-stu-id="0dff1-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="0dff1-106">Görüntü Düzenleyicisi'ni tasarım zamanında görüntü dosyalarını oluşturmak ve düzenlemek ve çalışma zamanında GDI+ ile işlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0dff1-106">You can use the Image Editor to create and edit image files at design time, and render them with GDI+ at run time.</span></span> <span data-ttu-id="0dff1-107">Daha fazla bilgi [için Simgeler için Resim Düzenleyicisi'ne](/cpp/windows/image-editor-for-icons)bakın.</span><span class="sxs-lookup"><span data-stu-id="0dff1-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="0dff1-108">GDI+ ile görüntü işlemek için</span><span class="sxs-lookup"><span data-stu-id="0dff1-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="0dff1-109">Görüntülemek istediğiniz görüntüyü temsil eden bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0dff1-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="0dff1-110">Bu nesne, devralan bir sınıfın üyesi <xref:System.Drawing.Image>olmalıdır <xref:System.Drawing.Bitmap> , <xref:System.Drawing.Imaging.Metafile>gibi veya .</span><span class="sxs-lookup"><span data-stu-id="0dff1-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="0dff1-111">Bir örnek gösterilir:</span><span class="sxs-lookup"><span data-stu-id="0dff1-111">An example is shown:</span></span>  
  
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
  
2. <span data-ttu-id="0dff1-112">Kullanmak <xref:System.Drawing.Graphics> istediğiniz çizim yüzeyini temsil eden bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0dff1-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="0dff1-113">Daha fazla bilgi için [bkz: Çizim için Grafik Nesneleri Oluşturma](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="0dff1-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3. <span data-ttu-id="0dff1-114">Görüntüyü <xref:System.Drawing.Graphics.DrawImage%2A> işlemek için grafik nesnenizi arayın.</span><span class="sxs-lookup"><span data-stu-id="0dff1-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="0dff1-115">Hem çizilecek görüntüyü hem de çizilecek koordinatları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0dff1-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0dff1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dff1-116">See also</span></span>

- [<span data-ttu-id="0dff1-117">Grafik Programlamaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="0dff1-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="0dff1-118">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0dff1-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="0dff1-119">GDI+'da Kalemler, Çizgiler ve Dikdörtgenler</span><span class="sxs-lookup"><span data-stu-id="0dff1-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="0dff1-120">Nasıl yapılır: Bir Windows Formunda Metin Çizme</span><span class="sxs-lookup"><span data-stu-id="0dff1-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="0dff1-121">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="0dff1-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="0dff1-122">Çizim Çizgileri veya Kapalı Şekiller</span><span class="sxs-lookup"><span data-stu-id="0dff1-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="0dff1-123">Simgeler için Görüntü Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="0dff1-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
