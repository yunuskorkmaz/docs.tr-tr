---
title: 'Nasıl yapılır: Bir Görüntüyü Küçük Resim Olarak Yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 349a602a10b89931701e24334bf5ac5536f26400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562329"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="a99e8-102">Nasıl yapılır: Bir Görüntüyü Küçük Resim Olarak Yükleme</span><span class="sxs-lookup"><span data-stu-id="a99e8-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="a99e8-103">Aşağıdaki örnekler nasıl yükleneceğini bir <xref:System.Windows.Controls.Image> uygulama belleğini korumak için bir küçük resim olarak.</span><span class="sxs-lookup"><span data-stu-id="a99e8-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a99e8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a99e8-104">Example</span></span>  
 <span data-ttu-id="a99e8-105">Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] resmi yüklemek için gerekli bellek miktarını azaltmak için.</span><span class="sxs-lookup"><span data-stu-id="a99e8-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="a99e8-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a99e8-106">Example</span></span>  
 <span data-ttu-id="a99e8-107">Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> resmi yüklemek için gerekli bellek miktarını azaltmak için kod.</span><span class="sxs-lookup"><span data-stu-id="a99e8-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="a99e8-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a99e8-108">See Also</span></span>  
 [<span data-ttu-id="a99e8-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a99e8-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
