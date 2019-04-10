---
title: 'Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: 3072c07781a8e8e57b64b48e5b4c304c2a0a0efb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217022"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="f19a2-102">Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f19a2-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="f19a2-103">Bunun aktardığınızda genellikle, bir görüntü dosyası biçiminden dönüştürme yapmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f19a2-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="f19a2-104">Çağırarak bu dönüştürme kolayca yapabilirsiniz <xref:System.Drawing.Image.Save%2A> yöntemi <xref:System.Drawing.Image> sınıfı ve belirterek <xref:System.Drawing.Imaging.ImageFormat> için istenen resim dosyası biçimi.</span><span class="sxs-lookup"><span data-stu-id="f19a2-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f19a2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f19a2-105">Example</span></span>  
 <span data-ttu-id="f19a2-106">Aşağıdaki örnek, bir türden bir BMP görüntüsünü yükler ve görüntü PNG biçiminde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f19a2-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f19a2-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f19a2-107">Compiling the Code</span></span>  
 <span data-ttu-id="f19a2-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f19a2-108">This example requires:</span></span>  
  
-   <span data-ttu-id="f19a2-109">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="f19a2-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="f19a2-110">Bir başvuru `System.Drawing.Imaging` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="f19a2-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19a2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f19a2-111">See also</span></span>

- [<span data-ttu-id="f19a2-112">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="f19a2-112">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="f19a2-113">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f19a2-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="f19a2-114">Bit Eşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="f19a2-114">Types of Bitmaps</span></span>](types-of-bitmaps.md)
