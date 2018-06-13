---
title: 'Nasıl yapılır: Görüntü Kırpma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: 46c559356447688e52508b823cc260c13128208f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553812"
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="1d74e-102">Nasıl yapılır: Görüntü Kırpma</span><span class="sxs-lookup"><span data-stu-id="1d74e-102">How to: Crop an Image</span></span>
<span data-ttu-id="1d74e-103">Bu örnek kullanarak bir görüntü kırpma gösterilmektedir <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span><span class="sxs-lookup"><span data-stu-id="1d74e-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="1d74e-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> öncelikle bir resim kırpılmış bir sürümünü kodlarken çıkışı bir dosyaya kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d74e-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="1d74e-105">Görüntü görüntüleme amacıyla bakın kırpma için [kırpma bölgesi oluşturma](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) konu.</span><span class="sxs-lookup"><span data-stu-id="1d74e-105">To crop an image for display purposes see the [Create a Clip Region](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d74e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d74e-106">Example</span></span>  
 <span data-ttu-id="1d74e-107">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örneklerin içinde kullanılan kaynakları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d74e-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="1d74e-108">Aşağıdaki örnek, bir görüntü kullanarak oluşturur bir <xref:System.Windows.Media.Imaging.CroppedBitmap> kaynağı olarak.</span><span class="sxs-lookup"><span data-stu-id="1d74e-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="1d74e-109"><xref:System.Windows.Media.Imaging.CroppedBitmap> De başka bir kaynak olarak kullanılabilir <xref:System.Windows.Media.Imaging.CroppedBitmap>, kırpmayı zincirleme.</span><span class="sxs-lookup"><span data-stu-id="1d74e-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="1d74e-110">Unutmayın <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> bit eşlem ve ilk resim kırpılmış kaynağı göreli değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1d74e-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="1d74e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d74e-111">See Also</span></span>  
 [<span data-ttu-id="1d74e-112">Kırpma bölgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d74e-112">Create a Clip Region</span></span>](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)
