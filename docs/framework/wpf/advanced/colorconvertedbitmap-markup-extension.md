---
title: ColorConvertedBitmap Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 4f71b90fa00d1aaee0ec5ad43e5a19be03c79c50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647653"
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="af307-102">ColorConvertedBitmap Biçimlendirme Uzantısı</span><span class="sxs-lookup"><span data-stu-id="af307-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="af307-103">Katıştırılmış bir profili olmayan bir bit eşlem kaynağını belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="af307-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="af307-104">Renk bağlamları / tarafından belirtilen profilleri [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], görüntü kaynağı olarak [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af307-104">Color contexts / profiles are specified by [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], as is the image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="af307-105">XAML Öznitelik Kullanımı</span><span class="sxs-lookup"><span data-stu-id="af307-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="af307-106">XAML Değerleri</span><span class="sxs-lookup"><span data-stu-id="af307-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="af307-107">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Kullanıp bit eşlemin.</span><span class="sxs-lookup"><span data-stu-id="af307-107">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="af307-108">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Kaynak profili yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="af307-108">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="af307-109">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Hedef profili yapılandırma</span><span class="sxs-lookup"><span data-stu-id="af307-109">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af307-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af307-110">Remarks</span></span>  
 <span data-ttu-id="af307-111">Bu işaretleme uzantısı gibi bir dizi görüntü kaynağı özellik değerleri doldurmak için hedeflenen <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="af307-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="af307-112">Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="af307-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="af307-113">`ColorConvertedBitmap` (veya `ColorConvertedBitmapExtension`) özellik öğesi sözdizimine kullanılamaz çünkü değerleri yalnızca değerleri dize ilk oluşturucu üzerinde ayarlanabilir uzantı tanımlayıcısı şu.</span><span class="sxs-lookup"><span data-stu-id="af307-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="af307-114">`ColorConvertedBitmap` bir işaretleme uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="af307-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="af307-115">Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="af307-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="af307-116">İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kuralına göre kendi öznitelik sözdizimi içinde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin bir işaretleme uzantısı özniteliği işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="af307-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="af307-117">Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="af307-117">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af307-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af307-118">See also</span></span>
- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [<span data-ttu-id="af307-119">İşaretleme Uzantıları ve WPF XAML</span><span class="sxs-lookup"><span data-stu-id="af307-119">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="af307-120">Görüntülemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="af307-120">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
