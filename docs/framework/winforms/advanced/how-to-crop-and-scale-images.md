---
title: "Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme"
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
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8fb5d527cd1047197f370c4a9a9b1f8f33461653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="c1326-102">Nasıl yapılır: Görüntü Kırpma ve Ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="c1326-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="c1326-103"><xref:System.Drawing.Graphics> Sınıfı sağlar birkaç <xref:System.Drawing.Graphics.DrawImage%2A> yöntemleri, bazıları sahip kırpma ve ölçeklendirme görüntülere kullanabileceğiniz kaynak ve hedef dikdörtgen parametreler.</span><span class="sxs-lookup"><span data-stu-id="c1326-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1326-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1326-104">Example</span></span>  
 <span data-ttu-id="c1326-105">Aşağıdaki örnek oluşturan bir <xref:System.Drawing.Image> disk dosyasından Apple.gif nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c1326-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="c1326-106">Kod özgün boyutunda tüm apple resim çizer.</span><span class="sxs-lookup"><span data-stu-id="c1326-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="c1326-107">Kod sonra çağırır <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi bir <xref:System.Drawing.Graphics> özgün apple görüntüden büyüktür hedef dikdörtgene apple görüntüsü bir kısmı çizmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="c1326-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="c1326-108"><xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi beşinci ve altıncı bağımsız değişkenler üçüncü tarafından dördüncü, belirtilen kaynak dikdörtgene bakarak çizmek için apple hangi kısmının belirler.</span><span class="sxs-lookup"><span data-stu-id="c1326-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="c1326-109">Bu durumda, apple eni yüzde 75'ini ve yüksekliğinin yüzde 75'ini kırpılır.</span><span class="sxs-lookup"><span data-stu-id="c1326-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="c1326-110"><xref:System.Drawing.Graphics.DrawImage%2A> Yöntemi kırpılmış apple çizmek nerede ve nasıl büyük hedef dikdörtgene bakarak kırpılmış apple yapmak için hangi belirler ikinci bağımsız değişkeni tarafından belirtilen.</span><span class="sxs-lookup"><span data-stu-id="c1326-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="c1326-111">Bu durumda hedef dikdörtgen yüzde 30 daha geniş ve yüzde 30'u orijinal görüntüden daha uzun olur.</span><span class="sxs-lookup"><span data-stu-id="c1326-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="c1326-112">Aşağıdaki çizimde, apple kırpılmış özgün apple ve ölçeklendirilmiş, gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1326-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 <span data-ttu-id="c1326-113">![Kırpma ve ölçeklendirme](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span><span class="sxs-lookup"><span data-stu-id="c1326-113">![Crop & Scale](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1326-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c1326-114">Compiling the Code</span></span>  
 <span data-ttu-id="c1326-115">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c1326-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="c1326-116">Değiştirdiğinizden emin olun `Apple.gif` bir görüntü dosyası adı ve, sisteminizde geçerli yolu.</span><span class="sxs-lookup"><span data-stu-id="c1326-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1326-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1326-117">See Also</span></span>  
 [<span data-ttu-id="c1326-118">Resimler, bit eşlemler ve meta dosyaları</span><span class="sxs-lookup"><span data-stu-id="c1326-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="c1326-119">Resimler, bit eşlemler, simgeler ve meta dosyaları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="c1326-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
