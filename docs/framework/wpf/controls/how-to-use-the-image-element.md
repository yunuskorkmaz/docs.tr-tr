---
title: "Nasıl yapılır: Görüntü Öğesi Kullanma"
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
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26beb6b0f5c446bbddd293e76ae79d062aa0fe48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="6c298-102">Nasıl yapılır: Görüntü Öğesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="6c298-102">How to: Use the Image Element</span></span>
<span data-ttu-id="6c298-103">Bu örnek görüntüleri kullanarak, bir uygulamada dahil etmek nasıl gösterir <xref:System.Windows.Controls.Image> öğesi.</span><span class="sxs-lookup"><span data-stu-id="6c298-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c298-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c298-104">Example</span></span>  
 <span data-ttu-id="6c298-105">Aşağıdaki örnek, bir resmin 200 piksel genişliğinde nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c298-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="6c298-106">Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, öznitelik sözdizimi ve özellik etiketi sözdizimi görüntü tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c298-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="6c298-107">Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz: [bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6c298-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="6c298-108">A <xref:System.Windows.Media.Imaging.BitmapImage> görüntünün kaynak verileri tanımlamak için kullanılır ve özellik etiketi sözdizimi örneği için açıkça tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6c298-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="6c298-109">Ayrıca, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> , <xref:System.Windows.Media.Imaging.BitmapImage> aynı genişliğe ayarlanır <xref:System.Windows.FrameworkElement.Width%2A> , <xref:System.Windows.Controls.Image>.</span><span class="sxs-lookup"><span data-stu-id="6c298-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="6c298-110">Bu görüntü işleme, en düşük bellek miktarını kullanılmasını sağlamak amacıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6c298-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c298-111">İşlenmiş resmin boyutunu belirtmek istiyorsanız, genel olarak, yalnızca belirtin <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A> ikisini birden belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="6c298-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="6c298-112">Yalnızca birini belirtirseniz, resmin en boy oranı korunur.</span><span class="sxs-lookup"><span data-stu-id="6c298-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="6c298-113">Aksi takdirde, resim, beklenmedik bir şekilde uzamış ya da çarpık görünebilir.</span><span class="sxs-lookup"><span data-stu-id="6c298-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="6c298-114">Görüntü denetlemek için davranış uzatma, kullanın <xref:System.Windows.Controls.Image.Stretch%2A> ve <xref:System.Windows.Controls.Image.StretchDirection%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="6c298-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c298-115">Belirttiğinizde görüntüsünün boyutu ile ya da <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.FrameworkElement.Height%2A>, ya da ayarlamalısınız <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> veya <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> aynı boyuta için.</span><span class="sxs-lookup"><span data-stu-id="6c298-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="6c298-116"><xref:System.Windows.Controls.Image.Stretch%2A> Özelliği, görüntü kaynağı bir görüntü öğesi doldurmak için nasıl genişletilir belirler.</span><span class="sxs-lookup"><span data-stu-id="6c298-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="6c298-117">Daha fazla bilgi için bkz: <xref:System.Windows.Media.Stretch> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="6c298-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="6c298-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c298-118">Example</span></span>  
 <span data-ttu-id="6c298-119">Aşağıdaki örnek bir resmin 200 piksel genişliğinde kod kullanarak nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c298-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c298-120">Ayarı <xref:System.Windows.Media.Imaging.BitmapImage> özellikleri Bitti, içinde bir <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloğu.</span><span class="sxs-lookup"><span data-stu-id="6c298-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="6c298-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c298-121">See Also</span></span>  
 [<span data-ttu-id="6c298-122">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6c298-122">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
