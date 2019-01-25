---
title: 'Nasıl yapılır: 3B Model Ölçeğinin Dönüşümü'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 13f718451cb1b753a41304efde7db55360d3f687
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672903"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a><span data-ttu-id="36ec9-102">Nasıl yapılır: 3B Model Ölçeğinin Dönüşümü</span><span class="sxs-lookup"><span data-stu-id="36ec9-102">How to: Transform the Scale of a 3-D Model</span></span>
<span data-ttu-id="36ec9-103">Bu örnek, 3B nesnenin ölçeklendirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="36ec9-103">This example shows how to scale a 3-D object.</span></span> <span data-ttu-id="36ec9-104">3B nesnenin ölçeklendirmek için kullanmak bir <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="36ec9-104">To scale a 3-D object, use a <xref:System.Windows.Media.Media3D.ScaleTransform3D>.</span></span> <span data-ttu-id="36ec9-105"><xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, Ve <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> özellikleri belirttiğiniz faktörüyle öğe yeniden boyutlandırır.</span><span class="sxs-lookup"><span data-stu-id="36ec9-105">The <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, and <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> properties resize the element by the factor you specify.</span></span> <span data-ttu-id="36ec9-106">Örneğin, bir <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> 1.5 değerini uzatır özgün genişliğinin yüzde 150'si bir nesne.</span><span class="sxs-lookup"><span data-stu-id="36ec9-106">For example, a <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> value of 1.5 stretches an object to 150 percent of its original width.</span></span> <span data-ttu-id="36ec9-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> 0,5 değerini yüzde 50 nesnenin yüksekliğini küçültür.</span><span class="sxs-lookup"><span data-stu-id="36ec9-107">A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> value of 0.5 shrinks the height of an object by 50 percent.</span></span> <span data-ttu-id="36ec9-108">Aşağıdaki kodu kullanarak gösteren bir <xref:System.Windows.Media.Media3D.ScaleTransform3D> olarak dönüştürme için bir <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="36ec9-108">The code below shows using a <xref:System.Windows.Media.Media3D.ScaleTransform3D> as the transform for a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="36ec9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ec9-109">Example</span></span>  
 <span data-ttu-id="36ec9-110">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="36ec9-110">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="36ec9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ec9-111">See also</span></span>
- [<span data-ttu-id="36ec9-112">3B Çevirilerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="36ec9-112">Animate 3-D Translations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)
- [<span data-ttu-id="36ec9-113">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="36ec9-113">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="36ec9-114">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="36ec9-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
