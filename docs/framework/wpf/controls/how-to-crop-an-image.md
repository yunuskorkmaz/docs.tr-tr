---
title: "Nasıl yapılır: Görüntü Kırpma"
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
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6de7914a1226381da763b3348d1794453fe93b02
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="e8978-102">Nasıl yapılır: Görüntü Kırpma</span><span class="sxs-lookup"><span data-stu-id="e8978-102">How to: Crop an Image</span></span>
<span data-ttu-id="e8978-103">Bu örnek kullanarak bir görüntü kırpma gösterilmektedir <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span><span class="sxs-lookup"><span data-stu-id="e8978-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="e8978-104"><xref:System.Windows.Media.Imaging.CroppedBitmap>öncelikle bir resim kırpılmış bir sürümünü kodlarken çıkışı bir dosyaya kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8978-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="e8978-105">Görüntü görüntüleme amacıyla bakın kırpma için [kırpma bölgesi oluşturma](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376) konu.</span><span class="sxs-lookup"><span data-stu-id="e8978-105">To crop an image for display purposes see the [Create a Clip Region](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8978-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8978-106">Example</span></span>  
 <span data-ttu-id="e8978-107">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örneklerin içinde kullanılan kaynakları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e8978-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="e8978-108">Aşağıdaki örnek, bir görüntü kullanarak oluşturur bir <xref:System.Windows.Media.Imaging.CroppedBitmap> kaynağı olarak.</span><span class="sxs-lookup"><span data-stu-id="e8978-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="e8978-109"><xref:System.Windows.Media.Imaging.CroppedBitmap> De başka bir kaynak olarak kullanılabilir <xref:System.Windows.Media.Imaging.CroppedBitmap>, kırpmayı zincirleme.</span><span class="sxs-lookup"><span data-stu-id="e8978-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="e8978-110">Unutmayın <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> bit eşlem ve ilk resim kırpılmış kaynağı göreli değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e8978-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="e8978-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8978-111">See Also</span></span>  
 [<span data-ttu-id="e8978-112">Kırpma bölgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8978-112">Create a Clip Region</span></span>](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376)
