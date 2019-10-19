---
title: ColorConvertedBitmap Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 7d14ddc6276b9dd7baee12e267e8af1250bc11ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582778"
---
# <a name="colorconvertedbitmap-markup-extension"></a>ColorConvertedBitmap Biçimlendirme Uzantısı
Gömülü profili olmayan bir bit eşlem kaynağı belirtmek için bir yol sağlar. Renk bağlamları/profilleri, görüntü kaynağı URI 'SI olduğu gibi URI tarafından belirtilir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`imageSource`|Profili oluşturulmuş olmayan bit eşlemin URI 'SI.|  
|`sourceIIC`|Kaynak profili yapılandırmasının URI 'SI.|  
|`destinationIIC`|Hedef profil yapılandırmasının URI 'SI|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu biçimlendirme uzantısı, <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A> gibi ilgili bir görüntü kaynağı özelliği değerlerini doldurmaya yöneliktir.  
  
 Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. `ColorConvertedBitmap` (veya `ColorConvertedBitmapExtension`) özellik öğesi sözdiziminde kullanılamaz, çünkü değerler yalnızca ilk oluşturucuda, uzantı tanımlayıcısından sonraki dize olan değer olarak ayarlanabilir.  
  
 `ColorConvertedBitmap`, biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. @No__t_0 tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakterlerini kullanır. Bu, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin, bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Görüntülemeye Genel Bakış](../graphics-multimedia/imaging-overview.md)
