---
title: x:Static İşaretleme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072027"
---
# <a name="xstatic-markup-extension"></a>x:Static İşaretleme Uzantısı

Ortak Dil Belirtimi (CLS) uyumlu bir şekilde tanımlanan statik by-value kodu varlığına başvurur. Başvurulan statik özellik XAML'deki bir özelliğin değerini sağlamak için kullanılabilir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>XAML Değerleri

| | |
|-|-|
|`prefix`|İsteğe bağlı. Eşlenen, varsayılan olmayan XAML ad alanına başvuran bir önek. `prefix`varsayılan XAML ad alanından gelen statik özelliklere nadiren başvuru yaptığınızdan, kullanımda açıkça gösterilir. Bkz. Açıklamalar.|
|`typeName`|Gereklidir. İstenilen statik üyeyi tanımlayan türün adı.|
|`staticMemberName`|Gereklidir. İstenilen statik değer üyesinin adı (sabit, statik özellik, alan veya numaralandırma değeri).|

## <a name="remarks"></a>Açıklamalar

Başvurulan kod varlığı aşağıdakilerden biri olmalıdır:

- Bir sabit
- Statik bir özellik
- Bir alan
- Numaralandırma değeri

Statik olmayan bir özellik gibi başka bir kod varlığı belirtmek, XAML biçimlendirme derlenmişse derleme zamanı hatasına veya XAML yük zamanı ayrıştırma özel durumu haline gelir.

Geçerli XAML belgesi için varsayılan XAML ad alanında olmayan statik alanlara veya özelliklere `x:Static` başvuru yapabilirsiniz; ancak, bu bir önek eşleme gerektirir. XAML ad alanları, XAML belgesinin kök öğesi üzerinde hemen hemen her zaman tanımlanır.

Statik özellikleri için arama işlemleri .NET XAML Hizmetleri ve xaml okuyucuları ve XAML yazarları tarafından, varsayılan XAML şeması bağlamı yla çalışırken gerçekleştirilebilir. Bu XAML şeması bağlamı, nesne grafiği yapısı için gerekli statik değerleri sağlamak için CLR yansımasını kullanabilir. Varsayılan `typeName` XAML şeması bağlamını kullanırken veya varolan tüm CLR tabanlı XAML uygulama çerçevelerini kullanırken bunlar temelde aynı ad olmasına rağmen, belirttiğiniz şey aslında bir CLR türü adı değil, BIR CLR türü adıdır.

Doğrudan bir özelliğin değeri türü olmayan başvurular yaparken `x:Static` dikkatli olun. XAML işleme dizisinde, biçimlendirme uzantısından sağlanan değerler ek değer dönüştürmeyi çağırmaz. Başvurunuz `x:Static` bir metin dizesi oluştursa ve metin dizesini temel alan öznitelik değerleri için bir değer dönüştürmesi genellikle belirli bir üye veya iade türündeki herhangi bir üye değerleri için gerçekleşse bile bu durum geçerlidir.

Öznitelik sözdizimi, bu işaretleme uzantısı ile kullanılan en yaygın sözdizimidir. Tanımlayıcı dizesonra sağlanan `x:Static` dize belirteci alttaki <xref:System.Windows.Markup.StaticExtension.Member%2A> <xref:System.Windows.Markup.StaticExtension> uzantı sınıfının değeri olarak atanır.

Teknik olarak mümkün olan iki XAML kullanımı daha vardır. Ancak, gereksiz yere ayrıntılı olduğundan bu kullanımlar daha az yaygındır:

01. Nesne öğesi sözdizimi.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. Başlatma dizesi için açık Üye özelliği ile sözdizimini atfedin.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

.NET XAML Hizmetleri uygulamasında, bu biçimlendirme uzantısı için <xref:System.Windows.Markup.StaticExtension> işleme sınıf tarafından tanımlanır.

`x:Static`biçimlendirme uzantısıdır. XAML'deki tüm biçimlendirme `{` uzantıları, bir XAML işlemcisinin biçimlendirme uzantısının bir değer sağlaması gerektiğini kabul ettiği kural olan öznitelik sözdiziminde karakterleri kullanır. `}` Biçimlendirme uzantıları hakkında daha fazla bilgi için [XAML Genel Bakış için Biçimlendirme Uzantıları'na](markup-extensions-overview.md)bakın.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

WPF programlama için kullandığınız varsayılan XAML ad alanı çok yararlı statik özellikler içermez ve yararlı statik özelliklerin çoğu gerektirmeden `{x:Static}` kullanımı kolaylaştıran tür dönüştürücüler gibi destek vardır. Statik özellikler için, aşağıdakilerden biri doğruysa, XAML ad alanı için bir önek eşlemelisiniz:

- WPF'de var olan ancak WPF için varsayılan XAML ad alanının bir`http://schemas.microsoft.com/winfx/2006/xaml/presentation`parçası olmayan bir türe başvurursunuz ( ). Bu kullanmak `x:Static`için oldukça yaygın bir senaryodur. Örneğin, <xref:System.Environment> sınıfın statik `x:Static` özelliklerine başvurmak için <xref:System> CLR ad alanı ve mscorlib derlemesine XAML ad alanı eşlemesi içeren bir başvuru kullanabilirsiniz.

- Özel bir derlemeden bir türe başvuruyorsunuz.

- WPF derlemesinde var olan bir türe başvuruyorsunuz, ancak bu tür WPF varsayılan XAML ad alanının bir parçası olarak eşlenmemiş bir CLR ad alanı içindedir. CLR ad alanlarının WPF için varsayılan XAML ad alanına eşlemesi çeşitli WPF derlemelerinde tanımlarla gerçekleştirilir (bu kavram hakkında daha fazla bilgi için Bkz. [XAML İsim Alanları ve WPF XAML için Namespace Eşleme).](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md) Bu CLR ad alanı çoğunlukla XAML için tasarlanmayan sınıf tanımlarından oluşuyorsa, eşlenen CLR <xref:System.Windows.Threading>ad alanları kullanılabilir.

WPF için öneklerin ve XAML ad alanlarının nasıl kullanılacağı hakkında daha fazla bilgi [için WPF XAML için XAML Ad Alanları ve Ad Alanı Eşleme'ye](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [x:Type İşaretleme Uzantısı](xtype-markup-extension.md)
- [WPF'den System.Xaml'e Geçirilen Türler](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
