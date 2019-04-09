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
ms.openlocfilehash: 90511adf9caffe7952e270d6fe32dd85162a29d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089185"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="5bcda-102">Nasıl yapılır: Ekrana Mevcut bir Bit Eşlemi Çizme</span><span class="sxs-lookup"><span data-stu-id="5bcda-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="5bcda-103">Bu gibi durumlarda, mevcut bir görüntüyü kolayca ekranda çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bcda-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="5bcda-104">İlk oluşturmak gereken bir <xref:System.Drawing.Bitmap> nesnesi alan bir dosya adı, bit eşlem Oluşturucu <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="5bcda-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="5bcda-105">Bu oluşturucu, BMP, GIF, JPEG, PNG ve TIFF gibi birçok farklı dosya biçimleri görüntülerle kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5bcda-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="5bcda-106">Oluşturduktan sonra <xref:System.Drawing.Bitmap> nesne, bu geçirmek <xref:System.Drawing.Bitmap> nesnesini <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne.</span><span class="sxs-lookup"><span data-stu-id="5bcda-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bcda-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bcda-107">Example</span></span>  
 <span data-ttu-id="5bcda-108">Bu örnekte bir <xref:System.Drawing.Bitmap> nesneden bir JPEG dosyası ve daha sonra sol üst köşede ile bit eşlem çizer (60, 10).</span><span class="sxs-lookup"><span data-stu-id="5bcda-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="5bcda-109">Belirtilen konumda çizilmiş bit eşlem aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5bcda-109">The following illustration shows the bitmap drawn at the specified location:</span></span>  
  
 ![Belirtilen konumda bir görüntü gösteren ekran görüntüsü.](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bcda-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5bcda-111">Compiling the Code</span></span>  
 <span data-ttu-id="5bcda-112">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5bcda-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bcda-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bcda-113">See also</span></span>

- [<span data-ttu-id="5bcda-114">Windows Formlarında Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="5bcda-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="5bcda-115">Resimler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="5bcda-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
