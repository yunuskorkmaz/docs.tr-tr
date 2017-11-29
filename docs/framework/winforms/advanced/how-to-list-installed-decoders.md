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
ms.openlocfilehash: 17cbdebfa6cbb0cacacd923de4bd22125c812938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="61d78-102">Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme</span><span class="sxs-lookup"><span data-stu-id="61d78-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="61d78-103">Uygulamanızı belirli görüntü dosyası biçimi okuyup okuyamadığını belirlemeye görüntü kod çözücüleri bir bilgisayarda kullanılabilir listelemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="61d78-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="61d78-104"><xref:System.Drawing.Imaging.ImageCodecInfo> SAX <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statik yöntemler hangi görüntü kod çözücüleri kullanılabilir belirleyebilmesi.</span><span class="sxs-lookup"><span data-stu-id="61d78-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="61d78-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="61d78-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61d78-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="61d78-106">Example</span></span>  
 <span data-ttu-id="61d78-107">Aşağıdaki kod örneğinde, yüklenen kod çözücüleri listesi ve özellik değerlerine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="61d78-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61d78-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="61d78-108">Compiling the Code</span></span>  
 <span data-ttu-id="61d78-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="61d78-109">This example requires:</span></span>  
  
-   <span data-ttu-id="61d78-110">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="61d78-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="61d78-111">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="61d78-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d78-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61d78-112">See Also</span></span>  
 [<span data-ttu-id="61d78-113">Nasıl yapılır: yüklenen Kodlayıcıları listeleme</span><span class="sxs-lookup"><span data-stu-id="61d78-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="61d78-114">Yönetilen GDI +'GÖRÜNTÜ Kodlayıcıları ve kod çözücüleri kullanma</span><span class="sxs-lookup"><span data-stu-id="61d78-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
