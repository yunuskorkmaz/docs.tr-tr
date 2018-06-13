---
title: 'Nasıl yapılır: Alfa Karışım Kullanmayı Denetlemek için Birleştirme Modunu Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 55c6db1029c6823652ac29fca46f6f8dc4ec40d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527008"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="e413d-102">Nasıl yapılır: Alfa Karışım Kullanmayı Denetlemek için Birleştirme Modunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="e413d-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="e413d-103">Aşağıdaki özelliklere sahip bir ekran dışı bitmap oluşturmak istediğinizde zamanlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="e413d-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="e413d-104">Renkleri 255'den az olan alfa değerleri var.</span><span class="sxs-lookup"><span data-stu-id="e413d-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="e413d-105">Bit eşlem oluşturma birbiriyle karışık özelliği renkler alfa değildir.</span><span class="sxs-lookup"><span data-stu-id="e413d-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="e413d-106">Tamamlanan bit eşlem görüntülediğinizde, bit eşlem renkleri görüntüleme cihazı arka plan renkleri ile karıştırılan alfa ' dir.</span><span class="sxs-lookup"><span data-stu-id="e413d-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="e413d-107">Bu tür bir bitmap oluşturmak için boş bir oluşturmak <xref:System.Drawing.Bitmap> nesnesini genişletin ve ardından oluşturmak bir <xref:System.Drawing.Graphics> nesne tabanlı, bit eşlem'i.</span><span class="sxs-lookup"><span data-stu-id="e413d-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="e413d-108">Birleştirme modunu ayarlama <xref:System.Drawing.Graphics> nesnesine <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e413d-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e413d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e413d-109">Example</span></span>  
 <span data-ttu-id="e413d-110">Aşağıdaki örnekte bir <xref:System.Drawing.Graphics> nesne temel alarak bir <xref:System.Drawing.Bitmap> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e413d-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="e413d-111">Kod kullanan <xref:System.Drawing.Graphics> iki yarı saydam Fırçalar yanı sıra nesnesi (alfa 160 =) bit eşlem'i boyamak için.</span><span class="sxs-lookup"><span data-stu-id="e413d-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="e413d-112">Kod bir kırmızı elips ve yarı saydam fırçalarını kullanma yeşil bir elips doldurur.</span><span class="sxs-lookup"><span data-stu-id="e413d-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="e413d-113">Yeşil elipsin kırmızı elips çakışıyor, ancak yeşil kırmızı ile çünkü karıştırılan değil birleştirme modunu <xref:System.Drawing.Graphics> nesne ayarlanmış <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="e413d-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="e413d-114">Ekranda bit eşlem kod iki kez çizer: kez beyaz bir arka plan ve bir kez renkli arka plan üzerinde.</span><span class="sxs-lookup"><span data-stu-id="e413d-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="e413d-115">Arka plan renklerini ekranında ile üç nokta karıştırılan şekilde iki elips parçası olan bit eşlem pikselleri 160, alfasayısal bir bileşeninin sahip.</span><span class="sxs-lookup"><span data-stu-id="e413d-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="e413d-116">Aşağıdaki çizimde örnek kodu çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e413d-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="e413d-117">Üç nokta arka plan karıştırılan, ancak bunlar birbiriyle karışık değil unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e413d-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 <span data-ttu-id="e413d-118">![Kaynağı Kopyala](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span><span class="sxs-lookup"><span data-stu-id="e413d-118">![Source Copy](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span></span>  
  
 <span data-ttu-id="e413d-119">Kod örneği, bu deyimi içerir:</span><span class="sxs-lookup"><span data-stu-id="e413d-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="e413d-120">Birbirleriyle ve aynı zamanda arka plana sahip karıştırılan için üç nokta istiyorsanız, bu deyimi aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e413d-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="e413d-121">Aşağıdaki çizimde düzeltilmiş kod çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e413d-121">The following illustration shows the output of the revised code.</span></span>  
  
 <span data-ttu-id="e413d-122">![Kaynak üzerinde](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span><span class="sxs-lookup"><span data-stu-id="e413d-122">![Source Over](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e413d-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e413d-123">Compiling the Code</span></span>  
 <span data-ttu-id="e413d-124">Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="e413d-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e413d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e413d-125">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="e413d-126">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="e413d-126">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
