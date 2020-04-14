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
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243368"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey Biçimlendirme Uzantısı
Dış derlemelerden yüklenen kaynaklar için anahtarları tanımlar ve başvurur. Bu, bir aygıtta veya sınıfta açık bir kaynak sözlüğü yerine, bir derlemede hedef türü belirtmek için kaynak araması sağlar.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML Öznitelik Kullanımı (ayar tuşu, kompakt)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML Öznitelik Kullanımı (ayar tuşu, ayrıntılı)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML Öznitelik Kullanımı (kaynak isteyen, kompakt)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML Öznitelik Kullanımı (kaynak isteyen, ayrıntılı)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`targetTypeName`|Kaynak derlemesinde tanımlanan ortak ortak dil çalışma zamanı (CLR) türünün adı.|  
|`targetID`|Kaynak için anahtar. Kaynaklar arandığında, `targetID` kaynağın [x:Anahtar Yönergesi'ne](../../../desktop-wpf/xaml-services/xkey-directive.md) benzer olacaktır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıdaki kullanımlarda görüldüğü gibi,`ComponentResourceKey`{ } biçimlendirme uzantısı kullanımı iki yerde bulunur:  
  
- Bir denetim yazarı tarafından sağlanan tema kaynağı sözlüğündeki anahtarın tanımı.  
  
- Denetimi yeniden ayarladığınız, ancak denetimin temaları tarafından sağlanan kaynaklardan gelen özellik değerlerini kullanmak istediğinizde, derlemeden bir tema kaynağına erişmek.  
  
 Temalardan gelen bileşen kaynaklarına başvurmak için genellikle `{DynamicResource}` . `{StaticResource}` Bu kullanımlarda gösterilir. `{DynamicResource}`temanın kendisi kullanıcı tarafından değiştirilebildiği için önerilir. Denetim yazarının bir temayı destekleme amacıyla en yakından eşleşen bileşen kaynağını istiyorsanız, bileşen kaynak başvurunuzun da dinamik olmasını sağlamanız gerekir.  
  
 Kaynak <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> gerçekte tanımlandığı hedef derlemede var olan bir türü tanımlar. A `ComponentResourceKey` tanımlanabilir ve tam olarak nerede <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tanımlandığını bilerek bağımsız olarak kullanılabilir, ancak sonunda başvurulan derlemeler aracılığıyla türü çözmek gerekir.  
  
 Bunun için <xref:System.Windows.ComponentResourceKey> yaygın bir kullanım, daha sonra bir sınıfın üyeleri olarak ortaya çıkarılan anahtarları tanımlamaktır. Bu kullanım için biçimlendirme uzantısını <xref:System.Windows.ComponentResourceKey> değil, sınıf oluşturucuyu kullanırsınız. Daha fazla bilgi <xref:System.Windows.ComponentResourceKey>için, bkz, veya konu Denetim Yazma Genel Bakış "Tema Kaynakları için Tanımlama ve Başvuru Tuşları" bölümüne [bakın.](../controls/control-authoring-overview.md)  
  
 Hem anahtar oluşturma hem de anahtarlı kaynaklara başvurma için, öznitelik sözdizimi genellikle `ComponentResourceKey` biçimlendirme uzantısı için kullanılır.  
  
 Gösterilen kompakt sözdizimi, <xref:System.Windows.ComponentResourceKey.%23ctor%2A> biçimlendirme uzantısının oluşturucu imzasını ve konumsal parametre kullanımına dayanır. Verilen `targetTypeName` ve `targetID` verilen sıra önemlidir. Ayrıntılı sözdizimi <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parametresiz oluşturucuya dayanır ve sonra <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> nesne <xref:System.Windows.ComponentResourceKey.ResourceId%2A> öğesiüzerindeki gerçek öznitelik sözdizimine benzer bir şekilde ayarlar. Ayrıntılı sözdiziminde, özelliklerin ayarlandığı sıra önemli değildir. İlişki ve bu iki alternatif mekanizmaları (kompakt ve ayrıntılı) konu [Markup Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)daha ayrıntılı olarak açıklanmıştır.  
  
 Teknik olarak, değer `targetID` herhangi bir nesne olabilir, bir dize olmak zorunda değildir. Ancak, WPF'de en yaygın `targetID` kullanım, değeri dizeleri olan ve [xamlName Grammar'da](../../../desktop-wpf/xaml-services/xamlname-grammar.md)bu dizeleri geçerli olan formlarla hizalamaktır.  
  
 `ComponentResourceKey`nesne öğesi sözdiziminde kullanılabilir. Bu durumda, uzantıyı düzgün <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> bir <xref:System.Windows.ComponentResourceKey.ResourceId%2A> şekilde başlatmanın hem hem de özelliklerin değerini belirtmesi gerekir.  
  
 Okuyucu uygulamasında, bu biçimlendirme uzantısı için işleme <xref:System.Windows.ComponentResourceKey> sınıf tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `ComponentResourceKey`biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. Öznitelik sözdiziminde { ve } karakterlerini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanan tüm biçimlendirme uzantıları, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini kabul ettiği kuraldır. Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
