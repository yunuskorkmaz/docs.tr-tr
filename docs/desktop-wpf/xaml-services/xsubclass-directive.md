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
ms.openlocfilehash: b888ef73d1678fd37c984e4bb223f24e5b65d2cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540725"
---
# <a name="xsubclass-directive"></a>x:Subclass Yönergesi

Ayrıca sağlandığında XAML biçimlendirme derleme davranışını değiştirir `x:Class` . ' I temel alan kısmi bir sınıf oluşturmak yerine, `x:Class` belirtilen `x:Class` bir ara sınıf olarak oluşturulur ve ardından, sağlanmış türetilmiş sınıfınızın temel olması beklenir `x:Class` .

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`namespace`|İsteğe bağlı. İçeren bir CLR ad alanı belirtir `classname` . `namespace`Belirtilmişse, nokta (.) `namespace` ve ayırır `classname` .|
|`classname`|Gereklidir. Yüklenen XAML 'yi ve bu XAML için arka plan kodunuzu bağlayan kısmi sınıfın CLR adını belirtir. Bkz. açıklamalar.|
|`subclassNamespace`|İsteğe bağlı. , `namespace` Her bir ad alanı diğerini çözümleyebiliyorsanız, öğesinden farklı olabilir. İçeren bir CLR ad alanı belirtir `subclassName` . `subclassName`Belirtilmişse, nokta (.) `subclassNamespace` ve ayırır `subclassName` .|
|`subclassName`|Gereklidir. Alt sınıfın CLR adını belirtir.|

## <a name="dependencies"></a>Bağımlılıklar

[X:Class yönergesi](xclass-directive.md) aynı nesne üzerinde de sağlanmalıdır ve bu nesnenin xaml üretiminin kök öğesi olması gerekir.

## <a name="remarks"></a>Açıklamalar

`x:Subclass` Kullanım öncelikle kısmi sınıf bildirimlerini desteklemeyen diller için tasarlanmıştır.

Olarak kullanılan sınıfı, `x:Subclass` iç içe geçmiş bir sınıf olamaz ve `x:Subclass` "bağımlılıklar" bölümünde açıklandığı gibi kök nesnesine başvurmalıdır.

Aksi takdirde, kavramsal anlamı `x:Subclass` .net xaml Hizmetleri uygulamasıyla tanımlanmamıştır. Bunun nedeni, .NET XAML Hizmetleri davranışının XAML biçimlendirme ve yedekleme kodunun bağlı olduğu genel programlama modelini belirtmemesi nedeniyle oluşur. Ve ile ilgili başka kavramların `x:Class` Uygulamaları `x:Subclass` , XAML biçimlendirme, derlenmiş BIÇIMLENDIRME ve clr tabanlı arka plan kod bağlamayı tanımlamak için programlama modellerini veya uygulama modellerini kullanan belirli çerçeveler tarafından gerçekleştirilir. Her çerçeve, bazı davranışlarının veya yapı ortamına dahil olması gereken belirli bileşenlerin bir kısmını etkinleştiren kendi derleme eylemlerine sahip olabilir. Bir çerçeve içinde, derleme eylemleri de arka plan kodu için kullanılan belirli CLR diline göre farklılık gösterebilir.

## <a name="wpf-usage-notes"></a>WPF kullanım notları

`x:Subclass` , zaten sahip olan uygulama tanımındaki bir sayfa kökü veya kök üzerinde olabilir <xref:System.Windows.Application> `x:Class` . `x:Subclass`Bir sayfa veya uygulama kökü dışında herhangi bir öğe üzerinde bildirme ya da bunu yok olarak belirleme `x:Class` , derleme zamanı hatasına neden olur.

Senaryo için doğru şekilde çalışan türetilmiş sınıfların oluşturulması `x:Subclass` oldukça karmaşıktır. Ara dosyaları (. xaml dosya adlarını içeren adlarla biçimlendirme derlemesi tarafından, projenizin obj klasöründe oluşturulan. g dosyaları) incelemeniz gerekebilir. Bu ara dosyalar, derlenmiş uygulamadaki birleştirilmiş kısmi sınıflarda belirli programlama yapılarının kaynağını belirlemenize yardımcı olabilir.

Türetilmiş sınıftaki olay işleyicileri `internal override` `Friend Overrides` , derleme sırasında ara sınıfta oluşturulan işleyicilerle ilgili saplamaları geçersiz kılmak Için (Microsoft Visual Basic) olmalıdır. Aksi halde, türetilmiş sınıf uygulamaları gizle (gölge) ara sınıf uygulaması ve ara sınıf işleyicileri çağrılmaz.

Hem hem de tanımladığınızda `x:Class` `x:Subclass` , tarafından başvurulan sınıf için herhangi bir uygulama sağlamanız gerekmez `x:Class` . `x:Class`Derleyicinin ara dosyalarda oluşturduğu sınıfa yönelik bir kılavuza sahip olması için yalnızca özniteliği aracılığıyla bir ad vermeniz gerekir (derleyici bu durumda varsayılan bir ad seçmez). `x:Class`Sınıfına bir uygulama verebilirsiniz; ancak, bu, hem hem de kullanımı için tipik bir senaryo değildir `x:Class` `x:Subclass` .

## <a name="see-also"></a>Ayrıca bkz.

- [x:Class Yönergesi](xclass-directive.md)
- [WPF için XAML ve Özel Sınıflar](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
