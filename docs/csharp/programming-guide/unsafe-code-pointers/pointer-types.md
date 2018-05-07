---
title: İşaretçi türleri (C# Programlama Kılavuzu)
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: cbc75a2ec6fe826cb192b1e8bef61c7295f13916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pointer-types-c-programming-guide"></a>İşaretçi türleri (C# Programlama Kılavuzu)

Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir. Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Önce belirtilen tür `*` bir işaretçi türü olarak adlandırılır **referrent türü**. Şu türlerden birini referrent türü olabilir:

- Herhangi bir tam sayı türü: [sbyte](../../language-reference/keywords/sbyte.md), [bayt](../../language-reference/keywords/byte.md), [kısa](../../language-reference/keywords/short.md), [ushort](../../language-reference/keywords/ushort.md), [int](../../language-reference/keywords/int.md), [uint](../../language-reference/keywords/uint.md), [uzun](../../language-reference/keywords/long.md), [ulong](../../language-reference/keywords/ulong.md).
- Herhangi bir kayan nokta türü: [float](../../language-reference/keywords/float.md), [çift](../../language-reference/keywords/double.md).
- [char](../../language-reference/keywords/char.md).
- [bool](../../language-reference/keywords/bool.md).
- [ondalık](../../language-reference/keywords/decimal.md).
- Tüm [enum](../../language-reference/keywords/enum.md) türü.
- Herhangi bir işaretçi türü. Bu ifadeler gibi sağlar `void**`.
- Yalnızca yönetilmeyen türlerde alanlar içeren, kullanıcı tarafından tanımlanmış herhangi bir yapı türü.

İşaretçi türleri devralmaz gelen [nesne](../../language-reference/keywords/object.md) ve işaretçi türleri arasında hiçbir dönüşümleri var ve `object`. Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez. Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.

Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz. Örneğin:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Bir işaretçi bir başvuru ya da çok işaret edemez bir [yapısı](../../language-reference/keywords/struct.md) nesne başvurusu bir işaretçi işaret olsa bile toplanacak olabileceğinden başvuruları içeren. Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.

Tür işaretçi değişkeninin değerini `myType*` türünde bir değişken adresidir `myType`. Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:

|Örnek|Açıklama|
|-------------|-----------------|
|`int* p`|`p` tamsayıya bir işaretçidir.|
|`int** p`|`p` tamsayı gösteren bir işaretçi bir işaretçi var.|
|`int*[] p`|`p` bir tek boyutlu tamsayı işaretçiler dizisidir.|
|`char* p`|`p` bir karakter için bir işaretçidir.|
|`void* p`|`p` Bilinmeyen bir tür için bir işaretçidir.|

İşaretçi yöneltme işleci *, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir. Örneğin, aşağıdaki bildirimi ele alalım:

```csharp
int* myVariable;
```

İfade `*myVariable` gösterir `int` içinde yer alan adresinde bulunan değişkeni `myVariable`.

Bazı işaretçiler konulardaki örnekleri vardır [deyimi sabit](../../language-reference/keywords/fixed-statement.md) ve [işaretçi dönüşümleri](../../programming-guide/unsafe-code-pointers/pointer-conversions.md). Aşağıdaki örnek kullanır `unsafe` anahtar sözcüğü ve `fixed` deyimi ve iç işaretçi Artır gösterilmektedir.  Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz. Bu örnekler ile derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği ayarlanmış.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

İndirection işleci gösteren bir işaretçi türü uygulanamıyor `void*`. Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.

Bir işaretçi olabilir `null`. Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.

İşaretçileri yöntemleri arasında geçirme tanımsız davranışa neden olabilir. Yerel bir değişken için bir işaretçi döndüren bir yöntem göz önünde bulundurun bir `in`, `out`, veya `ref` parametresi ya da işlevin sonucu olarak. İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.

Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:

|İşleç/Deyim|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|-------------------------|---------|
|*|İşaretçi yöneltmesi gerçekleştirir.|
|->|Bir yapının bir üyesine bir işaretçi yoluyla erişir.|
|[]|Bir işaretçiyi dizine ekler.|
|`&`|Bir değişkenin adresini alır.|
|++ ve --|İşaretçileri artırır ve azaltır.|
|+ ve -|İşaretçi aritmetiği gerçekleştirir.|
|==,! =, \<, >, \<= ve > =|İşaretçileri karşılaştırır.|
|`stackalloc`|Yığında bellek ayırır.|
|`fixed` Deyimi|Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.|

## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.
 [C# Programlama Kılavuzu](../index.md)  
 [Güvenli Olmayan Kod ve İşaretçiler](index.md)  
 [İşaretçi Dönüştürmeler](pointer-conversions.md)  
 [İşaretçi İfadeleri](pointer-expressions.md)  
 [Türler](../../language-reference/keywords/types.md)  
 [unsafe](../../language-reference/keywords/unsafe.md)  
 [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../language-reference/keywords/stackalloc.md)  
 [Kutulama ve Kutudan Çıkarma](../types/boxing-and-unboxing.md)
