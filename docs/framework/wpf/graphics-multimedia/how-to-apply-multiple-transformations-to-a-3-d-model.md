---
title: "Nasıl yapılır: 3B Modeline Birden Çok Dönüşüm Uygulama"
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
helpviewer_keywords: 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77e9f664ababa32cf0629f513f81b1e24030eac1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="41872-102">Nasıl yapılır: 3B Modeline Birden Çok Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="41872-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="41872-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.Media3D.RotateTransform3D> ve <xref:System.Windows.Media.Media3D.ScaleTransform3D> döndürmek ve 3B modelin ölçeğini değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="41872-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="41872-104">Aşağıdaki kod bu dönüşümlerin uygulamak gösterilmiştir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> özelliği bir <xref:System.Windows.Media.Media3D.GeometryModel3D> XAML'de.</span><span class="sxs-lookup"><span data-stu-id="41872-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="41872-105">Kod:</span><span class="sxs-lookup"><span data-stu-id="41872-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="41872-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="41872-106">Example</span></span>  
 <span data-ttu-id="41872-107">Aşağıdaki kod tüm örnek XAML'de gösterir.</span><span class="sxs-lookup"><span data-stu-id="41872-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="41872-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="41872-108">Example</span></span>  
 <span data-ttu-id="41872-109">Tüm örnek kodda aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="41872-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="41872-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41872-110">See Also</span></span>  
 [<span data-ttu-id="41872-111">Bir 3B modelin ölçeğini dönüştürme</span><span class="sxs-lookup"><span data-stu-id="41872-111">Transform the Scale of a 3-D Model</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-transform-the-scale-of-a-3-d-model.md)
