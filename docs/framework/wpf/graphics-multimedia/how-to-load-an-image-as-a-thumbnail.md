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
ms.openlocfilehash: d92a489f19f8c7160bed5ec83535bdc33cfe561b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735996"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="c8b09-102">Nasıl yapılır: Bir Görüntüyü Küçük Resim Olarak Yükleme</span><span class="sxs-lookup"><span data-stu-id="c8b09-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="c8b09-103">Aşağıdaki örnekler nasıl yükleneceğini gösterir. bir <xref:System.Windows.Controls.Image> uygulama bellekten kazanacak şekilde bir küçük resim olarak.</span><span class="sxs-lookup"><span data-stu-id="c8b09-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8b09-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8b09-104">Example</span></span>  
 <span data-ttu-id="c8b09-105">Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> içinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] görüntüyü yüklemek için gerekli bellek miktarını azaltmak için.</span><span class="sxs-lookup"><span data-stu-id="c8b09-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="c8b09-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8b09-106">Example</span></span>  
 <span data-ttu-id="c8b09-107">Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> özelliği bir <xref:System.Windows.Media.Imaging.BitmapImage> görüntüyü yüklemek için gerekli bellek miktarını azaltmaya yönelik kod içinde.</span><span class="sxs-lookup"><span data-stu-id="c8b09-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="c8b09-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8b09-108">See also</span></span>
- [<span data-ttu-id="c8b09-109">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c8b09-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
