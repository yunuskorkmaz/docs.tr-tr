---
title: "Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f49fc4b1e59879b9ecc67295610187fa2e5e80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a><span data-ttu-id="45710-102">Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma</span><span class="sxs-lookup"><span data-stu-id="45710-102">How to: Improve Performance by Avoiding Automatic Scaling</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="45710-103">otomatik olarak, hangi performans azalır çizerken görüntü ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="45710-103"> may automatically scale an image as you draw it, which would decrease performance.</span></span> <span data-ttu-id="45710-104">Alternatif olarak, hedef dikdörtgenin boyutlarını geçirerek görüntüsü ölçeklendirme denetleyebilirsiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45710-104">Alternatively, you can control the scaling of the image by passing the dimensions of the destination rectangle to the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
 <span data-ttu-id="45710-105">Aşağıdaki örnek, çağrısı <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi belirtir. bir sol üst köşesindeki (50, 30) ancak hedef dikdörtgen belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="45710-105">For example, the following call to the <xref:System.Drawing.Graphics.DrawImage%2A> method specifies an upper-left corner of (50, 30) but does not specify a destination rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 <span data-ttu-id="45710-106">Bu kolay sürümü olsa da <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi gerekli bağımsız değişken sayısı bakımından, mutlaka en etkin değil.</span><span class="sxs-lookup"><span data-stu-id="45710-106">Although this is the easiest version of the <xref:System.Drawing.Graphics.DrawImage%2A> method in terms of the number of required arguments, it is not necessarily the most efficient.</span></span> <span data-ttu-id="45710-107">Çözüm tarafından kullandıysanız [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (genellikle 96 inç başına nokta) depolanan çözümlemesi farklı <xref:System.Drawing.Image> nesnesi, sonra <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi görüntü ayarlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="45710-107">If the resolution used by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (usually 96 dots per inch) is different from the resolution stored in the <xref:System.Drawing.Image> object, then the <xref:System.Drawing.Graphics.DrawImage%2A> method will scale the image.</span></span> <span data-ttu-id="45710-108">Örneğin, varsayalım bir <xref:System.Drawing.Image> nesnesi 216 piksel genişliği ve 72 inç başına nokta saklı yatay çözünürlük değerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="45710-108">For example, suppose an <xref:System.Drawing.Image> object has a width of 216 pixels and a stored horizontal resolution value of 72 dots per inch.</span></span> <span data-ttu-id="45710-109">216/72 3, olduğundan <xref:System.Drawing.Graphics.DrawImage%2A> 96 inç başına nokta çözünürlükte 3 inç genişliğini sahip olması görüntü ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="45710-109">Because 216/72 is 3, <xref:System.Drawing.Graphics.DrawImage%2A> will scale the image so that it has a width of 3 inches at a resolution of 96 dots per inch.</span></span> <span data-ttu-id="45710-110">Diğer bir deyişle, <xref:System.Drawing.Graphics.DrawImage%2A> 96 x 3 = 288 genişliğini içeren bir görüntü görüntüler piksel.</span><span class="sxs-lookup"><span data-stu-id="45710-110">That is, <xref:System.Drawing.Graphics.DrawImage%2A> will display an image that has a width of 96x3 = 288 pixels.</span></span>  
  
 <span data-ttu-id="45710-111">Ekran çözünürlüğünü 96 inç başına nokta farklı olsa bile [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ekran çözünürlüğünü 96 inç başına nokta değilmiş gibi ölçek görüntü büyük olasılıkla olur.</span><span class="sxs-lookup"><span data-stu-id="45710-111">Even if your screen resolution is different from 96 dots per inch, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] will probably scale the image as if the screen resolution were 96 dots per inch.</span></span> <span data-ttu-id="45710-112">Çünkü bir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> nesnesi bir cihaz bağlamı ile ilişkili olan ve ne zaman [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sonucu ekran çözünürlüğü için cihaz bağlamı olan genellikle gerçek ekran çözünürlüğünü bakılmaksızın 96 sorguları.</span><span class="sxs-lookup"><span data-stu-id="45710-112">That is because a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> object is associated with a device context, and when [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] queries the device context for the screen resolution, the result is usually 96, regardless of the actual screen resolution.</span></span> <span data-ttu-id="45710-113">Hedef dikdörtgende belirterek otomatik ölçeklendirmeyi önleyebilirsiniz <xref:System.Drawing.Graphics.DrawImage%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45710-113">You can avoid automatic scaling by specifying the destination rectangle in the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45710-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="45710-114">Example</span></span>  
 <span data-ttu-id="45710-115">Aşağıdaki örnekte iki kez aynı resim çizer.</span><span class="sxs-lookup"><span data-stu-id="45710-115">The following example draws the same image twice.</span></span> <span data-ttu-id="45710-116">İlk durumda, genişlik ve yükseklik hedef dikdörtgenin belirtilmedi ve otomatik olarak ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="45710-116">In the first case, the width and height of the destination rectangle are not specified, and the image is automatically scaled.</span></span> <span data-ttu-id="45710-117">İkinci durumda, genişlik ve yükseklik (piksel cinsinden ölçülür) hedef dikdörtgenin genişliği ve yüksekliği orijinal görüntünün aynı olması için belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="45710-117">In the second case, the width and height (measured in pixels) of the destination rectangle are specified to be the same as the width and height of the original image.</span></span> <span data-ttu-id="45710-118">Aşağıdaki çizimde, iki kez çizilir resim göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="45710-118">The following illustration shows the image rendered twice.</span></span>  
  
 <span data-ttu-id="45710-119">![Ölçeklendirilmiş doku](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span><span class="sxs-lookup"><span data-stu-id="45710-119">![Scaled Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="45710-120">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="45710-120">Compiling the Code</span></span>  
 <span data-ttu-id="45710-121">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="45710-121">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="45710-122">Texture.jpg bir görüntü adı ve, sisteminizde geçerli yolu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="45710-122">Replace Texture.jpg with an image name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45710-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45710-123">See Also</span></span>  
 [<span data-ttu-id="45710-124">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="45710-124">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="45710-125">Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="45710-125">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
