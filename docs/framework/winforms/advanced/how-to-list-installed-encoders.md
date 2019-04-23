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
ms.openlocfilehash: ce297cb6d183bc63c8b276e30100aa4e864cd90d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078817"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="19a38-102">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="19a38-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="19a38-103">Uygulamanız için bir özel görüntü dosya biçimi tasarrufu yapıp yapamayacağınızı belirleyebilirsiniz için görüntü Kodlayıcıları bir bilgisayarda kullanılabilir listesinde isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19a38-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="19a38-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Sağlar sınıfını <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statik yöntemler hangi görüntü Kodlayıcıları kullanılabilir belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19a38-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="19a38-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="19a38-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19a38-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="19a38-106">Example</span></span>  
 <span data-ttu-id="19a38-107">Aşağıdaki kod örneği, yüklenen Kodlayıcıları listesi ve özellik değerlerine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="19a38-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="19a38-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="19a38-108">Compiling the Code</span></span>  
 <span data-ttu-id="19a38-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="19a38-109">This example requires:</span></span>  
  
-   <span data-ttu-id="19a38-110">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="19a38-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="19a38-111">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="19a38-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a38-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19a38-112">See also</span></span>

- [<span data-ttu-id="19a38-113">Nasıl yapılır: Yüklenen kod çözücüleri listeleme</span><span class="sxs-lookup"><span data-stu-id="19a38-113">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)
- [<span data-ttu-id="19a38-114">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="19a38-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
