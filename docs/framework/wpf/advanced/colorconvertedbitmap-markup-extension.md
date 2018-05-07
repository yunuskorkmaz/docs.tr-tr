---
title: ColorConvertedBitmap Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 9b39e30cbe4e0bedc88c859f013b4d7175f7eb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap Biçimlendirme Uzantısı
Katıştırılmış bir profili olmayan bir bit eşlem kaynağı belirtmek için bir yol sağlar. Renk bağlamları / profilleri tarafından belirtilen [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], görüntü kaynağı olarak [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`imageSource`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Eşlemin bitmap.|  
|`sourceIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Kaynak profil yapılandırmasının.|  
|`destinationIIC`|[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Hedef profil yapılandırmasının|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu biçimlendirme uzantısı görüntü kaynağı özellik değerlerini ilgili bir dizi gibi doldurmak için tasarlanmıştır <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `ColorConvertedBitmap` (veya `ColorConvertedBitmapExtension`) değerleri yalnızca değerleri olarak dize ilk kurucu üzerinde ayarlanabildiğinden özellik öğesi sözdiziminde kullanılamaz uzantı tanımlayıcısını izleyen.  
  
 `ColorConvertedBitmap` bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Görüntülemeye Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
