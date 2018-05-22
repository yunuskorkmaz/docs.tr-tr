---
title: İşleç Aşırı Yüklemesi (F#)
description: 'Aritmetik işleçler bir sınıf veya kayıt türü ve F # içinde genel düzeyde aşırı yüklemeyi öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: fc9b7311aa746fd758930365972a187ffdfff0d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="operator-overloading"></a>İşleç Aşırı Yüklemesi

Bu konuda, bir sınıf ya da kayıt türü ve genel düzeyde aritmetik işleçler aşırı yüklemeyi açıklar.


## <a name="syntax"></a>Sözdizimi

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a>Açıklamalar
Önceki sözdiziminde *işleç simgesi* biri `+`, `-`, `*`, `/`, `=`ve benzeri. *Parametre listesi* işlenenler göründükleri normal sözdiziminde işleç için sıra belirtir. *Yöntem gövdesi* sonuç değeri oluşturur.

İşleç aşırı yüklemeleri işleçleri için statik olmalıdır. İşleci birli işleçler için gibi aşırı yüklemeler `+` ve `-`, bir tilde kullanmanız gerekir (`~`) içinde *işleç simgesi* işleci birli işleç ve ikili işleç değil de gösterildiği gibi olduğunu göstermek için Aşağıdaki bildirimi.

```fsharp
static member (~-) (v : Vector)
```

Aşağıdaki kod yalnızca iki işleç olan bir vektör sınıfı gösterir tekli eksi, diğeri skaler tarafından çarpma için için. İşleç vektör ve skaler görünme sırasını bağımsız olarak çalışması gerekir çünkü örnekte, iki aşırı skaler çarpma için gereklidir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a>Yeni işleçleri oluşturma
Tüm standart işleçleri aşırı yüklenebilir, ancak belirli karakter dizileri dışında yeni işleçleri de oluşturabilirsiniz. İşleç karakterler izin `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, ve `~`. `~` Karakter işleci birli yapma özel bir anlamı yoktur ve işleci karakter dizisinin bir parçası değil. Tüm işleçleri birli yapılabilir.

Kullandığınız tam karakter dizisi bağlı olarak, belirli bir öncelik ve birleşim operatörünüze sahip olur. Birleşim sağdan sola veya sağa ya da bırakılabilir ve parantezler olmadan sırası aynı öncelik düzeyine operatörleri görünür olduğunda kullanılır.

İşleç karakter `.` Örneğin, gibiişleçlerinoluşturmakaynıöncelikvebirleşimsıradançarpmaolaraksahipçarpmakendisürümünütanımlamakistiyorsanız,böyleceönceliği,etkilemez `.*`.

Yalnızca işleçleri `?` ve `?<-` ile başlayabilir `?`.

Tüm işleçleri önceliğini F #'ta gösteren bir tablo bulunabilir [simge ve işleç başvurusu](symbol-and-operator-reference/index.md).


## <a name="overloaded-operator-names"></a>Aşırı yüklenmiş işleci adları
F # derleyici işleci ifade derlediğinde işleç için derleyici tarafından üretilen bir ada sahip bir yöntem oluşturur. Bu yöntem için Microsoft Ara dilde (MSIL) ve yansıma ve IntelliSense görünen addır. Normalde bu adları F # kodunda kullanmanız gerekmez.

Aşağıdaki tablo standart işleçler gösterir ve karşılık gelen adları oluşturulur.



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
Burada listelenmeyen işleci karakterden diğer bileşimlerini işletmenler olarak kullanılabilir ve aşağıdaki tablodan tek tek karakter adları birleştirerek oluşur adlara sahip. Örneğin, +! hale `op_PlusBang`.



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

## <a name="prefix-and-infix-operators"></a>Önek ve iç işleçleri
*Önek* işleçleri işleneni veya benzer bir işlev işlenenler önünde yerleştirilmesi beklenir. *İnfix* işleçleri arasında iki işlenen yerleştirilmesi beklenir.

Yalnızca belirli işleçleri önek operatörleri kullanılabilir. Bazı işleçler her önek operatörleri, diğerleri iç veya önek olabilir ve geri kalan her zaman işleçleri infix. İle başlayan işleçleri `!`, dışında `!=`and işleci `~`, veya yinelenen dizilerini`~`, her zaman önek işleçler şunlardır. İşleçler `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, ve `%%` önek işleçleri veya işleçleri infix olabilir. Bu işleçlere önek sürümü ekleyerek iç sürümünden ayırt bir `~` çok tanımlandığında bir önek işleci başındaki. `~` Yalnızca tanımlandığında işleci kullandığınızda kullanılmaz.

## <a name="example"></a>Örnek

Aşağıdaki kod bir kesir türü uygulamak için işleç aşırı yüklemesi kullanımını gösterir. Kesir bir pay ve bir paydası tarafından temsil edilir. İşlev `hcf` kesirler azaltmak için kullanılan en yüksek ortak çarpanını belirlemek için kullanılır.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

**Çıktı:**

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a>Genel düzeyde işleçleri
Genel düzeyde işleçleri tanımlayabilir. Aşağıdaki kod bir işleç tanımlar `+?`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

Yukarıdaki kod çıkışıdır `12`.

Kapsam kuralları F # için yeni tanımlanan işleçleri yerleşik işleçleri önceliklidir dikte çünkü bu şekilde normal aritmetik işleçler tanımlayabilirsiniz.

Anahtar sözcüğü `inline` çoğunlukla genellikle en iyi arama koda tümleşik küçük işlevlerdir genel işleçleri ile kullanılır. Yapma işleci işlevler satır içi bunları statik olarak çözümlenmiş genel kod üretmek için statik olarak çözümlenmiş tür parametreleri ile çalışmak etkinleştirir. Daha fazla bilgi için bkz: [satır içi işlevler](functions/inline-functions.md) ve [statik olarak çözümlenmiş tür parametreleri](generics/statically-resolved-type-parameters.md).

## <a name="see-also"></a>Ayrıca Bkz.
[Üyeler](members/index.md)
