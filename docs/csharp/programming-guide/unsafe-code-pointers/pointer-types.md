---
title: İşaretçi türleri - C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7bbfa6b2238458d3248da830cf9d6ac36551b431
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507041"
---
# <a name="pointer-types-c-programming-guide"></a>İşaretçi türleri (C# Programlama Kılavuzu)

Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir. Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

İşaretçi türünden `*` önce belirtilen türe **başvuru türü**denir. Yalnızca [yönetilmeyen](../../language-reference/builtin-types/unmanaged-types.md) bir tür başvuru türü olabilir.

İşaretçi türleri [nesneden](../../language-reference/builtin-types/reference-types.md) devralmaz ve işaretçi `object`türleri arasında dönüşüm yoktur ve . Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez. Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.

Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz. Örnek:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Bir işaretçi başvuruyu veya başvuru içeren bir [yapıyı](../../language-reference/builtin-types/struct.md) işaret edemez, çünkü bir nesne başvurusu işaret çikarsa bile bir nesne başvurusu çöp olarak toplanabilir. Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.

Tür işaretçi değişkeninin `myType*` değeri, türdeki `myType`bir değişkenin adresidir. Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:

|Örnek|Açıklama|
|-------------|-----------------|
|`int* p`|`p`bir tamsayı için bir işaretçidir.|
|`int** p`|`p`bir tamsayı için işaretçi dir.|
|`int*[] p`|`p`tamsayılar için işaretçilerin tek boyutlu bir dizidir.|
|`char* p`|`p`bir char için bir işaretçidir.|
|`void* p`|`p`bilinmeyen bir türe işaretçidir.|

İşaretçi yöneltme işleci *, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir. Örneğin, aşağıdaki bildirimi ele alalım:

```csharp
int* myVariable;
```

İfade, `*myVariable` `myVariable`'' `int` adresinde bulunan değişkeni gösterir.

Konular [sabit İfade](../../language-reference/keywords/fixed-statement.md) ve [İşaretçi Dönüşümleri](./pointer-conversions.md)işaretçileri birkaç örnek vardır. Aşağıdaki örnekte `unsafe` anahtar kelime `fixed` ve deyim kullanır ve bir iç işaretçi nasıl artış gösterir.  Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz. Bu örnekler [-güvenli olmayan](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği kümesi ile derlenmelidir.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Yön işleci, bir tür `void*`işaretçisine uygulayamazsınız. Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.

Bir işaretçi `null`olabilir. Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.

İşaretçileri yöntemler arasında geçirme, tanımlanmamış davranışlara neden olabilir. Bir işaretçiyi yerel bir değişkene `in`, `out`bir `ref` parametre veya işlev sonucu olarak döndüren bir yöntem düşünün. İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.

Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:

|İşleç/Deyim|Kullanım|
|-------------------------|---------|
|`*`|İşaretçi yöneltmesi gerçekleştirir.|
|`->`|Bir yapının bir üyesine bir işaretçi yoluyla erişir.|
|`[]`|Bir işaretçiyi dizine ekler.|
|`&`|Bir değişkenin adresini alır.|
|`++` ve `--`|İşaretçileri artırır ve azaltır.|
|`+` ve `-`|İşaretçi aritmetiği gerçekleştirir.|
|`==`, `!=` `<`, `>` `<=`, , ve`>=`|İşaretçileri karşılaştırır.|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|Yığında bellek ayırır.|
|[`fixed`Deyim](../../language-reference/keywords/fixed-statement.md)|Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.|

İşaretçi yle ilgili işleçler hakkında daha fazla bilgi için [Işaretçi ile ilgili işleçler'e](../../language-reference/operators/pointer-related-operators.md)bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Pointer türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [İşaretçi Dönüştürmeler](pointer-conversions.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
- [Değer türleri](../../language-reference/builtin-types/value-types.md)
- [Güvenli olmayan](../../language-reference/keywords/unsafe.md)
