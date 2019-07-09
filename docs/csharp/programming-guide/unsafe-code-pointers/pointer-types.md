---
title: İşaretçi türleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 59846affb1eea5bd9d6a80c623eab5e3aa9db87c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661079"
---
# <a name="pointer-types-c-programming-guide"></a>İşaretçi türleri (C# Programlama Kılavuzu)

Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir. Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Önce belirtilen tür `*` bir işaretçi türü olarak adlandırılır **başvurulan türü**. Aşağıdaki türlerde herhangi bir grup türü olabilir:

- Herhangi bir tamsayı türü: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [bayt](../../language-reference/builtin-types/integral-numeric-types.md), [kısa](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [uzun](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).
- Herhangi bir kayan nokta türü: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [çift](../../language-reference/builtin-types/floating-point-numeric-types.md).
- [char](../../language-reference/keywords/char.md).
- [bool](../../language-reference/keywords/bool.md).
- [ondalık](../../language-reference/builtin-types/floating-point-numeric-types.md).
- Tüm [enum](../../language-reference/keywords/enum.md) türü.
- Herhangi bir işaretçi türü. Bu ifadeler gibi sağlar `void**`.
- Yalnızca yönetilmeyen türlerde alanlar içeren, kullanıcı tarafından tanımlanmış herhangi bir yapı türü.

İşaretçi türleri öğesinden devralmaz [nesne](../../language-reference/keywords/object.md) ve işaretçi türleri arasında dönüştürme işlemi yok var ve `object`. Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez. Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.

Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz. Örneğin:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Bir işaretçi, başvuru veya çok işaret edemez bir [yapı](../../language-reference/keywords/struct.md) bir nesne başvurusu bir işaretçi kendisine işaret ettiği bile çöpten toplanmış olabileceğinden başvurular içeren. Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.

Türündeki işaretçi değişkeninin değerini `myType*` türünde bir değişkenin adresidir `myType`. Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:

|Örnek|Açıklama|
|-------------|-----------------|
|`int* p`|`p` bir tamsayının bir işaretçisidir.|
|`int** p`|`p` bir tamsayı işaretçisi için bir işaretçidir.|
|`int*[] p`|`p` işaretçileri dizisidir tek boyutlu bir dizidir.|
|`char* p`|`p` bir karakterin bir işaretçisidir.|
|`void* p`|`p` Bilinmeyen bir türün bir işaretçisidir.|

İşaretçi yöneltme işleci *, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir. Örneğin, aşağıdaki bildirimi ele alalım:

```csharp
int* myVariable;
```

İfade `*myVariable` gösterir `int` yer alan adreste bulunan değişkeni `myVariable`.

Çeşitli konularda işaretçi örnekleri vardır [fixed Statement](../../language-reference/keywords/fixed-statement.md) ve [işaretçi dönüşümleri](../../programming-guide/unsafe-code-pointers/pointer-conversions.md). Aşağıdaki örnekte `unsafe` anahtar sözcüğü ve `fixed` ifadesi ve bir iç işaretçinin nasıl artırılacağını gösterir.  Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz. Bu örnekler ile derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği ayarlanmış.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Yöneltme işleci türünde bir işaretçiye uygulayamazsınız `void*`. Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.

Bir işaretçi olabilir `null`. Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.

İşaretçilerin yöntemler arasında aktarılmasının tanımlanmamış davranışa neden. Bir yerel değişken için bir işaretçi döndüren bir yöntem düşünün bir `in`, `out`, veya `ref` parametresi veya işlev sonucu olarak. İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.

Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:

|İşleç/Deyim|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|-------------------------|---------|
|`*`|İşaretçi yöneltmesi gerçekleştirir.|
|`->`|Bir yapının bir üyesine bir işaretçi yoluyla erişir.|
|`[]`|Bir işaretçiyi dizine ekler.|
|`&`|Bir değişkenin adresini alır.|
|`++` ve `--`|İşaretçileri artırır ve azaltır.|
|`+` ve `-`|İşaretçi aritmetiği gerçekleştirir.|
|`==`, `!=`, `<`, `>`, `<=`, ve `>=`|İşaretçileri karşılaştırır.|
|[`stackalloc` İşleci](../../language-reference/operators/stackalloc.md)|Yığında bellek ayırır.|
|[`fixed` Deyimi](../../language-reference/keywords/fixed-statement.md)|Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.|

İşaretçi hakkında daha fazla bilgi için bkz: ilgili işleçleri [işaretçi işleçleri ilgili](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [İşaretçi Dönüştürmeler](pointer-conversions.md)
- [Türler](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
