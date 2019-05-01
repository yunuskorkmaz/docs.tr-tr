---
title: 'Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 4257431881565f9160f45795111d374cc680dedd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937585"
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="573c0-102">Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="573c0-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="573c0-103"><xref:System.Drawing.Graphics> Sınıfı sağlayan çeşitli <xref:System.Drawing.Graphics.DrawImage%2A> bazıları kırpma ve ölçeklendirme görüntüleri için kullanabileceğiniz kaynak ve hedef dikdörtgenin parametreleri olan yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="573c0-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="573c0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="573c0-104">Example</span></span>  
 <span data-ttu-id="573c0-105">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> disk dosyasından Apple.gif nesnesi.</span><span class="sxs-lookup"><span data-stu-id="573c0-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="573c0-106">Kod, tüm apple görüntünün özgün boyutunda çizer.</span><span class="sxs-lookup"><span data-stu-id="573c0-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="573c0-107">Ardından kod çağırır <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> orijinal apple görüntüden daha büyük bir hedef dikdörtgenin içindeki bir kısmını apple görüntüsü çizmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="573c0-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="573c0-108"><xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi tarafından üçüncü, dördüncü, belirtilen kaynak dikdörtgene beşinci ve altıncı bağımsız değişkenler bakarak çizmek için apple hangi kısmının belirler.</span><span class="sxs-lookup"><span data-stu-id="573c0-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="573c0-109">Bu durumda, apple yüzde 75'genişliğinin ve yüksekliğinin yüzde 75'kırpılır.</span><span class="sxs-lookup"><span data-stu-id="573c0-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="573c0-110"><xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi belirler kırpılmış apple nerede ve ne kadar büyük hedef dikdörtgene bakarak kırpılmış apple yapmak için bu değer ikinci bağımsız değişkeni tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="573c0-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="573c0-111">Bu durumda, hedef dikdörtgenin yüzde 30 daha geniş ve özgün resimden uzun yüzde 30 ' dir.</span><span class="sxs-lookup"><span data-stu-id="573c0-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="573c0-112">Apple kırpılmış orijinal apple ve genişletilmiş, aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="573c0-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 ![Özgün görüntü ve kırpılmış görüntünün ekran görüntüsü.](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="573c0-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="573c0-114">Compiling the Code</span></span>  
 <span data-ttu-id="573c0-115">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="573c0-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="573c0-116">Değiştirdiğinizden emin olun `Apple.gif` bir resim dosyası adı ve sisteminize göre geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="573c0-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573c0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="573c0-117">See also</span></span>

- [<span data-ttu-id="573c0-118">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="573c0-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="573c0-119">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="573c0-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
