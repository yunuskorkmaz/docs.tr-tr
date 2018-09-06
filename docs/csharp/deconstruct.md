---
title: Demetleri ve diğer türleri ayrıştırma
description: Demetleri ve diğer türleri ayrıştırma öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 48724c65de4fe71294eb5c61c1891d9d56c9b5a4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039309"
---
# <a name="deconstructing-tuples-and-other-types"></a>Demetleri ve diğer türleri ayrıştırma

Bir demet basit bir yöntem çağrısından birden çok değer almanıza olanak sağlar. Ancak kayıt almak sonra bireysel öğelerini işlemek vardır. Bir öğeye göre temelinde bunu aşağıdaki örnekte gösterildiği gibi yavaşlatan bir yöntemdir. `QueryCityData` Yöntemi 3-tanımlama grubu döndürür ve alt öğelerin her biri ayrı bir işlemde bir değişkene atanır.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Bir nesneden birden çok alan ve özellik değerlerini alma eşit hantal olabilir: bir üye tarafından üyesi olarak bir değişken için bir alan veya özellik değer atamanız gerekir.

C# 7.0 ile başlayarak, birden çok öğe tanımlama grubundan almak veya tek bir nesnenin birden fazla alan, özellik ve hesaplanan değerleri almak *Ayrıştır* işlemi. Bir demet ayrıştırma bağımsız değişkenlerini öğelerine atayın. Bir nesne ayrıştırma bağımsız değişkenleri için seçilen değerler atayın.

## <a name="deconstructing-a-tuple"></a>Bir demet ayrıştırma

Tüm öğeleri tek bir işlemde bir tanımlama grubu gitmeniz olanak sağlayan bir tanımlama grubu ayrıştırma için C# özellikleri yerleşik destekler. Bir demet ayrıştırma genel sözdizimi bir tanımlama sözdizimi benzer: parantez içinde bir atama ifadesi sol tarafındaki atanacak her öğe için olan değişkenler alın. Örneğin aşağıdaki deyim 4 bölütlü öğelerini dört ayrı değişkenlere atar:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Bir demet ayrıştırma için üç yol vardır:

- Parantez içinde her alanın türünü açıkça bildirebilirsiniz. Aşağıdaki örnek bu yaklaşım kullanan tarafından döndürülen 3 demet ayrıştırma `QueryCityData` yöntemi.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Kullanabileceğiniz `var` algılar, C# her bir değişken türü anahtar sözcüğü. Yerleştirdiğiniz `var` parantezler dışında anahtar sözcüğü. Aşağıdaki örnek tür çıkarımı tarafından döndürülen 3 demet ayrıştırma kullanır `QueryCityData` yöntemi.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Ayrıca `var` tek tek tüm değişken bildirimlerini parantez içinde ile anahtar sözcüğü.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Bu hantal ve önerilmez.

- Son olarak, zaten bildirilen değişkenlere demet ayrıştırma.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Dizideki her alan aynı türde olsa bile dışındaki parantezler belirli bir tür belirtemezsiniz. Bu, "ayrıştırma 'var (...)' form 'var' için belirli bir türe izin vermiyor." CS8136, derleyici hatası oluşturur.

Not, ayrıca her öğesi için bir değişken atamanız gerekir. Herhangi bir öğe atlarsanız, derleyici hatası CS8132, "'x' öğelerini tanımlama grubu 'y' değişkenlere ayrıştırılamıyor." oluşturur.

Bildirimler ve ayrıştırma deyiminin sol tarafında mevcut değişkenlere atamalarını karıştırılamaz unutmayın. Derleyici Hatası CS8184, "ayrıştırma deyiminin bildirimler ve sol taraftaki ifadelerini karıştırılamaz." oluşturur. ne zaman üyeleri yeni bildirilmiş ve mevcut değişkenler içerir.

## <a name="deconstructing-tuple-elements-with-discards"></a>Tanımlama grubu öğelerle ayrıştırma atar

Genellikle bir demet ayrıştırma, bazı öğeler yalnızca değerlerde ilgilenen. C# 7.0 ile başlayarak, C# desteği avantajlarından yararlanabilirsiniz *atar*, değerleri yok saymak için seçtiğiniz salt yazılır değişkenleri olduğu. Bir atma eylemi atanmış bir alt çizgi karakteriyle ("\_") bir atama. İstediğiniz kadar çok değerle atabilirsiniz; tüm tek atma tarafından temsil edilen `_`.

Aşağıdaki örnek, iptali ile tanımlama grubu kullanımını gösterir. `QueryCityDataForYears` Yöntemi bir şehir, kendi alanı, bir yıl, bu yıl, ikinci yıl ve bu ikinci yıl için city'nin popülasyonu city'nin nüfusunu adı ile 6-tanımlama grubu döndürür. Bu örnek, popülasyondaki bu iki yıl arasında değişiklik gösterir. Veri tanımlama grubu bulunan, şehir alanıyla unconcerned duyuyoruz ve şehir adı ve tasarım zamanında iki tarih biliyoruz. Sonuç olarak, biz tanımlama grubunda depolanan iki popülasyon değerleri yalnızca ilginizi çeken ve kalan değerleri atar olarak işleyebilir.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>Kullanıcı tanımlı türleri ayrıştırma

Olmayan tanımlama grubu türleri için yerleşik destek atar sağlamaz. Ancak, bir sınıf, yapı veya arabirim yazarı, bir veya daha fazla uygulayarak deconstructed için türün örneklerinin izin verebilirsiniz `Deconstruct` yöntemleri. Yöntemin void döndüren ve deconstructed için her bir değeri tarafından belirtilen bir [kullanıma](language-reference/keywords/out-parameter-modifier.md) parametresi yöntem imzası. Örneğin, aşağıdaki `Deconstruct` yöntemi bir `Person` sınıfı, Orta, adı ve Soyadı döndürür:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Ardından örneğini ayrıştırma `Person` adlı sınıfı `p` aşağıdaki gibi bir atama:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Aşağıdaki örnek aşırı `Deconstruct` özelliklerini çeşitli birleşimlerini döndürülecek yöntemi bir `Person` nesne. Tek tek aşırı döndürür:

- İlk ve son adı.
- Bir first, last ve ikinci adı.
- Ad, Soyadı, bir şehir adı ve durum adı.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Aşırı yüklenme olabilir çünkü `Deconstruct` genellikle bir nesneden ayıklandıktan veri grupları yansıtacak şekilde yöntemi tanımlamak dikkatli olmanız gerekir `Deconstruct` ayırt edici ve anlaşılır imzalarla yöntemleri. Birden çok `Deconstruct` aynı sayıda içeren yöntemlerin `out` parametreleri veya aynı numara ve tür `out` farklı bir düzende parametreleri karışıklığa neden olabilir.

Aşırı yüklenen `Deconstruct` yöntemi aşağıdaki örnekte bir olası kaynak karışıklık göstermektedir. İlk aşırı yükleme ilk adını, ikinci adı, Soyadı ve yaş döndürür bir `Person` o sırada bir nesne. İkinci aşırı yükleme yalnızca yıllık gelir yanı sıra ad bilgilerini döndürür, ancak farklı bir sırada, Orta, adı ve Soyadı olan. Bu, ayrıştırma, bağımsız değişkenlerin sırası karıştırılabilir kolaylaştırır bir `Person` örneği.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Kullanıcı tanımlı bir tür ile ayrıştırma atar

Yaptığınız gibi [diziler](#deconstructing-tuple-elements-with-discards), iptali seçilen öğeleri tarafından döndürülen yoksaymak için kullanabileceğiniz bir `Deconstruct` yöntemi. Her atma adlı bir değişkeni tarafından tanımlanan "\_", tek bir ayrıştırma işlemi birden çok atar içerebilir.

Aşağıdaki örnek deconstructs bir `Person` dört dizelere (ilk ve son adları, şehir ve durumu) nesne ancak son adını ve durumunu atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Kullanıcı tanımlı bir tür bir uzantı yönteminiz ayrıştırma

Bir sınıf, yapı veya arabirim yaramadı yazarsanız, yine de bu tür nesneleri bir veya daha fazla uygulayarak Ayrıştır `Deconstruct` [genişletme yöntemleri](programming-guide/classes-and-structs/extension-methods.md) içinde ilginizi değer döndürmek için.

Aşağıdaki örnek iki tanımlar `Deconstruct` için genişletme yöntemleri <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> sınıfı. İlk özelliğinin türünü statik olup dahil olmak üzere özellikleri belirtin veya örnek değerleri, salt okunur olup ve olup dizine kümesini döndürür. İkinci özelliğin erişilebilirlik gösterir. Çünkü erişilebilirliği get ve set erişimcileri gösterebileceğini, Boole değerleri göstermek özelliği ayrı olup get ve set erişimcileri ve bunların aynı erişilebilirliği sahip olup olmadığını, varsa. Yalnızca bir erişimci veya aynı erişilebilirlik, hem get hem de ayarlama erişimcisine sahip `access` değişkeni özelliğinin erişilebilirliğini bir bütün olarak gösterir. Aksi takdirde, Erişilebilirlik get ve set erişimcileri accessaccessibility tarafından belirtilen tarafından belirtilen `getAccess` ve `setAccess` değişkenleri.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Atılanlar](discards.md)
- [Demetler](tuples.md)  
