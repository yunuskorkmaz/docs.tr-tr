---
title: 'Nasıl yapılır: 3B Nesnesine Yayımlatıcı Malzeme Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- EmissiveMaterial [WPF], applying to 3-D objects
- 3-D objects [WPF], applying EmissiveMaterial
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
ms.openlocfilehash: 90a4903310ff7a8778296866f39f685aefee3ffb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645047"
---
# <a name="how-to-apply-emissive-material-to-a-3-d-object"></a><span data-ttu-id="df983-102">Nasıl yapılır: 3B Nesnesine Yayımlatıcı Malzeme Uygulama</span><span class="sxs-lookup"><span data-stu-id="df983-102">How to: Apply Emissive Material to a 3-D Object</span></span>
<span data-ttu-id="df983-103">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Media3D.EmissiveMaterial> EmissiveMaterial'ın fırça rengini eşit var olan bir malzeme rengi eklemek için.</span><span class="sxs-lookup"><span data-stu-id="df983-103">The following example shows how to use <xref:System.Windows.Media.Media3D.EmissiveMaterial> to add color to an existing Material equal to the color of the EmissiveMaterial's brush.</span></span> <span data-ttu-id="df983-104">Aşağıdaki kod gösterir <xref:System.Windows.Media.Media3D.DiffuseMaterial> ve <xref:System.Windows.Media.Media3D.EmissiveMaterial> mavi DiffuseMaterial'ın eklemek için birlikte uygulanır.</span><span class="sxs-lookup"><span data-stu-id="df983-104">The code below shows <xref:System.Windows.Media.Media3D.DiffuseMaterial> and <xref:System.Windows.Media.Media3D.EmissiveMaterial> applied in combination to add blue to the DiffuseMaterial's appearance.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 <span data-ttu-id="df983-105">Yordam kodunda:</span><span class="sxs-lookup"><span data-stu-id="df983-105">In procedural code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="df983-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="df983-106">Example</span></span>  
 <span data-ttu-id="df983-107">Aşağıdaki kod, tüm örnek XAML içinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="df983-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="df983-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="df983-108">Example</span></span>  
 <span data-ttu-id="df983-109">Yordam kodunda tüm örnek aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="df983-109">Below is the entire sample in procedural code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="df983-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df983-110">See also</span></span>
- [<span data-ttu-id="df983-111">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="df983-111">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="df983-112">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="df983-112">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="df983-113">3B Görünümde Malzeme Özelliklerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="df983-113">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="df983-114">3B Nesnenin Ön ve Arkasına Malzeme Uygulama</span><span class="sxs-lookup"><span data-stu-id="df983-114">Apply Material to the Front and Back of a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)
