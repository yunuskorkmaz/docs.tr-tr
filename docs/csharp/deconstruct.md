---
title: Demetleri ve diğer türleri ayrıştırma
description: Tuples ve diğer türleri yapısızlaştırılmasını öğrenin.
ms.technology: csharp-fundamentals
ms.date: 11/23/2017
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: d238f6f520653befb1464377094b93e34dde0eca
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463134"
---
# <a name="deconstructing-tuples-and-other-types"></a>Demetleri ve diğer türleri ayrıştırma

Tuple, yöntem çağrısından birden çok değer almak için hafif bir yol sağlar. Ama bir kez tuple almak, onun bireysel unsurları işlemek zorunda. Bunu bir öğe-by-eleman bazında yapmak, aşağıdaki örnekte gösterdiği gibi hantal. Yöntem `QueryCityData` 3-tuple döndürür ve öğelerinin her biri ayrı bir işlemde bir değişkene atanır.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Bir nesneden birden çok alan ve özellik değeri almak da aynı derecede hantal olabilir: bir alan veya özellik değerini bir değişkene üye bazında atamanız gerekir.

C# 7.0 ile başlayarak, bir tuple'dan birden çok öğe alabilir veya tek bir *deconstruct* işleminde bir nesneden birden çok alan, özellik ve hesaplanan değerleri alabilirsiniz. Bir tuple'ı yapısızleştirdiğinizde, öğelerini tek tek değişkenlere atarsınız. Bir nesneyi yapısızleştirdiğinizde, seçili değerleri tek tek değişkenlere atarsınız.

## <a name="deconstructing-a-tuple"></a>Bir tuple deconstructing

C#, tek bir işlemde bir tuple'daki tüm öğeleri çözmenize olanak tanıyan yerleşik destek özelliğine sahiptir. Bir tuple'ı dekonstrükte etmek için kullanılan genel sözdizimi, bir tanesini tanımlamak için sözdizimine benzer: her öğenin bir atama deyiminin sol tarafında parantez içinde atanacak olan değişkenleri içine alabilirsiniz. Örneğin, aşağıdaki deyim dört ayrı değişkene 4-tuple öğeleriatar:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Bir tuple'ı yapısızlandırmanın üç yolu vardır:

- Parantez içindeki her alanın türünü açıkça bildirebilirsiniz. Aşağıdaki örnek, `QueryCityData` yöntem tarafından döndürülen 3-tuple yapısızlaştırılması için bu yaklaşımı kullanır.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- C# her `var` değişkenin türünü çıkarsın diye anahtar sözcüğü kullanabilirsiniz. Anahtar kelimeyi `var` parantezlerin dışına yerlikir. Aşağıdaki örnek, yöntemle döndürülen 3-tuple'ı dekonstrükte ederken tür çıkarımını `QueryCityData` kullanır.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Anahtar kelimeyi `var` parantez içindeki değişken bildirimlerinden herhangi biriyle veya tümüyle tek tek kullanabilirsiniz.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Bu hantal ve tavsiye edilmez.

- Son olarak, tuple'ı zaten bildirilmiş değişkenlere dönüştürebilirsiniz.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Tuple'daki her alan aynı türe sahip olsa bile parantez dışında belirli bir tür belirtemeyeceğiniz unutmayın. Bu, CS8136 derleyici hatası oluşturur, "Dekonstrüksiyon 'var (...)' formu 'var' için belirli bir tür eserinizinverir."

Tuple'ın her öğesini bir değişkene atamanız gerektiğini de unutmayın. Herhangi bir öğeyi atlarsanız, derleyici CS8132 hatası oluşturur, "'x' öğelerinin bir tuple'ını 'y' değişkenlerine dönüştüremez."

Dekonstrüksiyonun sol tarafındaki varolan değişkenlere bildirimleri ve atamaları karıştıramayacağınızı unutmayın. Derleyici CS8184 hatası oluşturur, "bir yapısızlaştırma sol tarafta ki bildirimleri ve ifadeleri karıştıramaz." üyeleri yeni beyan ve varolan değişkenleri içerdiğinde.

## <a name="deconstructing-tuple-elements-with-discards"></a>Tuple elemanlarının atılarak yapısızlaştırılması

Genellikle bir tuple deconstructing, yalnızca bazı öğelerin değerleri ilgileniyorsunuz. C# 7.0 ile başlayarak, yalnızca yazma değişkenleri olan ve değerlerini yoksaymayı seçtiğiniz c#'ın *atılması*desteğinden yararlanabilirsiniz. Bir atama, bir atamadaki alt\_karakter (" ") tarafından belirlenir. İstediğiniz kadar değer atabilirsiniz; hepsi tek bir atlayıp, `_`.

Aşağıdaki örnek, tuples'in atılarak kullanımını göstermektedir. Bu `QueryCityDataForYears` yöntem, bir şehrin adı, alanı, bir yıl, o yıl için şehir nüfusu, ikinci yıl ve ikinci yıl için şehrin nüfusu ile 6-tuple döndürür. Örnek, bu iki yıl arasındaki nüfus değişimini göstermektedir. Tuple'dan elde edilen verilerden şehir alanıyla ilgilenmiyoruz ve şehir adını ve iki tarihi tasarım zamanında biliyoruz. Sonuç olarak, yalnızca tuple'da depolanan iki popülasyon değeriyle ilgileniyoruz ve kalan değerlerini atılarak işleyebiliriz.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Kullanıcı tanımlı türleri deconstructing

C#, tuple olmayan türleri yapılandırmak için yerleşik destek sunmaz. Ancak, bir sınıfın, bir yapının veya arabirimin yazarı olarak, bir veya daha fazla `Deconstruct` yöntem uygulayarak tür örneklerinin deconstructed izin verebilirsiniz. Yöntem geçersiz döndürür ve oluşturulacak her değer yöntem imzasında bir [çıkış](language-reference/keywords/out-parameter-modifier.md) parametresi ile gösterilir. Örneğin, bir `Person` `Deconstruct` sınıfın aşağıdaki yöntemi ilk, orta ve soyadı döndürür:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Daha sonra aşağıdaki gibi bir `Person` atama `p` ile adlı sınıfın bir örneğini deconstruct olabilir:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Aşağıdaki örnek, bir `Deconstruct` `Person` nesnenin çeşitli özelliklerini döndürmek için yöntemi aşırı yükler. Bireysel aşırı yükler geri dönüş:

- Adı ve soyadı.
- Bir ilk, son ve göbek adı.
- Ad, soyad, şehir adı ve eyalet adı.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

`Deconstruct` Yöntemi, genellikle bir nesneden çıkarılan veri gruplarını yansıtmak için aşırı yüklenebildiğinizden, ayırt edici ve açık olan imzalarla yöntemleri tanımlamaya `Deconstruct` dikkat etmelisiniz. Aynı `Deconstruct` sayıda `out` parametreye veya aynı sayıda ve `out` farklı bir sırada parametre türüne sahip birden çok yöntem karışıklığa neden olabilir.

Aşağıdaki örnekte aşırı yüklenen `Deconstruct` yöntem, olası bir karışıklık kaynağını göstermektedir. İlk aşırı yükleme, bir `Person` nesnenin adını, soyadını ve yaşını bu sırada döndürür. İkinci aşırı yükleme ad bilgilerini yalnızca yıllık gelirle birlikte döndürür, ancak ilk, orta ve soyadı farklı bir sıradadır. Bu, bir `Person` örneğin yapısını çözerken bağımsız değişkenlerin sırasını karıştırmayı kolaylaştırır.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Kullanıcı tanımlı bir türü atar ile yapılandırma

[Tuples](#deconstructing-tuple-elements-with-discards)ile yaptığınız gibi, bir `Deconstruct` yöntem tarafından döndürülen seçili öğeleri yok saymak için atar kullanabilirsiniz. Her atfetmek " "\_adlı bir değişkenle tanımlanır ve tek bir yapısızlaştırma işlemi birden çok atamı içerebilir.

Aşağıdaki örnek, bir `Person` nesneyi dört dize (ad ve soyad, şehir ve devlet) olarak belirtir, ancak soyadını ve durumu atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Uzantı yöntemiyle kullanıcı tanımlı bir tür deconstructing

Bir sınıf, yapı veya arabirim yazmadıysanız, ilgilendiğiniz değerleri döndürmek için bir veya daha `Deconstruct` fazla [uzantı yöntemi](programming-guide/classes-and-structs/extension-methods.md) uygulayarak bu tür nesneleri yapısızhale getirebilirsiniz.

Aşağıdaki örnek, `Deconstruct` <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> sınıf için iki uzantı yöntemi tanımlar. İlk, özelliğin türü, statik veya örnek olsun, salt okunur olup olmadığı ve dizine eklenip dizilmediği de dahil olmak üzere özellikleri gösteren bir değer kümesi döndürür. İkincisi, özelliğin erişilebilirliğini gösterir. Get ve Set erişime sahip olan ların erişilebilirliği farklı olabileceğinden, Boolean değerleri özelliğin ayrı get ve set erişime sahip olup olmadığını ve varsa aynı erişilebilirliğe sahip olup olmadıklarını gösterir. Yalnızca bir erişimci varsa veya hem get hem de set erişime `access` sahipse, değişken özelliğin bir bütün olarak erişilebilirliğini gösterir. Aksi takdirde, get ve set erişimci erişilebilirliği `getAccess` ve `setAccess` değişkenler tarafından gösterilir.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Atılanlar](discards.md)
- [Demetler](tuples.md)
