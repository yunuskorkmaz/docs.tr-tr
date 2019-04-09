---
title: 'Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 1d3f6a0622b5e0ccccf14af99782bb78dfe87ccb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168057"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="ffc58-102">Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama</span><span class="sxs-lookup"><span data-stu-id="ffc58-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="ffc58-103">Aşağıdaki örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.Media3D.Material> ön ve arkasına bir 3B nesne ve her iki tarafında bir nesneyi göstermek için nesneye animasyon uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ffc58-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="ffc58-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D> kırmızı uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesne ön tarafındaki ve <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D> mavi uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesnenin tarafı için.</span><span class="sxs-lookup"><span data-stu-id="ffc58-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="ffc58-105">Aşağıdaki kod, nesneyi malzemeleri uygulamaya gösterir:</span><span class="sxs-lookup"><span data-stu-id="ffc58-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="ffc58-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffc58-106">Example</span></span>  
 <span data-ttu-id="ffc58-107">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffc58-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ffc58-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffc58-108">See also</span></span>

- [<span data-ttu-id="ffc58-109">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ffc58-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="ffc58-110">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ffc58-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="ffc58-111">3B Görünümde Malzeme Özelliklerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="ffc58-111">Animate Material Properties in a 3-D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="ffc58-112">3B Nesnesine Yayımlatıcı Malzeme Uygulama</span><span class="sxs-lookup"><span data-stu-id="ffc58-112">Apply Emissive Material to a 3-D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
