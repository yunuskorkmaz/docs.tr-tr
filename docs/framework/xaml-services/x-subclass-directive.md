---
title: "x:Subclass Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5c6e91fcecb60dee2577ea62c2313f8b2c7eecbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 `x:Subclass`Kullanım öncelikle kısmi sınıf bildirimleri desteklemeyen diller için tasarlanmıştır.  
  
 Olarak kullanılan sınıf `x:Subclass` iç içe geçmiş sınıf olamaz ve `x:Subclass` kök nesnesine "Bağımlılıkları" bölümünde açıklandığı gibi başvurmalıdır.  
  
 Aksi takdirde, kavramsal anlamını `x:Subclass` .NET Framework XAML Hizmetleri uygulaması tarafından tanımlanmamış. .NET Framework XAML hizmetlerinde davranışı tarafından hangi XAML biçimlendirme ve kodun yedekleme bağlı genel programlama modeli belirtmediğinden budur. Daha fazla kavramlarını uygulamaları ile ilgili `x:Class` ve `x:Subclass` programlama modelleri veya uygulama modelleri XAML işaretleme, derlenmiş biçimlendirme ve CLR tabanlı gerideki koddan nasıl bağlayacağınızı tanımlamak için kullanmak belirli çerçeveleri tarafından gerçekleştirilir. Her framework davranışı ya da derleme ortamında eklenmelidir belirli bileşenlerini bazılarını etkinleştirmek kendi yapı eylemleri olabilir. Bir çerçeve içinde yapı eylemleri de arka plan kod için kullanılan belirli CLR dil göre değişebilir.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `x:Subclass`bir sayfa kök veya üzerinde olabilir <xref:System.Windows.Application> zaten uygulama tanımında kök `x:Class`. Bildirme `x:Subclass` sayfa veya uygulama kökü veya no burada belirtme dışındaki herhangi bir öğe üzerinde `x:Class` var, bir derleme zamanı hatasına neden olur.  
  
 Türetilen oluşturma sınıflar, iş için doğru `x:Subclass` senaryodur oldukça karmaşık. Ara (dosyaları projenizin obj klasörü .xaml dosya adlarını dahil adlarıyla biçimlendirmesi derleme tarafından üretilen .g) incelemeniz gerekebilir. Bu Ara dosyaları derlenmiş uygulama birleştirilmiş kısmi sınıflarda programlama belirli yapılardan kökenini belirlemenize yardımcı olabilir.  
  
 Olay işleyicileri türetilmiş sınıfında olmalıdır `internal override` (`Friend Overrides` içinde [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) Ara sınıfında derleme sırasında oluşturulan saplamalar işleyicileri için geçersiz kılmak için. Aksi takdirde, türetilmiş sınıf uygulamaları (gölge) Ara sınıf uygulamasını gizleme ve Ara sınıfı işleyici çağrılamaz.  
  
 Tanımladığınızda her ikisi de `x:Class` ve `x:Subclass`, herhangi bir uygulama tarafından başvurulan sınıfı için sağlamak zorunda değildir `x:Class`. Aracılığıyla bir ad vermek yeterlidir `x:Class` derleyici (derleyici ı varsayılan adı bu durumda) Ara dosyalarında oluşturur sınıfı için bazı yönergeler sahip olması özniteliği. Verebilirsiniz `x:Class` uygulaması sınıf; ancak, bu her ikisi de kullanmak için tipik senaryo değil `x:Class` ve `x:Subclass`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [x: Class yönergesi](../../../docs/framework/xaml-services/x-class-directive.md)  
 [XAML ve WPF için özel sınıflar](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
