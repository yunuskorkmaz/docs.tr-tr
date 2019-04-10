---
title: 'Nasıl yapılır: Küçük Resimler Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: b9afbac85dee90938e2bd55ebe19d3b02c0d66d5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341497"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="4e88c-102">Nasıl yapılır: Küçük Resimler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e88c-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="4e88c-103">Bir küçük resim, bir resmin küçük bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="4e88c-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="4e88c-104">Bir küçük resim çağırarak oluşturabileceğiniz <xref:System.Drawing.Image.GetThumbnailImage%2A> yöntemi bir <xref:System.Drawing.Image> nesne.</span><span class="sxs-lookup"><span data-stu-id="4e88c-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e88c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e88c-105">Example</span></span>  
 <span data-ttu-id="4e88c-106">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> JPG dosyası nesne.</span><span class="sxs-lookup"><span data-stu-id="4e88c-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="4e88c-107">Özgün resmin 640 piksel genişliği ve yüksekliği 479 piksel sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4e88c-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="4e88c-108">Kod 100 piksel genişliği ve yüksekliği 100 piksel olan bir küçük resim görüntüsü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4e88c-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="4e88c-109">Küçük resim görüntüsü aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4e88c-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="4e88c-110">![Küçük resim görüntüsü](./media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="4e88c-110">![Thumbnail Image](./media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e88c-111">Bu örnekte, bir geri çağırma yöntemi bildirildi ancak hiç kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="4e88c-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="4e88c-112">Bu, GDI +'in tüm sürümleri destekler.</span><span class="sxs-lookup"><span data-stu-id="4e88c-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e88c-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4e88c-113">Compiling the Code</span></span>  
 <span data-ttu-id="4e88c-114">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="4e88c-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="4e88c-115">Örneği çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="4e88c-115">To run the example, follow these steps:</span></span>  
  
1. <span data-ttu-id="4e88c-116">Yeni bir Windows Forms uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e88c-116">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="4e88c-117">Örnek kod formuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4e88c-117">Add the example code to the form.</span></span>  
  
3. <span data-ttu-id="4e88c-118">Form için bir işleyici oluşturma <xref:System.Windows.Forms.Control.Paint> olay</span><span class="sxs-lookup"><span data-stu-id="4e88c-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4. <span data-ttu-id="4e88c-119">İçinde <xref:System.Windows.Forms.Control.Paint> işleyicisi, çağrı `GetThumbnail` yöntemi ve pass `e` için <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="4e88c-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5. <span data-ttu-id="4e88c-120">Küçük resmini yapmak istediğiniz görüntü dosyasını bulun.</span><span class="sxs-lookup"><span data-stu-id="4e88c-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6. <span data-ttu-id="4e88c-121">İçinde `GetThumbnail` yöntemi, bir yol belirtin ve dosya adı görüntünüze.</span><span class="sxs-lookup"><span data-stu-id="4e88c-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7. <span data-ttu-id="4e88c-122">Örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4e88c-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="4e88c-123">Form üzerinde bir 100 x 100 küçük resim görünür.</span><span class="sxs-lookup"><span data-stu-id="4e88c-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e88c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e88c-124">See also</span></span>

- [<span data-ttu-id="4e88c-125">Resimler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4e88c-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="4e88c-126">Resimler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="4e88c-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
