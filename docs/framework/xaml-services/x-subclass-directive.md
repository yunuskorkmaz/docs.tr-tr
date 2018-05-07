---
title: x:Subclass Yönergesi
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: b04982ff0b7685b4e4b809255e3bbe541b42cb9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xsubclass-directive"></a>x:Subclass Yönergesi
XAML biçimlendirme derleme davranışını değiştiren zaman `x:Class` de sağlanır. Temel alan bir parçalı sınıf oluşturmak yerine `x:Class`, sağlanan `x:Class` Ara bir sınıf olarak oluşturulur ve ardından, sağlanan türetilmiş sınıf temel beklenen `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`namespace`|İsteğe bağlı. İçeren bir CLR ad alanını belirtir `classname`. Varsa `namespace` belirtilirse, nokta (.) ayıran `namespace` ve `classname`.|  
|`classname`|Gerekli. CLR yüklenen XAML ve, arka plan kod bu XAML bağlayan kısmi sınıfın adını belirtir. Açıklamalar bakın.|  
|`subclassNamespace`|İsteğe bağlı. Farklı olabilir `namespace` ise her ad alanı diğer çözebilirsiniz. İçeren bir CLR ad alanını belirtir `subclassName`. Varsa `subclassName` belirtilirse, nokta (.) ayıran `subclassNamespace` ve `subclassName`.|  
|`subclassName`|Gerekli. Bir alt CLR adını belirtir.|  
  
## <a name="dependencies"></a>Bağımlılıklar  
 [x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md) de aynı nesnede sağlanması gerekir ve bu nesne XAML üretim kök öğesi olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `x:Subclass` Kullanım öncelikle kısmi sınıf bildirimleri desteklemeyen diller için tasarlanmıştır.  
  
 Olarak kullanılan sınıf `x:Subclass` iç içe geçmiş sınıf olamaz ve `x:Subclass` kök nesnesine "Bağımlılıkları" bölümünde açıklandığı gibi başvurmalıdır.  
  
 Aksi takdirde, kavramsal anlamını `x:Subclass` .NET Framework XAML Hizmetleri uygulaması tarafından tanımlanmamış. .NET Framework XAML hizmetlerinde davranışı tarafından hangi XAML biçimlendirme ve kodun yedekleme bağlı genel programlama modeli belirtmediğinden budur. Daha fazla kavramlarını uygulamaları ile ilgili `x:Class` ve `x:Subclass` programlama modelleri veya uygulama modelleri XAML işaretleme, derlenmiş biçimlendirme ve CLR tabanlı gerideki koddan nasıl bağlayacağınızı tanımlamak için kullanmak belirli çerçeveleri tarafından gerçekleştirilir. Her framework davranışı ya da derleme ortamında eklenmelidir belirli bileşenlerini bazılarını etkinleştirmek kendi yapı eylemleri olabilir. Bir çerçeve içinde yapı eylemleri de arka plan kod için kullanılan belirli CLR dil göre değişebilir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `x:Subclass` bir sayfa kök veya üzerinde olabilir <xref:System.Windows.Application> zaten uygulama tanımında kök `x:Class`. Bildirme `x:Subclass` sayfa veya uygulama kökü veya no burada belirtme dışındaki herhangi bir öğe üzerinde `x:Class` var, bir derleme zamanı hatasına neden olur.  
  
 Türetilen oluşturma sınıflar, iş için doğru `x:Subclass` senaryodur oldukça karmaşık. Ara (dosyaları projenizin obj klasörü .xaml dosya adlarını dahil adlarıyla biçimlendirmesi derleme tarafından üretilen .g) incelemeniz gerekebilir. Bu Ara dosyaları derlenmiş uygulama birleştirilmiş kısmi sınıflarda programlama belirli yapılardan kökenini belirlemenize yardımcı olabilir.  
  
 Olay işleyicileri türetilmiş sınıfında olmalıdır `internal override` (`Friend Overrides` Visual Basic'de) Ara sınıfında derleme sırasında oluşturulan saplamalar işleyicileri için geçersiz kılmak için. Aksi takdirde, türetilmiş sınıf uygulamaları (gölge) Ara sınıf uygulamasını gizleme ve Ara sınıfı işleyici çağrılamaz.  
  
 Tanımladığınızda her ikisi de `x:Class` ve `x:Subclass`, herhangi bir uygulama tarafından başvurulan sınıfı için sağlamak zorunda değildir `x:Class`. Aracılığıyla bir ad vermek yeterlidir `x:Class` derleyici (derleyici ı varsayılan adı bu durumda) Ara dosyalarında oluşturur sınıfı için bazı yönergeler sahip olması özniteliği. Verebilirsiniz `x:Class` uygulaması sınıf; ancak, bu her ikisi de kullanmak için tipik senaryo değil `x:Class` ve `x:Subclass`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x:Class Yönergesi](../../../docs/framework/xaml-services/x-class-directive.md)  
 [WPF için XAML ve Özel Sınıflar](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
