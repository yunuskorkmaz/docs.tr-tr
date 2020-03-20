---
title: 'Nasıl yapılır: Düz Renk ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849528"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="1268c-102">Nasıl yapılır: Düz Renk ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="1268c-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="1268c-103">Bir <xref:System.Windows.Media.Brushes.Red%2A> alanı düz renkle boyamak için, <xref:System.Windows.Media.Brushes.Blue%2A>önceden tanımlanmış bir sistem fırçası kullanabilir <xref:System.Windows.Media.SolidColorBrush> veya yeni <xref:System.Windows.Media.SolidColorBrush.Color%2A> bir yeni oluşturabilir ve alfa, kırmızı, yeşil ve mavi değerleri kullanarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1268c-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="1268c-104">XAML'de, heksidecimal gösterim kullanarak düz renkli bir alanı da boyayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1268c-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="1268c-105">Aşağıdaki örnekler, mavi boyamak <xref:System.Windows.Shapes.Rectangle> için bu tekniklerin her birini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1268c-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1268c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1268c-106">Example</span></span>  
 <span data-ttu-id="1268c-107">**Önceden Tanımlanmış Fırça Kullanma**</span><span class="sxs-lookup"><span data-stu-id="1268c-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="1268c-108">Aşağıdaki örnekte, dikdörtgen mavisini boyamak için önceden tanımlanmış fırça <xref:System.Windows.Media.Brushes.Blue%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="1268c-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="1268c-109">**Hexadecimal Gösterim kullanma**</span><span class="sxs-lookup"><span data-stu-id="1268c-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="1268c-110">Sonraki örnek, dikdörtgen mavisini boyamak için 8 basamaklı heksadedesmal gösterim kullanır.</span><span class="sxs-lookup"><span data-stu-id="1268c-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="1268c-111">**ARGB Değerlerini Kullanma**</span><span class="sxs-lookup"><span data-stu-id="1268c-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="1268c-112">Sonraki örnek bir <xref:System.Windows.Media.SolidColorBrush> oluşturur ve <xref:System.Windows.Media.SolidColorBrush.Color%2A> mavi renk için ARGB değerlerini kullanarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="1268c-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="1268c-113">Rengi açıklamanın diğer yolları için <xref:System.Windows.Media.Color> yapıya bakın.</span><span class="sxs-lookup"><span data-stu-id="1268c-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="1268c-114">**İlgili Konular**</span><span class="sxs-lookup"><span data-stu-id="1268c-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="1268c-115">Hakkında <xref:System.Windows.Media.SolidColorBrush> daha fazla bilgi ve ek örnekler [için, Düz Renkler ve Degradelere Genel Bakış ile Resim](painting-with-solid-colors-and-gradients-overview.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="1268c-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="1268c-116">Bu kod örneği, <xref:System.Windows.Media.SolidColorBrush> sınıf için sağlanan daha büyük bir örneğin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="1268c-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="1268c-117">Numunenin tamamı için [Fırçalar Örneğine](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)bakın.</span><span class="sxs-lookup"><span data-stu-id="1268c-117">For the complete sample, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1268c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1268c-118">See also</span></span>

- <xref:System.Windows.Media.Brushes>
