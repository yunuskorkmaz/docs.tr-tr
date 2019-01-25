---
title: 'Nasıl yapılır: Yüklenen kod çözücüleri listeleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: 3d24eadca23aa6da4a8557cc2db3189b6e232e78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605217"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="7442d-102">Nasıl yapılır: Yüklenen kod çözücüleri listeleme</span><span class="sxs-lookup"><span data-stu-id="7442d-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="7442d-103">Uygulamanızın belirli resim dosyası biçimi erişip erişemeyeceğini belirlemek için görüntü kod çözücüleri bir bilgisayarda kullanılabilir listesinde isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7442d-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="7442d-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Sağlar sınıfını <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statik yöntemler hangi görüntü kod çözücüleri kullanılabilir belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7442d-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="7442d-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7442d-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7442d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7442d-106">Example</span></span>  
 <span data-ttu-id="7442d-107">Aşağıdaki kod örneği, yüklenen kod çözücüleri listesi ve özellik değerlerine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="7442d-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7442d-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7442d-108">Compiling the Code</span></span>  
 <span data-ttu-id="7442d-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7442d-109">This example requires:</span></span>  
  
-   <span data-ttu-id="7442d-110">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="7442d-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="7442d-111">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="7442d-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7442d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7442d-112">See also</span></span>
- [<span data-ttu-id="7442d-113">Nasıl yapılır: Yüklenen Kodlayıcıları listeleme</span><span class="sxs-lookup"><span data-stu-id="7442d-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="7442d-114">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="7442d-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
