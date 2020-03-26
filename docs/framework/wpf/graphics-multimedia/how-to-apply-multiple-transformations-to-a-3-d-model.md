---
title: 'Nasıl yapılır: 3B Modele Birden Çok Dönüşüm Uygula'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
ms.openlocfilehash: 6400d224fb51b93c76c5e9798b4bcc68ff3b9de6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112134"
---
# <a name="how-to-apply-multiple-transformations-to-a-3d-model"></a><span data-ttu-id="7ea1c-102">Nasıl yapılır: 3B Modele Birden Çok Dönüşüm Uygula</span><span class="sxs-lookup"><span data-stu-id="7ea1c-102">How to: Apply Multiple Transformations to a 3D Model</span></span>
<span data-ttu-id="7ea1c-103">Bu örnek, bir <xref:System.Windows.Media.Media3D.RotateTransform3D> 3B <xref:System.Windows.Media.Media3D.ScaleTransform3D> modelin ölçeğini döndürmek ve değiştirmek için a ve a'nın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ea1c-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3D model.</span></span> <span data-ttu-id="7ea1c-104">Aşağıdaki kod, bu dönüşümlerin XAML'deki <xref:System.Windows.Media.Media3D.GeometryModel3D> bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliğine nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7ea1c-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="7ea1c-105">Kod:</span><span class="sxs-lookup"><span data-stu-id="7ea1c-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="7ea1c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ea1c-106">Example</span></span>  
 <span data-ttu-id="7ea1c-107">Aşağıdaki kod XAML'deki tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ea1c-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="7ea1c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ea1c-108">Example</span></span>  
 <span data-ttu-id="7ea1c-109">Aşağıda kod tüm örnektir.</span><span class="sxs-lookup"><span data-stu-id="7ea1c-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7ea1c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ea1c-110">See also</span></span>

- [<span data-ttu-id="7ea1c-111">3B Modelölçeğini Dönüştürün</span><span class="sxs-lookup"><span data-stu-id="7ea1c-111">Transform the Scale of a 3D Model</span></span>](how-to-transform-the-scale-of-a-3-d-model.md)
