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
ms.openlocfilehash: b373b33fcc962e49aa220f31e24b1484a0a8cd98
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401595"
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
|`targetID`|Kaynak için anahtar. Kaynaklar arandığında, `targetID` kaynağın [x:Key yönergesine](../../xaml-services/x-key-directive.md) benzer olacaktır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıdaki kullanımlar bölümünde görüldüğü gibi, iki yerde bir`ComponentResourceKey`{} biçimlendirme uzantısı kullanımı bulunur:  
  
- Bir denetim yazarı tarafından sağlandığı şekilde, tema kaynak sözlüğündeki bir anahtarın tanımı.  
  
- Denetimi yeniden oluştururken, ancak denetimin temaları tarafından belirtilen kaynaklardan gelen özellik değerlerini kullanmak istediğinizde derlemeden bir tema kaynağına erişme.  
  
 Temalardan gelen bileşen kaynaklarına başvurmak için, genellikle `{DynamicResource}` `{StaticResource}`yerine kullanmanız önerilir. Bu, kullanımlar içinde gösterilir. `{DynamicResource}`teması Kullanıcı tarafından değiştirilebileceğinden önerilir. Bir temayı desteklemek için denetim yazarının amacını en yakından karşılayan bileşen kaynağını isterseniz, bileşen kaynak başvurunuz ' ı da dinamik olacak şekilde etkinleştirmeniz gerekir.  
  
 , <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> Kaynağın gerçekten tanımladığı hedef derlemede bulunan bir türü tanımlar. , Tam olarak tanımlandığı <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> yerin bilinmesinin bağımsız olarak tanımlanabilir ve kullanılabilir, ancak sonunda türü başvurulan derlemeler aracılığıyla çözümlenmelidir. `ComponentResourceKey`  
  
 İçin <xref:System.Windows.ComponentResourceKey> ortak bir kullanım, daha sonra bir sınıfın üyeleri olarak ortaya çıkarılan anahtarlar tanımlamaktır. Bu kullanım için, biçimlendirme uzantısını değil <xref:System.Windows.ComponentResourceKey> sınıf oluşturucusunu kullanırsınız. Daha fazla bilgi için, <xref:System.Windows.ComponentResourceKey>veya [Denetim yazma genel bakış](../controls/control-authoring-overview.md)konusunun "Tema kaynakları için anahtar tanımlama ve başvuru" bölümüne bakın.  
  
 Her iki anahtar oluşturmak ve anahtarlı kaynaklara başvurmak için, `ComponentResourceKey` biçimlendirme uzantısı için genellikle öznitelik sözdizimi kullanılır.  
  
 Gösterilen Compact sözdizimi, bir işaretleme uzantısının <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> Oluşturucu imzasını ve Konumsal parametre kullanımını temel alır. `targetTypeName` Ve`targetID` verilen sıra önemlidir. Verbose sözdizimi <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> parametresiz oluşturucuyu kullanır ve ardından bir nesne öğesindeki doğru bir öznitelik sözdizimine <xref:System.Windows.ComponentResourceKey.ResourceId%2A> benzer şekilde <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> ve öğesini ayarlar. Ayrıntılı sözdiziminde, özelliklerin ayarlandığı sıra önemli değildir. Bu iki alternatifin (Compact ve verbose) ilişkisi ve mekanizmaları, konu [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)'de daha ayrıntılı olarak açıklanmıştır.  
  
 Teknik olarak, için `targetID` değeri herhangi bir nesne olabilir, bir dize olması gerekmez. Ancak WPF 'nin en yaygın kullanımları, `targetID` değeri dizeler olan formlarla ve bu tür dizelerin [XamlName dilbilgisinde](../../xaml-services/xamlname-grammar.md)geçerli olduğu şekilde hizalanacaktır.  
  
 `ComponentResourceKey`nesne öğesi söz dizimi içinde kullanılabilir. Bu durumda, uzantıyı doğru şekilde başlatmak için hem <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> hem <xref:System.Windows.ComponentResourceKey.ResourceId%2A> de özelliklerinin değerinin belirtilmesi gerekir.  
  
 Okuyucu uygulamasında, bu biçimlendirme <xref:System.Windows.ComponentResourceKey> uzantısının işlenmesi sınıfı tarafından tanımlanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `ComponentResourceKey`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve bu gereksinim, belirli türler veya özellikler üzerine tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tüm biçimlendirme uzantıları öznitelik sözdiziminde {ve} karakteri kullanır. Bu, bir işlemcinin bir biçimlendirme uzantısının özniteliği işlemesi gerektiğini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [Denetim Yazımına Genel Bakış](../controls/control-authoring-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
