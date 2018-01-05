---
title: "Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme"
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
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec3ce7d2d933226162664826764c818eacf97afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="85c9a-102">Nasıl yapılır: Yüklenen Kodlayıcıları Listeleme</span><span class="sxs-lookup"><span data-stu-id="85c9a-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="85c9a-103">Uygulamanızı bir belirli görüntü dosyası biçimi kaydedin olup olmadığını belirlemek için görüntü Kodlayıcıları bir bilgisayarda kullanılabilir listelemek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="85c9a-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="85c9a-104"><xref:System.Drawing.Imaging.ImageCodecInfo> SAX <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statik yöntemler hangi görüntü Kodlayıcıları kullanılabilir belirleyebilmesi.</span><span class="sxs-lookup"><span data-stu-id="85c9a-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="85c9a-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>bir dizi döndürür <xref:System.Drawing.Imaging.ImageCodecInfo> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="85c9a-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85c9a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="85c9a-106">Example</span></span>  
 <span data-ttu-id="85c9a-107">Aşağıdaki kod örneğinde yüklü kodlayıcılar listesi ve özellik değerlerine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="85c9a-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85c9a-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="85c9a-108">Compiling the Code</span></span>  
 <span data-ttu-id="85c9a-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="85c9a-109">This example requires:</span></span>  
  
-   <span data-ttu-id="85c9a-110">Bir Windows Forms uygulaması.</span><span class="sxs-lookup"><span data-stu-id="85c9a-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="85c9a-111">A <xref:System.Windows.Forms.PaintEventArgs>, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="85c9a-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c9a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85c9a-112">See Also</span></span>  
 [<span data-ttu-id="85c9a-113">Nasıl yapılır: Yüklenen Kod Çözücüleri Listeleme</span><span class="sxs-lookup"><span data-stu-id="85c9a-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="85c9a-114">Yönetilen GDI+'da Görüntü Kodlayıcıları ve Kod Çözücüleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="85c9a-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
