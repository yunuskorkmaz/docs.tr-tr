---
title: XAML'deki Genel Türler
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 9354f74b978652c36df28a91a6b9db5cfff4bb1e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071740"
---
# <a name="generics-in-xaml"></a>XAML'deki Genel Türler

.NET XAML Hizmetleri uygulandığı <xref:System.Xaml?displayProperty=fullName> gibi genel CLR türlerinin kullanımı için destek sağlar. Bu destek, genel değişken olarak genel değişkenin kısıtlamalarını belirtmeyi ve `Add` genel koleksiyon örnekleri için uygun yöntemi çağırarak kısıtlamayı zorlamayı içerir. Bu konu, XAML'de genel türleri kullanma ve başvurma yönlerini açıklar.

## <a name="xtypearguments"></a>x:TypeArguments

`x:TypeArguments`XAML dili tarafından tanımlanan bir yönergedir. Genel bir tür tarafından desteklenen bir XAML türünün üyesi olarak `x:TypeArguments` kullanıldığında, genel yapıtın kısıtlayıcı tür bağımsız değişkenlerini destek oluşturucuya geçirir. .NET XAML Hizmetleri kullanımıyla `x:TypeArguments`ilgili, sözdizimi örneklerini içeren başvuru sözdizimi için [bkz. x:TypeArguments Yönergesi.](xtypearguments-directive.md)

Bir `x:TypeArguments` dize aldığından ve tür dönüştürücü desteği olduğundan, genellikle XAML kullanımında öznitelik olarak bildirilir.

XAML düğüm akışında, bildirilen `x:TypeArguments` bilgiler düğüm akışındaki bir <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> `StartObject` konumdan elde edilebilir. İade <xref:System.Xaml.XamlType> değeri, <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> değerlerin listesidir. XAML türünün genel bir türü temsil edip <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>etmediğinin belirlenmesi.

## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>XAML'de Jenler için Kurallar ve Sözdizimi Kuralları

XAML'de, genel bir tür her zaman kısıtlanmış bir genel olarak temsil edilmelidir. XAML türü sisteminde veya XAML düğüm akışında sınırlandırılmamış bir jenerik hiçbir zaman bulunmaz ve XAML biçimlendirmesinde temsil edilemez. Genel bir genel, genel bir tür tarafından `x:TypeArguments`başvurulan bir genel in iç içe türü kısıtlaması olduğu durumlar `x:Type` veya genel bir tür için CLR türü başvurusu sağlayan durumlar için XAML öznitelik sözdizimi içinde başvurulabilir. Genel gönderme .NET XAML <xref:System.Xaml.Schema.XamlTypeTypeConverter> Hizmetleri tarafından tanımlanan sınıf aracılığıyla desteklenir.

XAML öznitelik sözdizimi <xref:System.Xaml.Schema.XamlTypeTypeConverter> formu tarafından etkin tipik MSIL / CLR sözdizimi kuralı nı değiştirir, genel jenerik türleri ve kısıtlamaları için açı parantezi kullanır ve bunun yerine kısıtlama kapsayıcısı için parantez değiştirir. Örneğin, bkz [x:TypeArguments Yönergesi](xtypearguments-directive.md).

## <a name="generics-and-xaml-2009-features"></a>Jenerik ve XAML 2009 Özellikleri

Ortak dil ilkelleri için XAML türleri elde etmek için CLR taban türlerini eşlemek yerine [XAML 2009 kullanıyorsanız, XAML 2009 yerleşik türleri](types-for-primitives.md) bilgi öğeleri olarak `x:TypeArguments`kullanabilirsiniz. Örneğin, aşağıdakileri bildirebilirsiniz (önek eşlemeleri `x` gösterilmez, ancak XAML 2009 için XAML dili XAML ad alanıdır):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

## <a name="generics-support-in-wpf"></a>WPF'de Jenerik Desteği

Özellikle WPF hedeflendiğinde XAML 2006 kullanımı için [x:Class](xclass-directive.md) aynı öğe `x:TypeArguments`üzerinde de sağlanmalıdır ve bu öğe bir XAML belgesinde kök öğe olmalıdır. Kök öğe, en az bir tür bağımsız değişkeni olan genel bir türle eşlenmelidir. <xref:System.Windows.Navigation.PageFunction%601> bunun bir örneğidir.

Genel kullanımları desteklemek için olası geçici geçici işler, genel türleri döndürebilen özel bir biçimlendirme uzantısı tanımlamayı veya genel bir türden türeyen ancak kendi sınıf tanımındaki genel kısıtlamayı düzleştiren bir sarma sınıfı tanımı sağlamayı içerir.

WPF'de XAML 2009 özelliklerini, `x:TypeArguments`ancak yalnızca gevşek XAML (biçimlendirme derlememiş XAML) ile birlikte kullanabilirsiniz. WPF için biçimlendirmeyle derlenen XAML ve XAML'nin BAML formu şu anda XAML 2009 anahtar kelimelerini ve özelliklerini desteklemez.

.NET Framework 3.5 için Windows İş Akışı Temeli'ndeki özel iş akışları genel XAML kullanımını desteklemez.

## <a name="see-also"></a>Ayrıca bkz.

- [x:TypeArguments Yönergesi](xtypearguments-directive.md)
- [x:Class Yönergesi](xclass-directive.md)
- [XAML Dili Ortak Temelleri İçin Yerleşik Türler](types-for-primitives.md)
