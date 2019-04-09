---
title: 'Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: c92b8010def2f77f859ee0bd9cdb1ed51dd15f27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079423"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="d5501-102">Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme</span><span class="sxs-lookup"><span data-stu-id="d5501-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="d5501-103">Uygulamanızın belirli resim dosyası biçimi erişip erişemeyeceğini belirlemek için görüntü kod çözücüleri bir bilgisayarda kullanılabilir listesinde isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5501-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="d5501-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Sağlar sınıfını <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statik yöntemler hangi görüntü kod çözücüleri kullanılabilir belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5501-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> <span data-ttu-id="d5501-105">Bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d5501-105">returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5501-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5501-106">Example</span></span>  
 <span data-ttu-id="d5501-107">Aşağıdaki kod örneği, yüklenen kod çözücüleri listesi ve özellik değerlerine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d5501-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d5501-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d5501-108">Compiling the Code</span></span>  
 <span data-ttu-id="d5501-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d5501-109">This example requires:</span></span>  
  
-   <span data-ttu-id="d5501-110">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d5501-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="d5501-111">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d5501-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5501-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5501-112">See also</span></span>

- [<span data-ttu-id="d5501-113">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="d5501-113">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="d5501-114">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="d5501-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
