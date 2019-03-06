---
title: 'Nasıl yapılır: 3B Modeline Birden Çok Dönüşüm Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
ms.openlocfilehash: d18b9bc78e011796f9d9e6d535f3dc949bd5a0f8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352470"
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="b15e1-102">Nasıl yapılır: 3B Modeline Birden Çok Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="b15e1-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="b15e1-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Media3D.RotateTransform3D> ve <xref:System.Windows.Media.Media3D.ScaleTransform3D> döndürmek ve 3B model ölçeğinin değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b15e1-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="b15e1-104">Aşağıdaki kod bu dönüşüm için uygulama gösterilmiştir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D> XAML içinde.</span><span class="sxs-lookup"><span data-stu-id="b15e1-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="b15e1-105">Kod:</span><span class="sxs-lookup"><span data-stu-id="b15e1-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="b15e1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b15e1-106">Example</span></span>  
 <span data-ttu-id="b15e1-107">Aşağıdaki kod, tüm örnek XAML içinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="b15e1-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="b15e1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b15e1-108">Example</span></span>  
 <span data-ttu-id="b15e1-109">Tüm örnek kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b15e1-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b15e1-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b15e1-110">See also</span></span>
- [<span data-ttu-id="b15e1-111">3B Model Ölçeğinin Dönüşümü</span><span class="sxs-lookup"><span data-stu-id="b15e1-111">Transform the Scale of a 3-D Model</span></span>](how-to-transform-the-scale-of-a-3-d-model.md)
