---
title: 'Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 1882ce9a140fb325c29411173ba7bde717bd3f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524761"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="e4dcc-102">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="e4dcc-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="e4dcc-103">Uygulamanızı bir belirli görüntü dosyası biçimi kaydedin olup olmadığını belirlemek için görüntü Kodlayıcıları bir bilgisayarda kullanılabilir listelemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="e4dcc-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="e4dcc-104"><xref:System.Drawing.Imaging.ImageCodecInfo> SAX <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statik yöntemler hangi görüntü Kodlayıcıları kullanılabilir belirleyebilmesi.</span><span class="sxs-lookup"><span data-stu-id="e4dcc-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="e4dcc-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e4dcc-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4dcc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4dcc-106">Example</span></span>  
 <span data-ttu-id="e4dcc-107">Aşağıdaki kod örneğinde yüklü kodlayıcılar listesi ve özellik değerlerine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="e4dcc-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4dcc-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e4dcc-108">Compiling the Code</span></span>  
 <span data-ttu-id="e4dcc-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e4dcc-109">This example requires:</span></span>  
  
-   <span data-ttu-id="e4dcc-110">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="e4dcc-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="e4dcc-111">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="e4dcc-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4dcc-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4dcc-112">See Also</span></span>  
 [<span data-ttu-id="e4dcc-113">Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme</span><span class="sxs-lookup"><span data-stu-id="e4dcc-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="e4dcc-114">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e4dcc-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
