---
title: İşleç Aşırı Yüklemesi
description: "Aritmetik işleçleri bir sınıf veya kayıt türünde ve F # ' da genel düzeyde aşırı yüklemeyi öğrenin."
ms.date: 08/15/2020
ms.openlocfilehash: fb86ceb95101fcc1f157ec9ba17a9d8145b11a91
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557587"
---
# <a name="operator-overloading"></a>İşleç Aşırı Yüklemesi

Bu konu, bir sınıf veya kayıt türünde ve genel düzeyde aritmetik işleçlerin nasıl aşırı yükleneceğini açıklar.

## <a name="syntax"></a>Syntax

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *operator-symbol* ,,,, vb `+` . ' den biridir `-` `*` `/` `=` . *Parametre-listesi* , işlenenleri söz konusu işlecin olağan sözdiziminde göründükleri sırada belirtir. *Yöntem-gövde* , elde edilen değeri oluşturur.

İşleçler için işleç aşırı yüklemelerinin statik olması gerekir. Ve gibi Birli İşleçler için işleç aşırı yüklemeleri, işlecin, `+` `-` `~` aşağıdaki bildirimde gösterildiği gibi bir birli işleç olduğunu ve ikili işleç olduğunu göstermek için *operator-symbol* içinde bir tilde () kullanması gerekir.

```fsharp
static member (~-) (v : Vector)
```

Aşağıdaki kod, biri birli eksi ve bir skalar ile çarpma için olmak üzere yalnızca iki işleçle bir vektör sınıfını gösterir. Örnekte, skalar çarpma için iki aşırı yükleme gerekir, çünkü operatör vektör ve skaler 'in göründüğü sıraya bakılmaksızın çalışır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Yeni Işleçler oluşturma

Tüm standart işleçleri aşırı yükleyebilirsiniz, ancak belirli karakter dizileri dışında yeni işleçler de oluşturabilirsiniz. İzin verilen işleç karakterleri,,,, `!` `%` `&` `*` `+` , `-` , `.` , `/` , `<` , `=` , `>` , `?` , `@` , `^` , `|` , ve `~` . `~`Karakter, bir işleç birli oluşturma ve işleç karakter sırasının bir parçası olmayan özel anlamdadır. Tüm işleçler birli yapılamaz.

Kullandığınız tam karakter dizisine bağlı olarak, operatörünüzün belirli bir önceliği ve ilişkilendirilebilirliği olur. İlişkilendirilebilirlik, sola veya sağdan sola doğru olabilir ve aynı öncelik düzeyindeki operatörler parantez olmadan sırayla gösterildiğinde kullanılır.

İşleç karakteri `.` önceliği etkilemez, örneğin, normal çarpma ile aynı önceliğe ve ilişkilendirilebilirliği olan kendi çarpma sürümünüzü tanımlamak istiyorsanız gibi işleçler oluşturabilirsiniz `.*` .

Yalnızca işleçler `?` ve `?<-` ile başlayabilir `?` .

F # içindeki tüm işleçlerin önceliğini gösteren bir tablo, [sembol ve Işleç başvurusunda](./symbol-and-operator-reference/index.md)bulunabilir.

## <a name="overloaded-operator-names"></a>Aşırı yüklenmiş Işleç adları

F # derleyicisi bir işleç ifadesi derlediğinde, bu işleç için derleyicinin ürettiği bir ada sahip bir yöntem oluşturur. Bu, yöntemi için Microsoft ara dili (MSIL) ve ayrıca yansıma ve IntelliSense içinde görünen addır. Normalde bu adları F # kodunda kullanmanız gerekmez.

Aşağıdaki tabloda, standart işleçler ve bunlara karşılık gelen oluşturulan adlar gösterilmektedir.

|Operatör|Oluşturulan ad|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

`not`Bir sembolik işleç olmadığından F # içindeki işlecin yaymadığını unutmayın `op_Inequality` . Bu, bir Boolean ifadesini geçersiz hale getirir Il 'yi gösteren bir işlevdir.

Burada listelenmeyen işleç karakterlerinin diğer birleşimleri, işleçler olarak kullanılabilir ve aşağıdaki tablodaki tek karakterlerin adlarını birleştirerek oluşturulan adlara sahip olabilir. Örneğin, +! olur `op_PlusBang` .

|İşleç karakteri|Adı|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a>Ön ek ve ınfıx Işleçleri

*Önek* işleçlerinin, bir işlev gibi bir işlenenin veya işlenenlerin önüne yerleştirilmesi beklenmektedir. *Indüzeltilme* işleçlerinin iki işlenen arasına yerleştirilmesi beklenmektedir.

Yalnızca belirli işleçler önek işleçleri olarak kullanılabilir. Bazı işleçler her zaman ön ek işleçleridir, diğerleri geçersiz veya ön ek olabilir ve REST, her zaman geri düzeltilebilirler. ,, `!` `!=` , Ve işleç `~` veya yinelenen dizileri ile başlayan işleçler `~` her zaman önek işleçleridir. ,,,,,, `+` `-` Ve işleçleri `+.` `-.` `&` `&&` `%` `%%` önek işleçleri veya ınfıx işleçleri olabilir. Bu işleçlerin ön ek sürümünü, `~` tanımlandığında önek işlecinin başlangıcına ekleyerek bir ınfıx sürümünden ayırt edersiniz. `~`İşleci kullanıldığında, yalnızca tanımlandığında kullanılmaz.

## <a name="example"></a>Örnek

Aşağıdaki kod, bir kesir türü uygulamak için işleç aşırı yüklemesi kullanımını gösterir. Kesir, pay ve payda ile temsil edilir. İşlevi, `hcf` kesirleri azaltmak için kullanılan en yüksek ortak faktörü belirlemekte kullanılır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Çıktıların**

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Genel düzeyde işleçler

Ayrıca, genel düzeyde işleçler tanımlayabilirsiniz. Aşağıdaki kod bir işleci tanımlar `+?` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

Yukarıdaki kodun çıktısı `12` .

Bu şekilde normal aritmetik işleçleri yeniden tanımlayabilirsiniz çünkü F # için kapsam kuralları, yeni tanımlanan işleçlerin yerleşik işleçlerden öncelikli olduğunu dikte ediyor.

Anahtar sözcüğü `inline` genellikle, çağıran kodla en iyi şekilde tümleşik olan küçük işlevler olan genel işleçlerle kullanılır. İşleç işlevlerini satır içi olarak oluşturmak, statik olarak çözümlenen genel kod üretmek için statik olarak çözümlenen tür parametreleriyle birlikte çalışabilmelerini de sağlar. Daha fazla bilgi için bkz. [satır Içi işlevler](./functions/inline-functions.md) ve [statik olarak çözümlenen tür parametreleri](./generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](./members/index.md)
