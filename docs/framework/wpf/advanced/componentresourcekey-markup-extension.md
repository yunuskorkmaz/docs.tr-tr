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
ms.openlocfilehash: 5f72d6c3273cfda4276383cfe72f90196e5d4340
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169760"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey Biçimlendirme Uzantısı
Tanımlar ve dış derlemelerden yüklü olan kaynaklar için anahtarları başvurur. Bu, bir açık kaynak sözlüğü bir derlemede veya bir sınıf yerine bir derleme bir hedef türü belirtmek bir kaynak araması sağlar.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML öznitelik kullanımı (anahtar ayarlama, compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML öznitelik kullanımı (anahtar ayarlama, ayrıntılı)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML öznitelik kullanımı (kaynak isteme, compact)  
  
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
|`targetTypeName`|Ortak adını [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] kaynak derlemesinde tanımlanan tür.|  
|`targetID`|Kaynak anahtarı. Kaynakları, arandığı zaman `targetID` benzer olacaktır [x: Key yönergesi](../../xaml-services/x-key-directive.md) kaynak.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıdaki kullanımları görüldüğü gibi bir {`ComponentResourceKey`} biçimlendirme uzantısı kullanımı, iki yerde bulunur:  
  
-   Denetim yazarı tarafından sağlanan bir tema kaynak sözlüğünün içinde bir anahtar tanımı.  
  
-   Derlemeden bir tema kaynak erişimi ne zaman yeniden şablon oluşturma denetimi olan ancak denetimin temalar tarafından sağlanan kaynaklardan gelen özellik değerlerini kullanmak istiyorsunuz.  
  
 Temalarından gelen bileşen kaynakları başvurmak için genellikle kullanmanız önerilir `{DynamicResource}` yerine `{StaticResource}`. Bu kullanımları içinde gösterilir. `{DynamicResource}` kullanıcı tarafından tema değiştirilebilmesi için nedeniyle önerilir. Bir tema desteklemek için denetim yazarının hedefi en yakından eşleşen bileşen kaynak isterseniz, bileşeni kaynak başvurusu'de dinamik olarak etkinleştirmeniz gerekir.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Burada kaynak gerçekten tanımlanmış hedef derlemede mevcut bir türü tanımlar. A `ComponentResourceKey` tanımlanabilir ve tam olarak bilerek bağımsız olarak kullanılan burada <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tanımlandı, ancak başvurulan derlemeler üzerinden türü çözümlemelidir.  
  
 Bir ortak kullanım <xref:System.Windows.ComponentResourceKey> sonra sunulan anahtarları bir sınıfın üyeleri olarak tanımlamaktır. Bu kullanım için kullandığınız <xref:System.Windows.ComponentResourceKey> sınıf oluşturucusu, işaretleme uzantısı değil. Daha fazla bilgi için <xref:System.Windows.ComponentResourceKey>, veya "tanımlama ve başvurma anahtarları için tema kaynaklar" bölümünü konunun [denetim yazmaya genel bakış](../controls/control-authoring-overview.md).  
  
 Hem anahtarları oluşturma ve başvuru kaynakları Anahtarlanan için öznitelik sözdizimi için yaygın olarak kullanılır `ComponentResourceKey` işaretleme uzantısı.  
  
 Kısaltılmış sözdizimi kullanır <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Oluşturucu imzası ve bir işaretleme uzantısı konumsal parametresi kullanımı. Bir sırayı `targetTypeName` ve `targetID` verilen önemlidir. Ayrıntılı sözdizimi kullanır <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> varsayılan oluşturucu ve kümelerini <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> bir nesne öğesi üzerinde doğru öznitelik sözdizimine benzer bir şekilde. Ayrıntılı söz dizimi içinde özelliklerini ayarlamak sırası önemli değildir. İlişkileri ve bu iki alternatifleri (kısa ve ayrıntılı) mekanizmaları konusunda daha ayrıntılı açıklanmıştır [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Teknik olarak, değeri `targetID` bir dize olması gerekmez, herhangi bir nesne olabilir. Ancak, en yaygın WPF hizalamak için kullanımdır `targetID` dizeleri olan ve burada gibi dizeleri geçerli forms değeriyle [XamlName Dilbilgisi](../../xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` nesne öğesi sözdiziminde kullanılabilir. Bu durumda, her ikisi de değerini belirterek <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> özellikler uzantısı düzgün başlatmak için gereklidir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu uygulaması, bu işaretleme uzantısının işlenmesi tarafından tanımlanır <xref:System.Windows.ComponentResourceKey> sınıfı.  
  
 `ComponentResourceKey` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki tüm biçimlendirme uzantıları [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmak {ve} kuralına göre kendi öznitelik sözdizimi içinde karakterler bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin bir işaretleme uzantısı özniteliği işlemesi gerekir. Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
