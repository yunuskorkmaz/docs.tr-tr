---
title: 'Nasıl yapılır: Alfa karışım kullanmayı denetlemek için birleştirme modunu kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 2e00b0b9b22bc8dcdd1c63494f1bc5854bc4f033
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632016"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="0e4a1-102">Nasıl yapılır: Alfa karışım kullanmayı denetlemek için birleştirme modunu kullanma</span><span class="sxs-lookup"><span data-stu-id="0e4a1-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="0e4a1-103">Aşağıdaki özelliklere sahip çizerek bir bit eşlem oluşturmak istediğiniz zaman zamanlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="0e4a1-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="0e4a1-104">Renkleri 255'den küçük olan alfa değerleri var.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="0e4a1-105">Bit eşlem oluşturma gibi birbiriyle karışık özelliği renkler alfa değildir.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="0e4a1-106">Tamamlanmış bir bit eşlem görüntülediğinizde, bit eşlemde görüntü cihazı üzerinde arka plan renkleri ile karışık alfa renklerdir.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="0e4a1-107">Böyle bir bit eşlem oluşturmak için boş bir oluşturmak <xref:System.Drawing.Bitmap> nesnesi ve ardından oluşturmak bir <xref:System.Drawing.Graphics> nesne tabanlı, bit eşlem.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="0e4a1-108">Birleştirme modunu ayarlama <xref:System.Drawing.Graphics> nesnesini <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e4a1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e4a1-109">Example</span></span>  
 <span data-ttu-id="0e4a1-110">Aşağıdaki örnek, oluşturur bir <xref:System.Drawing.Graphics> nesnesini temel alan bir <xref:System.Drawing.Bitmap> nesne.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="0e4a1-111">Kod <xref:System.Drawing.Graphics> iki yarı saydam fırçalarla Fırçalar yanı sıra nesnesi (alpha 160 =) üzerinde bir bit eşlem boyamak için.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="0e4a1-112">Kod, kırmızı bir elips ve yarı saydam fırçalarla fırçalarını kullanma yeşil bir elipsin doldurur.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="0e4a1-113">Yeşil elips kırmızı elips çakışıyor, ancak yeşil kırmızı ile çünkü harmanlanan olmayan birleştirme modunu <xref:System.Drawing.Graphics> nesne ayarlandığında <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="0e4a1-114">Ekranda bir bit eşlem kod iki kez çizer: bir kez beyaz arka plan üzerinde ve bir kez renkli arka plan üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="0e4a1-115">Üç nokta simgesini ekranın arka plan renkleriyle ile karışık şekilde iki üç noktayı parçası olan bit eşlem pikselleri 160, bir alfa bileşeni vardır.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="0e4a1-116">Kod örneği, çıktı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="0e4a1-117">Üç nokta arka plan ile karışık, ancak bunlar birbiriyle karışık değil unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 <span data-ttu-id="0e4a1-118">![Kopyalama kaynağı](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span><span class="sxs-lookup"><span data-stu-id="0e4a1-118">![Source Copy](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span></span>  
  
 <span data-ttu-id="0e4a1-119">Kod örneği, bu deyimi içerir:</span><span class="sxs-lookup"><span data-stu-id="0e4a1-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="0e4a1-120">Birbiriyle yanı sıra arka plan ile karışık için üç noktayı istiyorsanız, o ifadeyi şu şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0e4a1-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="0e4a1-121">Düzeltilmiş kodun çıktısı aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-121">The following illustration shows the output of the revised code.</span></span>  
  
 <span data-ttu-id="0e4a1-122">![Kaynak üzerinde](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span><span class="sxs-lookup"><span data-stu-id="0e4a1-122">![Source Over](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0e4a1-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0e4a1-123">Compiling the Code</span></span>  
 <span data-ttu-id="0e4a1-124">Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e4a1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e4a1-125">See also</span></span>
- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="0e4a1-126">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e4a1-126">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
