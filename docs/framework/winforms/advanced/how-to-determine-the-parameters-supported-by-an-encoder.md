---
title: "Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3304adc9ab22d12905bd2a6c3739d909387d82cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="f6f9d-102">Nasıl yapılır: Bir Kodlayıcı Tarafından Desteklenen Parametreleri Belirleme</span><span class="sxs-lookup"><span data-stu-id="f6f9d-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="f6f9d-103">Kalite ve sıkıştırma düzeyi gibi görüntü parametreleri değiştirebilirsiniz ancak hangi parametreleri verilen görüntü Kodlayıcı tarafından desteklenen bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="f6f9d-104"><xref:System.Drawing.Image> SAX <xref:System.Drawing.Image.GetEncoderParameterList%2A> yöntemi hangi görüntü parametreleri için belirli bir kodlayıcı desteklenen belirleyebilmesi.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="f6f9d-105">Kodlayıcı ile bir GUID belirtin.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="f6f9d-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A> Yöntemi bir dizi döndürür <xref:System.Drawing.Imaging.EncoderParameter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f9d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6f9d-107">Example</span></span>  
 <span data-ttu-id="f6f9d-108">Aşağıdaki kod örneği, JPEG Kodlayıcı için desteklenen parametreler çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="f6f9d-109">Parametre kategorileri ve ilişkili GUID içinde listesini kullanın <xref:System.Drawing.Imaging.Encoder> her parametre için kategori belirlemek için sınıf genel bakış.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6f9d-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f6f9d-110">Compiling the Code</span></span>  
 <span data-ttu-id="f6f9d-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f6f9d-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f6f9d-112">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-112">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="f6f9d-113">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f9d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6f9d-114">See Also</span></span>  
 [<span data-ttu-id="f6f9d-115">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="f6f9d-115">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="f6f9d-116">Bit Eşlem Türleri</span><span class="sxs-lookup"><span data-stu-id="f6f9d-116">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [<span data-ttu-id="f6f9d-117">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f6f9d-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
