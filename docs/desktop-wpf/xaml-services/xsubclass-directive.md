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
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071369"
---
# <a name="xsubclass-directive"></a>x:Subclass Yönergesi

XAML biçimlendirmesi de sağlandığında davranışı `x:Class` derle'i değiştirir. Buna dayalı kısmi bir sınıf `x:Class`oluşturmak yerine, sağlanan `x:Class` bir ara sınıf olarak oluşturulur ve daha sonra `x:Class`sağlanan türemiş sınıfın temel alınması beklenir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`namespace`|İsteğe bağlı. Bir CLR ad alanı içerir. `classname` `namespace` Belirtilirse, nokta (.) ayrılır `namespace` `classname`ve .|
|`classname`|Gereklidir. Yüklenen XAML'yi ve bu XAML için kod arkanızı bağlayan kısmi sınıfın CLR adını belirtir. Bkz. Açıklamalar.|
|`subclassNamespace`|İsteğe bağlı. Her ad `namespace` alanı diğerini çözebilirse farklı olabilir. Bir CLR ad alanı içerir. `subclassName` `subclassName` Belirtilirse, nokta (.) ayrılır `subclassNamespace` `subclassName`ve .|
|`subclassName`|Gereklidir. Alt sınıfın CLR adını belirtir.|

## <a name="dependencies"></a>Bağımlılıklar

[x:Sınıf Yönergesi](xclass-directive.md) de aynı nesne üzerinde sağlanmalıdır ve bu nesne XAML üretiminin kök öğesi olmalıdır.

## <a name="remarks"></a>Açıklamalar

`x:Subclass`kullanımı öncelikle kısmi sınıf bildirimlerini desteklemeyen diller için tasarlanmıştır.

İç içe sınıf `x:Subclass` olarak kullanılan sınıf, `x:Subclass` "Bağımlılıklar" bölümünde açıklandığı gibi kök nesneye başvurmalıdır.

Aksi takdirde, kavramsal `x:Subclass` anlamı .NET XAML Hizmetleri uygulaması ile tanımlanmaz. Bunun nedeni, .NET XAML Hizmetleri davranışının XAML biçimlendirme ve destek kodunun bağlı olduğu genel programlama modelini belirtmesidir. XAML `x:Class` biçimlendirmesi, derlenmiş biçimlendirme ve CLR tabanlı kod arkası bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçevelerle ilgili ve `x:Subclass` diğer kavramların uygulamaları gerçekleştirilir. Her çerçevenin, bazı davranışları veya yapı ortamına dahil edilmesi gereken belirli bileşenleri etkinleştiren kendi yapı eylemleri olabilir. Bir çerçeve içinde, yapı eylemleri de kod arkası için kullanılan belirli CLR dile bağlı olarak değişebilir.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

`x:Subclass`bir sayfa kökünde veya <xref:System.Windows.Application> zaten var `x:Class`uygulama tanımında kök üzerinde olabilir. Bir `x:Subclass` sayfa veya uygulama kökü dışındaki herhangi bir öğeüzerinde `x:Class` bildirimde bulunmak veya varsa belirtme, derleme zamanı hatasına neden olur.

`x:Subclass` Senaryo için doğru çalışan türemiş sınıflar oluşturmak oldukça karmaşıktır. Ara dosyaları (.xaml dosya adlarını içeren adlarla birlikte biçimlendirme derlemesi ile projenizin obj klasöründe üretilen .g dosyalarını) incelemeniz gerekebilir. Bu ara dosyalar, derlenen uygulamada birleştirilmiş kısmi sınıflardaki belirli programlama yapılarının kaynağını belirlemenize yardımcı olabilir.

Türemiş sınıftaki olay işleyicileri, derleme sırasında ara sınıfta oluşturulan işleyicilerin saplamalarını geçersiz kılmak için (Microsoft `internal override` `Friend Overrides` Visual Basic'te) olmalıdır. Aksi takdirde, türemiş sınıf uygulamaları ara sınıf uygulamasını gizle (gölge) ve ara sınıf işleyicileri çağrılmaz.

Her ikisini `x:Class` ve `x:Subclass`, tarafından başvurulan sınıf için herhangi bir uygulama `x:Class`sağlamanız gerekmez. Derleyicinin ara dosyalarda oluşturduğu `x:Class` sınıf için bazı yönergelere sahip olması için öznitelik üzerinden bir ad vermeniz gerekir (derleyici bu durumda varsayılan bir ad seçmez). Sınıfa `x:Class` bir uygulama verebilirsiniz; ancak, bu hem `x:Class` ve `x:Subclass`kullanmak için tipik bir senaryo değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [WPF için XAML ve Özel Sınıflar](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
