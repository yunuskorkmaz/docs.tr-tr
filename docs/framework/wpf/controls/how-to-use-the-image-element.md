---
title: 'Nasıl yapılır: Görüntü Öğesi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 164eee7c10d9e388c6e6ee695af479ca2d6974b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958321"
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="f7b3e-102">Nasıl yapılır: Görüntü Öğesi Kullanma</span><span class="sxs-lookup"><span data-stu-id="f7b3e-102">How to: Use the Image Element</span></span>
<span data-ttu-id="f7b3e-103">Bu örnek, <xref:System.Windows.Controls.Image> öğesini kullanarak bir uygulamaya görüntülerin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7b3e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7b3e-104">Example</span></span>  
 <span data-ttu-id="f7b3e-105">Aşağıdaki örnek bir görüntünün 200 piksel genişliğinde nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="f7b3e-106">Bu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekte, görüntüyü tanımlamak için hem öznitelik sözdizimi hem de özellik etiketi sözdizimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="f7b3e-107">Öznitelik sözdizimi ve özellik sözdizimi hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f7b3e-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="f7b3e-108"><xref:System.Windows.Media.Imaging.BitmapImage> , Görüntünün kaynak verilerini tanımlamak için kullanılır ve özellik etiketi sözdizimi örneği için açıkça tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="f7b3e-109">Ayrıca, <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.FrameworkElement.Width%2A> öğesinin ' ı ile aynı <xref:System.Windows.Controls.Image>genişliğe ayarlanır. <xref:System.Windows.Media.Imaging.BitmapImage></span><span class="sxs-lookup"><span data-stu-id="f7b3e-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="f7b3e-110">Bu, görüntüyü işlemek için en az bellek miktarının kullanıldığından emin olmak için yapılır.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7b3e-111">Genel olarak, işlenmiş bir görüntünün boyutunu belirtmek istiyorsanız, her ikisini de yalnızca <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> veya ' ı belirtin.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="f7b3e-112">Yalnızca bir tane belirtirseniz, görüntünün en boy oranı korunur.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="f7b3e-113">Aksi takdirde, görüntü beklenmedik şekilde uzatılmış veya çarpıtılmış görünebilir.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="f7b3e-114">Görüntünün uzatma davranışını denetlemek için <xref:System.Windows.Controls.Image.Stretch%2A> ve <xref:System.Windows.Controls.Image.StretchDirection%2A> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7b3e-115">Ya <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> da ile bir görüntünün boyutunu belirttiğinizde, ya da aynı boyuta göre de ayarlamanız gerekir. <xref:System.Windows.FrameworkElement.Height%2A></span><span class="sxs-lookup"><span data-stu-id="f7b3e-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="f7b3e-116"><xref:System.Windows.Controls.Image.Stretch%2A> Özelliği, görüntü kaynağının görüntü öğesini doldurmak için nasıl uzatılacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="f7b3e-117">Daha fazla bilgi için bkz <xref:System.Windows.Media.Stretch> . sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="f7b3e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7b3e-118">Example</span></span>  
 <span data-ttu-id="f7b3e-119">Aşağıdaki örnek, kod kullanarak bir görüntünün 200 piksel genelinde nasıl işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7b3e-120">Ayar <xref:System.Windows.Media.Imaging.BitmapImage> özellikleri bir <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> ve <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> bloğu içinde yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="f7b3e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7b3e-121">See also</span></span>

- [<span data-ttu-id="f7b3e-122">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f7b3e-122">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
