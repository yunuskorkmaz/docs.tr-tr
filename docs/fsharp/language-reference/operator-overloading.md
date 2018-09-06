---
title: İşleç Aşırı Yüklemesi (F#)
description: 'Aritmetik işleçler bir sınıf ya da kayıt türü ve F # içinde genel düzeyde aşırı yükleme hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 6232ebf215289e6a22b9d77fbd5fa67b82460486
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798745"
---
# <a name="operator-overloading"></a>İşleç Aşırı Yüklemesi

Bu konu, bir sınıf ya da kayıt türü ve genel düzeyde aritmetik işleçler aşırı açıklar.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *operatör sembolünü* biri `+`, `-`, `*`, `/`, `=`ve benzeri. *Parametre-listesi* işlenenler sırada operatörü için her zamanki sözdiziminde görüntülendiğini belirtir. *Yöntem gövdesini* sonuç değeri oluşturur.

İşleçler için işleç aşırı yüklemeleri statik olmalıdır. İşleç aşırı birli işleçler için gibi `+` ve `-`, bir tilde kullanmanız gerekir (`~`) içinde *operatör sembolünü* gösterildiği işleci birli işleç ve ikili bir işleç değil, olduğunu belirtmek için Aşağıdaki bildirimi.

```fsharp
static member (~-) (v : Vector)
```

Aşağıdaki kod, yalnızca iki işleçleri olan vector sınıfı göstermektedir biri tek işlenenli eksi işareti, diğeri bir skaler tarafından çarpma için. İşleç skaler ve vektör görünme sırasını bağımsız olarak çalışması gerekir çünkü örnekte, skaler çarpma için iki aşırı yüklemesi gerekir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Yeni işleçleri oluşturma

Tüm standart işleçleri aşırı yükleyebilirler, ancak belirli karakter dizilerinin dışında yeni işleçleri de oluşturabilirsiniz. İşleç karakterler izin `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, ve `~`. `~` Karakter işleci birli hale getirme özel bir anlamı vardır ve işleci karakter dizisinin bir parçası değil. Tüm işleçler birli yapılabilir.

Kullandığınız tam karakter dizisi bağlı olarak, belirli bir öncelik ve ilişkisellik operatörünüze sahip olur. Birleşim sağdan sola veya sağa ya da bırakılabilir ve parantezler olmadan dizisi aynı öncelik düzeyine operatörleri görünür olduğunda kullanılır.

İşleç karakter `.` Örneğin, gibiişleçlerinoluşturmakaynıöncelikvebirleşimsıradançarpmaolaraksahipçarpmakendisürümünütanımlamakistiyorsanız,böyleceönceliği,etkilemez`.*`.

Yalnızca işleçler `?` ve `?<-` ile başlayabilir `?`.

Tüm işleçler, öncelik F #'de gösteren bir tablo bulunabilir [simge ve işleç başvurusu](symbol-and-operator-reference/index.md).

## <a name="overloaded-operator-names"></a>Aşırı yüklenmiş işleç adları

F # derleyicisi bir işleç ifade derlediğinde, işleç için derleyici tarafından oluşturulan bir ada sahip bir yöntem oluşturur. Bu yöntemin Microsoft Ara dilini (MSIL) ve aynı zamanda yansıma ve IntelliSense görünen addır. Normalde bu adları F # kodunda kullanmanız gerekmez.

Standart işleçleri aşağıdaki tabloda gösterilmiştir ve bunlara karşılık gelen adları oluşturulur.

|İşleç|Oluşturulan adı|
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

Burada listelenmeyen işleci karakter diğer birleşimleri işleçleri kullanılabilir ve aşağıdaki tablodan karakterlerin tek tek adlarını birleştirerek oluşur adlara sahip. Örneğin, +! olur `op_PlusBang`.

|İşleç karakter|Ad|
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

## <a name="prefix-and-infix-operators"></a>Önek ve İçtakı işleçleri

*Önek* işleçleri, işleç veya işlev gibi işlenenler önüne yerleştirileceği beklenir. *İnfix* işleçleri arasında iki işlenenden yerleştirilecek beklenir.

Yalnızca bazı işleçlerin önek operatörleri kullanılabilir. Bazı işleçleri her zaman önek operatörleri, diğerleri içtakı veya önek olabilir ve geri kalan her zaman işleçleri infix. Şununla işleçleri `!`, dışında `!=`and işleci `~`, veya yinelenen dizileri`~`, her zaman önek işleçleridir. İşleçler `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, ve `%%` önek işleçleri veya işleçler infix olabilir. Ekleyerek bu işleçlerin önek sürümünü iç sürümünden ayırt bir `~` başında tanımlandığında, bu önek işleci. `~` Yalnızca tanımlandığında işleci kullandığınızda kullanılmaz.

## <a name="example"></a>Örnek

Aşağıdaki kod bir kesir türü uygulamak için işleç aşırı yüklemesi kullanımını gösterir. Bir kesir bir pay ve bir paydası tarafından temsil edilir. İşlev `hcf` kesir azaltmak için kullanılan en yüksek ortak çarpanını belirlemek için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Çıkış:**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Genel düzeyde işleçleri

Genel düzeyde işleçleri de tanımlayabilirsiniz. Aşağıdaki kod bir işleci tanımlar `+?`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

Yukarıdaki kod çıktısı `12`.

Kapsam kuralları için F # yeni tanımlanan işleçleri yerleşik işleçlerine göre öncelikli dikte çünkü bu şekilde normal aritmetik işleçler tanımlayabilirsiniz.

Anahtar sözcüğü `inline` genellikle en iyi şekilde çağıran kodun içine tümleştirilmiştir küçük işlevleri genellikle olan genel işleçli kullanılır. Satır içi yapma işleci işlevleri statik olarak çözümlenmiş genel kod üretmek için statik olarak çözümlenmiş tür parametreleri ile çalışmak bunları sağlar. Daha fazla bilgi için [satır içi işlevleri](functions/inline-functions.md) ve [statik olarak çözümlenmiş tür Parametreleri'nde](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](members/index.md)
