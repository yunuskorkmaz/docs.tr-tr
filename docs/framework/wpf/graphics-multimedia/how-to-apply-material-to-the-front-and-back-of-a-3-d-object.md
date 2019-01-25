---
title: 'Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 16f30e3a880d7dcc943a9583ba0f04c4bd682827
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652039"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="64904-102">Nasıl yapılır: 3B Nesnenin Ön ve Arkasına Malzeme Uygulama</span><span class="sxs-lookup"><span data-stu-id="64904-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="64904-103">Aşağıdaki örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.Media3D.Material> ön ve arkasına bir 3B nesne ve her iki tarafında bir nesneyi göstermek için nesneye animasyon uygulayın.</span><span class="sxs-lookup"><span data-stu-id="64904-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="64904-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D> kırmızı uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesne ön tarafındaki ve <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> özelliği <xref:System.Windows.Media.Media3D.GeometryModel3D> mavi uygulamak için kullanılan <xref:System.Windows.Media.Brush> nesnenin tarafı için.</span><span class="sxs-lookup"><span data-stu-id="64904-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="64904-105">Aşağıdaki kod, nesneyi malzemeleri uygulamaya gösterir:</span><span class="sxs-lookup"><span data-stu-id="64904-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="64904-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="64904-106">Example</span></span>  
 <span data-ttu-id="64904-107">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="64904-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="64904-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64904-108">See also</span></span>
- [<span data-ttu-id="64904-109">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="64904-109">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="64904-110">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="64904-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="64904-111">3B Görünümde Malzeme Özelliklerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="64904-111">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="64904-112">3B Nesnesine Yayımlatıcı Malzeme Uygulama</span><span class="sxs-lookup"><span data-stu-id="64904-112">Apply Emissive Material to a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
