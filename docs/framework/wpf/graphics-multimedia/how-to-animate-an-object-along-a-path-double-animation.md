---
title: "Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6a461b741675a18ac1e3544b17a9bbe9a8d18547
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="cf624-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)</span><span class="sxs-lookup"><span data-stu-id="cf624-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="cf624-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> sınıfı tarafından tanımlanan bir yol boyunca bir nesneyi taşımak için bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cf624-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf624-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf624-104">Example</span></span>  
 <span data-ttu-id="cf624-105">Aşağıdaki örnekte iki kullanan <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> dikdörtgeni geometrik yol boyunca taşımak için nesneler:</span><span class="sxs-lookup"><span data-stu-id="cf624-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="cf624-106">İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır <xref:System.Windows.Media.TranslateTransform.X%2A> , <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanan.</span><span class="sxs-lookup"><span data-stu-id="cf624-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="cf624-107">Bu dikdörtgeni yol boyunca yatay olarak taşır.</span><span class="sxs-lookup"><span data-stu-id="cf624-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="cf624-108">İkinci <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır <xref:System.Windows.Media.TranslateTransform.Y%2A> , <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanan.</span><span class="sxs-lookup"><span data-stu-id="cf624-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="cf624-109">Bu dikdörtgeni yol boyunca dikey olarak taşır.</span><span class="sxs-lookup"><span data-stu-id="cf624-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="cf624-110">Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="cf624-110">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="cf624-111">Geometrik yol kullanarak bir nesne taşımak için başka bir yolu bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cf624-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="cf624-112">Bir örnek için bkz: [bir nesne boyunca bir yolu (Matris Animasyonu) animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="cf624-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf624-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf624-113">See Also</span></span>  
 [<span data-ttu-id="cf624-114">Animasyon genel bakış</span><span class="sxs-lookup"><span data-stu-id="cf624-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="cf624-115">Yol animasyon nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="cf624-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
