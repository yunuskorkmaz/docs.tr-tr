---
title: 'Nasıl yapılır: Bir kodlayıcı tarafından desteklenen parametreleri belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 56b78a0cdfcb9ac8e3a7dbc12527fcc59f0524fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723413"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="9e96a-102">Nasıl yapılır: Bir kodlayıcı tarafından desteklenen parametreleri belirleme</span><span class="sxs-lookup"><span data-stu-id="9e96a-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="9e96a-103">Kalite ve sıkıştırma düzeyi gibi görüntü parametreleri ayarlayabilirsiniz ancak belirtilen görüntü Kodlayıcı tarafından desteklenen parametreleri bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e96a-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="9e96a-104"><xref:System.Drawing.Image> Sağlar sınıfını <xref:System.Drawing.Image.GetEncoderParameterList%2A> yöntemi görüntü parametreleri için belirli bir kodlayıcı desteklenen belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e96a-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="9e96a-105">Size encoder bir GUID ile belirtin.</span><span class="sxs-lookup"><span data-stu-id="9e96a-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="9e96a-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A> Yöntemi, bir dizi döndürür <xref:System.Drawing.Imaging.EncoderParameter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9e96a-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e96a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e96a-107">Example</span></span>  
 <span data-ttu-id="9e96a-108">Aşağıdaki kod örneği, JPEG Kodlayıcı için desteklenen parametreler çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9e96a-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="9e96a-109">Parametre kategorileri ve ilişkili GUID'lerinin listesini kullanın <xref:System.Drawing.Imaging.Encoder> her parametre için bir kategori belirlemek için sınıfına genel bakış.</span><span class="sxs-lookup"><span data-stu-id="9e96a-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9e96a-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="9e96a-110">Compiling the Code</span></span>  
 <span data-ttu-id="9e96a-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9e96a-111">This example requires:</span></span>  
  
-   <span data-ttu-id="9e96a-112">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="9e96a-112">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="9e96a-113">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9e96a-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e96a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e96a-114">See also</span></span>
- [<span data-ttu-id="9e96a-115">Nasıl yapılır: Yüklenen Kodlayıcıları listeleme</span><span class="sxs-lookup"><span data-stu-id="9e96a-115">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="9e96a-116">Bit Eşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="9e96a-116">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
- [<span data-ttu-id="9e96a-117">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="9e96a-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
