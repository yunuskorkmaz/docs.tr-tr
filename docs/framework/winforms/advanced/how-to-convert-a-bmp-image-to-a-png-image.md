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
ms.workload: dotnet
ms.openlocfilehash: 2ee2669c41f4ee558d9457cee7df0ae8425cf065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="ac796-102">Nasıl yapılır: BMP Resmini PNG Resmine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ac796-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="ac796-103">Görmemeleri, bir görüntü dosyası biçimden diğerine dönüştürmeyi isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ac796-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="ac796-104">Çağırarak bu dönüştürme kolayca yapabilirsiniz <xref:System.Drawing.Image.Save%2A> yöntemi <xref:System.Drawing.Image> sınıfı ve belirterek <xref:System.Drawing.Imaging.ImageFormat> istenen görüntü dosyası biçimi için.</span><span class="sxs-lookup"><span data-stu-id="ac796-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac796-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac796-105">Example</span></span>  
 <span data-ttu-id="ac796-106">Aşağıdaki örnek, bir türden BMP resmini yükler ve görüntü PNG biçiminde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="ac796-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac796-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ac796-107">Compiling the Code</span></span>  
 <span data-ttu-id="ac796-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ac796-108">This example requires:</span></span>  
  
-   <span data-ttu-id="ac796-109">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ac796-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="ac796-110">Bir başvuru `System.Drawing.Imaging` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ac796-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac796-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac796-111">See Also</span></span>  
 [<span data-ttu-id="ac796-112">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="ac796-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="ac796-113">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="ac796-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [<span data-ttu-id="ac796-114">Bit Eşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="ac796-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
