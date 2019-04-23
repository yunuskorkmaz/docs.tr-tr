---
title: 'Nasıl yapılır: 3B Çevirilerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 3e27c2d5f0cd44235a1d897b1b8f057808ae6bd8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168278"
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="9d414-102">Nasıl yapılır: 3B Çevirilerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="9d414-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="9d414-103">Bu konuda ayarlanan bir çeviri dönüşümü animasyon yapmayı gösteren bir [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modeli.</span><span class="sxs-lookup"><span data-stu-id="9d414-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="9d414-104">Aşağıdaki kod, uygulamayı gösterir. bir <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesnesini <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="9d414-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="9d414-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Bu özelliği <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesne animasyon aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="9d414-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="9d414-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d414-106">Example</span></span>  
 <span data-ttu-id="9d414-107">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d414-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9d414-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d414-108">See also</span></span>

- [<span data-ttu-id="9d414-109">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="9d414-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="9d414-110">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d414-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="9d414-111">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d414-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="9d414-112">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d414-112">Transforms Overview</span></span>](transforms-overview.md)
