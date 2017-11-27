---
title: "Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 542dd132ece543b6a53a9e6d867b49fce4d15a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="e1833-102">Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e1833-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="e1833-103">Görmemeleri, bir görüntü dosyası biçimden diğerine dönüştürmeyi isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e1833-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="e1833-104">Çağırarak bu dönüştürme kolayca yapabilirsiniz <xref:System.Drawing.Image.Save%2A> yöntemi <xref:System.Drawing.Image> sınıfı ve belirterek <xref:System.Drawing.Imaging.ImageFormat> istenen görüntü dosyası biçimi için.</span><span class="sxs-lookup"><span data-stu-id="e1833-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1833-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1833-105">Example</span></span>  
 <span data-ttu-id="e1833-106">Aşağıdaki örnek, bir türden BMP resmini yükler ve görüntü PNG biçiminde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e1833-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1833-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e1833-107">Compiling the Code</span></span>  
 <span data-ttu-id="e1833-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e1833-108">This example requires:</span></span>  
  
-   <span data-ttu-id="e1833-109">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="e1833-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="e1833-110">Bir başvuru `System.Drawing.Imaging` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e1833-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1833-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1833-111">See Also</span></span>  
 [<span data-ttu-id="e1833-112">Nasıl yapılır: yüklenen Kodlayıcıları listeleme</span><span class="sxs-lookup"><span data-stu-id="e1833-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="e1833-113">Yönetilen GDI +'GÖRÜNTÜ Kodlayıcıları ve kod çözücüleri kullanma</span><span class="sxs-lookup"><span data-stu-id="e1833-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [<span data-ttu-id="e1833-114">Bit eşlem türleri</span><span class="sxs-lookup"><span data-stu-id="e1833-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
