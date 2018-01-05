---
title: "Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme"
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
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7993345a39a24c770fdd717580d428968dae836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="dd02e-102">Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme</span><span class="sxs-lookup"><span data-stu-id="dd02e-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="dd02e-103">Uygulamanızı belirli görüntü dosyası biçimi okuyup okuyamadığını belirlemeye görüntü kod çözücüleri bir bilgisayarda kullanılabilir listelemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="dd02e-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="dd02e-104"><xref:System.Drawing.Imaging.ImageCodecInfo> SAX <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statik yöntemler hangi görüntü kod çözücüleri kullanılabilir belirleyebilmesi.</span><span class="sxs-lookup"><span data-stu-id="dd02e-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="dd02e-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="dd02e-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd02e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd02e-106">Example</span></span>  
 <span data-ttu-id="dd02e-107">Aşağıdaki kod örneğinde, yüklenen kod çözücüleri listesi ve özellik değerlerine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="dd02e-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd02e-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="dd02e-108">Compiling the Code</span></span>  
 <span data-ttu-id="dd02e-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="dd02e-109">This example requires:</span></span>  
  
-   <span data-ttu-id="dd02e-110">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="dd02e-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="dd02e-111">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="dd02e-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd02e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd02e-112">See Also</span></span>  
 [<span data-ttu-id="dd02e-113">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="dd02e-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="dd02e-114">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="dd02e-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
