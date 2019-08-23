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
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923748"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="c75a1-102">Nasıl yapılır: Küçük Resimler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c75a1-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="c75a1-103">Küçük resim görüntüsü görüntünün küçük bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="c75a1-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="c75a1-104"><xref:System.Drawing.Image.GetThumbnailImage%2A> Bir<xref:System.Drawing.Image> nesnenin yöntemini çağırarak bir küçük resim görüntüsü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c75a1-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c75a1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c75a1-105">Example</span></span>  
 <span data-ttu-id="c75a1-106">Aşağıdaki örnek, bir jpg <xref:System.Drawing.Image> dosyasından bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c75a1-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="c75a1-107">Orijinal görüntüde 640 piksellik bir genişlik ve 479 piksellik yükseklik bulunur.</span><span class="sxs-lookup"><span data-stu-id="c75a1-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="c75a1-108">Kod, 100 piksel genişlik ve 100 piksel yüksekliğinde bir küçük resim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c75a1-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="c75a1-109">Aşağıdaki çizim, küçük resim görüntüsünü göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c75a1-109">The following illustration shows the thumbnail image:</span></span>  
  
 ![Çıkış küçük resmini gösteren ekran görüntüsü.](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> <span data-ttu-id="c75a1-111">Bu örnekte, bir geri çağırma yöntemi tanımlanmış, ancak hiç kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="c75a1-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="c75a1-112">Bu, tüm GDI+ sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="c75a1-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c75a1-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c75a1-113">Compiling the Code</span></span>  
 <span data-ttu-id="c75a1-114">Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan gerektirir `e`.</span><span class="sxs-lookup"><span data-stu-id="c75a1-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="c75a1-115">Örneği çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="c75a1-115">To run the example, follow these steps:</span></span>  
  
1. <span data-ttu-id="c75a1-116">Yeni bir Windows Forms uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c75a1-116">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="c75a1-117">Forma örnek kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c75a1-117">Add the example code to the form.</span></span>  
  
3. <span data-ttu-id="c75a1-118">Formun <xref:System.Windows.Forms.Control.Paint> olayı için bir işleyici oluşturun</span><span class="sxs-lookup"><span data-stu-id="c75a1-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4. <span data-ttu-id="c75a1-119">İşleyicisinde metodunu çağırın ve `e` için<xref:System.Windows.Forms.PaintEventArgs>geçişyapın. <xref:System.Windows.Forms.Control.Paint> `GetThumbnail`</span><span class="sxs-lookup"><span data-stu-id="c75a1-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5. <span data-ttu-id="c75a1-120">Küçük resmini oluşturmak istediğiniz bir görüntü dosyası bulun.</span><span class="sxs-lookup"><span data-stu-id="c75a1-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6. <span data-ttu-id="c75a1-121">`GetThumbnail` Yönteminde, görüntünüzün yolunu ve dosya adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="c75a1-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7. <span data-ttu-id="c75a1-122">Örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c75a1-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="c75a1-123">Formda 100 ile 100 arasında bir küçük resim görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c75a1-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75a1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c75a1-124">See also</span></span>

- [<span data-ttu-id="c75a1-125">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="c75a1-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="c75a1-126">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="c75a1-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
