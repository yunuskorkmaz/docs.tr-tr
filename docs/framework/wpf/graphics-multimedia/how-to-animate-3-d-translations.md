---
title: 'Nasıl yapılır: 3B Çevirilerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: e73035a48e32e3eec20b44c82b5b9ec6763c1e7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653040"
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="a6022-102">Nasıl yapılır: 3B Çevirilerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="a6022-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="a6022-103">Bu konuda ayarlanan bir çeviri dönüşümü animasyon yapmayı gösteren bir [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modeli.</span><span class="sxs-lookup"><span data-stu-id="a6022-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="a6022-104">Aşağıdaki kod, uygulamayı gösterir. bir <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesnesini <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="a6022-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="a6022-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Bu özelliği <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesne animasyon aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a6022-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="a6022-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6022-106">Example</span></span>  
 <span data-ttu-id="a6022-107">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6022-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a6022-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6022-108">See also</span></span>
- [<span data-ttu-id="a6022-109">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="a6022-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="a6022-110">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6022-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="a6022-111">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6022-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="a6022-112">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a6022-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
