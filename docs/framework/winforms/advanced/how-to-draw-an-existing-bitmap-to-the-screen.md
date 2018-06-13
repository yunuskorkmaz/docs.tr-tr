---
title: 'Nasıl yapılır: Ekrana Mevcut bir Bit Eşlemi Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: 2c66c1e2cdd0ee3f1a189b9a27284566210ef480
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522326"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="26582-102">Nasıl yapılır: Ekrana Mevcut bir Bit Eşlemi Çizme</span><span class="sxs-lookup"><span data-stu-id="26582-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="26582-103">Bu gibi durumlarda, var olan bir görüntüsünü kolayca ekranda çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26582-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="26582-104">Önce oluşturmak için gereken bir <xref:System.Drawing.Bitmap> bir dosya adı alan bit eşlem oluşturucu kullanılarak nesne <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="26582-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="26582-105">Bu oluşturucu, BMP, GIF, JPEG, PNG ve TIFF de dahil olmak üzere birkaç farklı dosya biçimleri görüntülerle kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26582-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="26582-106">Oluşturduktan sonra <xref:System.Drawing.Bitmap> nesne, bu geçirmek <xref:System.Drawing.Bitmap> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="26582-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26582-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="26582-107">Example</span></span>  
 <span data-ttu-id="26582-108">Bu örnekte bir <xref:System.Drawing.Bitmap> JPEG dosyadan nesne ve bit eşlem'i, sol üst köşede ile çizer (60, 10).</span><span class="sxs-lookup"><span data-stu-id="26582-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="26582-109">Aşağıda belirtilen konumda çizilmiş bit eşlem gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="26582-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="26582-110">![Görüntü konumu](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="26582-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="26582-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="26582-111">Compiling the Code</span></span>  
 <span data-ttu-id="26582-112">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="26582-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26582-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26582-113">See Also</span></span>  
 [<span data-ttu-id="26582-114">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="26582-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="26582-115">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="26582-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
