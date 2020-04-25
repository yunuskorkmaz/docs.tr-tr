---
title: ColorConvertedBitmap Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: a5b491723a036c1b1fd0bb61736e6f2ee53fbcd3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141222"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="b034f-102">ColorConvertedBitmap Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="b034f-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="b034f-103">Gömülü profili olmayan bir bit eşlem kaynağı belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b034f-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="b034f-104">Renk bağlamları/profilleri, görüntü kaynağı URI 'SI olduğu gibi URI tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b034f-104">Color contexts / profiles are specified by URI, as is the image source URI.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b034f-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b034f-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" ... />
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b034f-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="b034f-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="b034f-107">Profili oluşturulmuş olmayan bit eşlemin URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="b034f-107">The URI of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="b034f-108">Kaynak profili yapılandırmasının URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="b034f-108">The URI of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="b034f-109">Hedef profil yapılandırmasının URI 'SI</span><span class="sxs-lookup"><span data-stu-id="b034f-109">The URI of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b034f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b034f-110">Remarks</span></span>  
 <span data-ttu-id="b034f-111">Bu biçimlendirme uzantısı, gibi ilgili görüntü kaynağı özellik değerlerinin bir kümesini doldurmaya yöneliktir <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="b034f-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="b034f-112">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="b034f-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="b034f-113">`ColorConvertedBitmap`(veya `ColorConvertedBitmapExtension`) özellik öğesi sözdiziminde kullanılamaz, çünkü değerler yalnızca ilk oluşturucuda, uzantı tanımlayıcısından sonraki dize olan değer olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b034f-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="b034f-114">`ColorConvertedBitmap`bir biçimlendirme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="b034f-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="b034f-115">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b034f-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="b034f-116">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="b034f-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="b034f-117">Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="b034f-117">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b034f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b034f-118">See also</span></span>

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="b034f-119">Biçimlendirme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="b034f-119">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="b034f-120">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b034f-120">Imaging Overview</span></span>](../graphics-multimedia/imaging-overview.md)
