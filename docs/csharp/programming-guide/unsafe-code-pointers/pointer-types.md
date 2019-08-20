---
title: İşaretçi türleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 4d0801cd81e00c84be278b44730058798b0acfa9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588194"
---
# <a name="pointer-types-c-programming-guide"></a>İşaretçi türleri (C# Programlama Kılavuzu)

Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir. Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Bir işaretçi türündeki öğesinden önce `*` belirtilen tür, **başvurulan tür**olarak adlandırılır. Yalnızca [yönetilmeyen bir tür](../../language-reference/builtin-types/unmanaged-types.md) , başvurulan bir tür olabilir.

İşaretçi türleri [nesneden](../../language-reference/keywords/object.md) aktarılmaz ve işaretçi türleri ve `object`arasında dönüştürme yok. Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez. Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.

Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz. Örneğin:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Bir işaretçi, bir işaretçiye işaret eden bir nesne başvurusu atık olarak toplanabileceğinden, bir başvuruya veya başvuru içeren bir [yapıya](../../language-reference/keywords/struct.md) işaret edemez. Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.

Türündeki `myType*` işaretçi değişkeninin değeri, türünde `myType`bir değişkenin adresidir. Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:

|Örnek|Açıklama|
|-------------|-----------------|
|`int* p`|`p`bir tamsayıya yönelik bir işaretçidir.|
|`int** p`|`p`, tamsayıya yönelik işaretçinin bir işaretçisidir.|
|`int*[] p`|`p`, tamsayılara yönelik işaretçilerin tek boyutlu bir dizisidir.|
|`char* p`|`p`, Char için bir işaretçidir.|
|`void* p`|`p`, bilinmeyen bir türe yönelik bir işaretçidir.|

İşaretçi yöneltme işleci *, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir. Örneğin, aşağıdaki bildirimi ele alalım:

```csharp
int* myVariable;
```

İfade `*myVariable` , `int` içinde`myVariable`bulunan adreste bulunan değişkeni gösterir.

Konular [Sabit bildiriminde](../../language-reference/keywords/fixed-statement.md) ve [işaretçi dönüştürmelerinde birçok işaretçiye](./pointer-conversions.md)örnek vardır. Aşağıdaki örnek, `unsafe` anahtar sözcüğünü `fixed` ve ifadesini kullanır ve iç işaretçinin nasıl artırılacağını gösterir.  Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz. Bu örneklerin [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçenek kümesiyle derlenmesi gerekir.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Yöneltme işlecini türündeki `void*`bir işaretçiye uygulayamazsınız. Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.

Bir işaretçi `null`olabilir. Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.

Yöntemler arasında işaretçiler geçirmek tanımsız davranışlara neden olabilir. Bir `in`, `out`veya parametresiyadaişlevsonucuolarakyerelbirdeğişkenebirişaretçidöndürenbiryöntemdüşünün.`ref` İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.

Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:

|İşleç/Deyim|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|-------------------------|---------|
|`*`|İşaretçi yöneltmesi gerçekleştirir.|
|`->`|Bir yapının bir üyesine bir işaretçi yoluyla erişir.|
|`[]`|Bir işaretçiyi dizine ekler.|
|`&`|Bir değişkenin adresini alır.|
|`++` ve `--`|İşaretçileri artırır ve azaltır.|
|`+` ve `-`|İşaretçi aritmetiği gerçekleştirir.|
|`==`, `!=` ,`<`, ,ve`>` `<=``>=`|İşaretçileri karşılaştırır.|
|[`stackalloc`işlecinde](../../language-reference/operators/stackalloc.md)|Yığında bellek ayırır.|
|[`fixed`Ekstre](../../language-reference/keywords/fixed-statement.md)|Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.|

İşaretçi ile ilgili işleçler hakkında daha fazla bilgi için bkz. [işaretçi ile ilgili işleçler](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [İşaretçi Dönüştürmeler](pointer-conversions.md)
- [Türler](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
