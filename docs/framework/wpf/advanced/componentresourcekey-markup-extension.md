---
title: ComponentResourceKey Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: d11c26add084165eaa9fd0b319a375c4b98c7fb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey Biçimlendirme Uzantısı
Tanımlar ve dış derlemelerden yüklenen kaynaklar tuşları başvurur. Bu, bir derlemeyi ya da bir sınıf bir açık kaynak sözlüğü yerine bir derlemeyi hedef türünü belirtmek bir kaynak arama sağlar.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML öznitelik kullanımı (anahtar ayarlama, kısaltılmış)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML öznitelik (anahtar ayarlama, ayrıntılı) kullanımı  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML öznitelik kullanımı (kaynak isteme, kısaltılmış)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML öznitelik kullanımı (kaynak isteme, ayrıntılı)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`targetTypeName`|Ortak ad [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] kaynak derlemede tanımlanan türü.|  
|`targetID`|Kaynak anahtarı. Kaynaklar, arandığı zaman `targetID` benzer olacaktır [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) kaynağının.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıdaki kullanımları görülen bir {`ComponentResourceKey`} biçimlendirme uzantısı kullanımı iki yerde bulundu:  
  
-   Bir anahtar içerisinde bir denetim yazar tarafından sağlanan bir tema kaynak sözlüğü tanımı.  
  
-   Bir tema kaynak derlemeden erişme, ne zaman yeniden şablon oluşturma denetimi olan ancak denetimin temalar tarafından sağlanan kaynaklardan gelen özellik değerleri kullanmak istiyorsunuz.  
  
 Temalardan gelmesi bileşen kaynakları başvurmak için genellikle kullanmanız önerilir `{DynamicResource}` yerine `{StaticResource}`. Bu kullanımları gösterilir. `{DynamicResource}` kullanıcı tarafından tema değiştirilebildiğinden önerilir. Bir tema desteklemek için denetim yazarının hedefi en yakından eşleşen bileşen kaynak isterseniz, bileşeni kaynak başvuru dinamik de etkinleştirmeniz gerekir.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Kaynak gerçekte tanımlandığı hedef derlemesinde varolan bir türü tanımlar. A `ComponentResourceKey` tanımlanan ve tam olarak bilmeden bağımsız olarak kullanılan nerede <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tanımlandı ancak başvurulan derlemeler üzerinden türü çözümlemelidir.  
  
 Bir ortak kullanım <xref:System.Windows.ComponentResourceKey> bir sınıf bir üyesi olarak ardından sunulan anahtarları tanımlamaktır. Bu kullanım için kullandığınız <xref:System.Windows.ComponentResourceKey> sınıfı oluşturucusu, biçimlendirme uzantısını değil. Daha fazla bilgi için bkz: <xref:System.Windows.ComponentResourceKey>, veya "Tanımlama ve başvuran anahtarları için tema kaynaklar" bölümüne [denetimine genel bakış yazma](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Hem anahtarları oluşturma ve başvuru kaynakları anahtarlı için öznitelik sözdizimi için yaygın olarak kullanılır `ComponentResourceKey` biçimlendirme uzantısı.  
  
 Kısaltılmış sözdizimi dayanan <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Oluşturucusu imza ve biçimlendirme uzantısı konumsal parametre kullanımı. Hangi sırayla `targetTypeName` ve `targetID` verilir önemlidir. Ayrıntılı sözdizimi dayanan <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> varsayılan oluşturucu ve kümelerini <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> nesne öğesindeki doğru öznitelik sözdizimine benzer şekilde. Ayrıntılı sözdizimi, hangi özellikler ayarlanır sırası önemli değildir. İlişkileri ve bu iki alternatifleri (kısaltılmış ve ayrıntılı) mekanizmaları açıklanan konusunda daha fazla ayrıntı [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Teknik olarak, değeri `targetID` bir dize olması gerekmez, herhangi bir nesne olabilir. Ancak, en yaygın WPF'de hizalamak için kullanımdır `targetID` dizeleri olan ve olduğu gibi dizeleri geçerli forms değerle [XamlName Dilbilgisi](../../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` nesne öğesi sözdiziminde kullanılabilir. Bu durumda, her ikisi de değerini belirten <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> özellikleri uzantıyı düzgün başlatmak için gereklidir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu uygulaması işleme için bu biçimlendirme uzantısı tarafından tanımlanan <xref:System.Windows.ComponentResourceKey> sınıfı.  
  
 `ComponentResourceKey` bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kurala göre kendi öznitelik sözdiziminde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci tanıdığı biçimlendirme uzantısı öznitelik işlemelidir. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Denetim Yazımına Genel Bakış](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [İşaretleme Uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
