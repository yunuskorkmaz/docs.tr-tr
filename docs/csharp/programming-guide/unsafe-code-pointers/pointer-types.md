---
title: İşaretçi türleri-C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 492b37460c05ffbc82e020facb354be22706f8d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396265"
---
# <a name="pointer-types-c-programming-guide"></a>İşaretçi türleri (C# Programlama Kılavuzu)

Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir. Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

`*`Bir işaretçi türündeki öğesinden önce belirtilen tür, **başvurulan tür**olarak adlandırılır. Yalnızca [yönetilmeyen bir tür](../../language-reference/builtin-types/unmanaged-types.md) , başvurulan bir tür olabilir.

İşaretçi türleri [nesneden](../../language-reference/builtin-types/reference-types.md) aktarılmaz ve işaretçi türleri ve arasında dönüştürme yok `object` . Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez. Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.

Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz. Örnek:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Bir işaretçi, bir işaretçiye işaret eden bir nesne başvurusu atık olarak toplanabileceğinden, bir başvuruya veya başvuru içeren bir [yapıya](../../language-reference/builtin-types/struct.md) işaret edemez. Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.

Türündeki işaretçi değişkeninin değeri, `myType*` türünde bir değişkenin adresidir `myType` . Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:

|Örnek|Description|
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

İfade, `*myVariable` içinde bulunan `int` adreste bulunan değişkeni gösterir `myVariable` .

Konular [Sabit bildiriminde](../../language-reference/keywords/fixed-statement.md) ve [işaretçi dönüştürmelerinde birçok işaretçiye](./pointer-conversions.md)örnek vardır. Aşağıdaki örnek, `unsafe` anahtar sözcüğünü ve ifadesini kullanır `fixed` ve iç işaretçinin nasıl artırılacağını gösterir.  Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz. Bu örneklerin [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçenek kümesiyle derlenmesi gerekir.

[!code-csharp[Using pointer types](snippets/FixedKeywordExamples.cs#5)]

Yöneltme işlecini türündeki bir işaretçiye uygulayamazsınız `void*` . Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.

Bir işaretçi olabilir `null` . Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.

Yöntemler arasında işaretçiler geçirmek tanımsız davranışlara neden olabilir. Bir `in` , `out` veya `ref` parametresi ya da işlev sonucu olarak yerel bir değişkene bir işaretçi döndüren bir yöntem düşünün. İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.

Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:

|İşleç/Deyim|Kullanım|
|-------------------------|---------|
|`*`|İşaretçi yöneltmesi gerçekleştirir.|
|`->`|Bir yapının bir üyesine bir işaretçi yoluyla erişir.|
|`[]`|Bir işaretçiyi dizine ekler.|
|`&`|Bir değişkenin adresini alır.|
|`++` ve `--`|İşaretçileri artırır ve azaltır.|
|`+` ve `-`|İşaretçi aritmetiği gerçekleştirir.|
|`==`, `!=` , `<` , `>` , `<=` ve`>=`|İşaretçileri karşılaştırır.|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|Yığında bellek ayırır.|
|[`fixed`Ekstre](../../language-reference/keywords/fixed-statement.md)|Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.|

İşaretçi ile ilgili işleçler hakkında daha fazla bilgi için bkz. [işaretçi ile ilgili işleçler](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [İşaretçi dönüştürmeleri](pointer-conversions.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
- [Değer türleri](../../language-reference/builtin-types/value-types.md)
- [olmayabilecek](../../language-reference/keywords/unsafe.md)
