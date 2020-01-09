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
ms.openlocfilehash: 2ccc4f3154996a4e442a4092833f5c9ed9c8938a
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559467"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey Biçimlendirme Uzantısı
Dış derlemelerden yüklenen kaynaklar için anahtarlar tanımlar ve başvurur. Bu, bir derlemede veya bir sınıftaki açık kaynak sözlüğü yerine bir derlemede hedef türü belirtmesini sağlar.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML öznitelik kullanımı (anahtar ayarlama, sıkıştırma)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML öznitelik kullanımı (anahtar ayarlama, ayrıntılı)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML öznitelik kullanımı (kaynak isteme, Compact)  
  
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
|`targetTypeName`|Kaynak derlemesinde tanımlanan ortak ortak dil çalışma zamanı (CLR) türünün adı.|  
|`targetID`|Kaynak için anahtar. Kaynaklar arandığında, `targetID` kaynağın [X:Key yönergesine](../../../desktop-wpf/xaml-services/xkey-directive.md) benzer.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıdaki kullanımlar bölümünde görüldüğü gibi, iki yerde bir {`ComponentResourceKey`} biçimlendirme uzantısı kullanımı bulunur:  
  
- Bir denetim yazarı tarafından sağlandığı şekilde, tema kaynak sözlüğündeki bir anahtarın tanımı.  
  
- Denetimi yeniden oluştururken, ancak denetimin temaları tarafından belirtilen kaynaklardan gelen özellik değerlerini kullanmak istediğinizde derlemeden bir tema kaynağına erişme.  
  
 Temalardan gelen bileşen kaynaklarına başvurmak için, `{StaticResource}`yerine `{DynamicResource}` kullanmanız genellikle önerilir. Bu, kullanımlar içinde gösterilir. `{DynamicResource}`, temanın kendisi Kullanıcı tarafından değiştirilebileceğinden önerilir. Bir temayı desteklemek için denetim yazarının amacını en yakından karşılayan bileşen kaynağını isterseniz, bileşen kaynak başvurunuz ' ı da dinamik olacak şekilde etkinleştirmeniz gerekir.  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>, kaynağın gerçekten tanımladığı hedef derlemede bulunan bir türü tanımlar. `ComponentResourceKey`, tam olarak <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> tanımlandığı, ancak sonunda türü başvurulan derlemeler aracılığıyla çözümlenmesi gereken bağımsız olarak tanımlanabilir ve kullanılabilir.  
  
 <xref:System.Windows.ComponentResourceKey> için ortak bir kullanım, daha sonra bir sınıfın üyeleri olarak ortaya çıkarılan anahtarlar tanımlamaktır. Bu kullanım için biçimlendirme uzantısını değil <xref:System.Windows.ComponentResourceKey> Class oluşturucusunu kullanırsınız. Daha fazla bilgi için, bkz. <xref:System.Windows.ComponentResourceKey>veya "Tema kaynakları için anahtarları tanımlama ve başvuru" bölümü, [Denetim yazma konusunun genel bakış](../controls/control-authoring-overview.md).  
  
 Hem anahtar oluşturma hem de anahtarlı kaynaklara başvurma için öznitelik sözdizimi genellikle `ComponentResourceKey` biçimlendirme uzantısı için kullanılır.  
  
 Gösterilen Compact sözdizimi, bir işaretleme uzantısının <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Oluşturucu imzasını ve Konumsal parametre kullanımını temel alır. `targetTypeName` ve `targetID` verilen sıra önemlidir. Ayrıntılı sözdizimi, <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> parametresiz oluşturucuya dayanır ve sonra <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve <xref:System.Windows.ComponentResourceKey.ResourceId%2A> bir nesne öğesindeki doğru bir öznitelik sözdizimine benzer şekilde ayarlar. Ayrıntılı sözdiziminde, özelliklerin ayarlandığı sıra önemli değildir. Bu iki alternatifin (Compact ve verbose) ilişkisi ve mekanizmaları, konu [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)'de daha ayrıntılı olarak açıklanmıştır.  
  
 Teknik olarak, `targetID` değeri herhangi bir nesne olabilir, bir dize olması gerekmez. Ancak WPF 'nin en yaygın kullanımları, `targetID` değerini dizeler olan formlarla ve bu tür dizelerin [XamlName dilbilgisinde](../../../desktop-wpf/xaml-services/xamlname-grammar.md)geçerli olduğu şekilde hizalanacaktır.  
  
 `ComponentResourceKey`, nesne öğesi sözdiziminde kullanılabilir. Bu durumda, uzantıyı doğru şekilde başlatmak için hem <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> hem de <xref:System.Windows.ComponentResourceKey.ResourceId%2A> özelliklerinin değerinin belirtilmesi gerekir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] okuyucu uygulamasında, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.ComponentResourceKey> sınıfı tarafından tanımlanır.  
  
 `ComponentResourceKey`, biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakterlerini kullanır. Bu, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinin, bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
