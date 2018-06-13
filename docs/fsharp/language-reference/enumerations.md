---
title: Numaralandırmalar (F#)
description: 'F # numaralandırmalar değişmez değerler yerine kodunuzu daha okunabilir ve korunabilir hale getirmek için nasıl kullanılacağını öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 00faf6e2ad08a7b232a8ae35aa0f7deb1ba3e76a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562998"
---
# <a name="enumerations"></a>Numaralandırmalar

*Numaralandırmalar*, olarak da bilinen *numaralandırmaları*,, burada etiketleri atanır değerleri alt ağını için tam sayı türleridir. Kodunu daha okunabilir ve sürdürülebilir hale değişmez değerler yerine bunları kullanabilirsiniz.


## <a name="syntax"></a>Sözdizimi

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Açıklamalar
Değerlerin belirtilen dışında numaralandırma basit değerlere sahip ayrılmış bir birleşim benzer görünüyor. Genellikle 0 veya 1 Başlat tamsayılar veya bit konumlarını temsil eden tamsayılar değerlerdir. Bit konumlarını temsil etmek için bir numaralandırma amaçlıyorsanız da kullanmalısınız [bayrakları](xref:System.FlagsAttribute) özniteliği.

Örneğin, bir sonek ile değişmez değerleri gibi kullanabilirsiniz böylece numaralandırması temel alınan türü kullanılan sabit değer belirlenir `1u`, `2u`ve benzeri bir işaretsiz tamsayı (`uint32`) yazın.

Adlandırılmış değerler başvurduğunuzda numaralandırma türünün adı bir niteleyici başka bir deyişle, kullanmalısınız `enum-name.value1`, yalnızca `value1`. Bu davranış, ayrılmış birleşimler farklıdır. Numaralandırmalar her zaman sahip olmasıdır [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliği.

Aşağıdaki kod, bildirimler ve numaralandırma kullanımını gösterir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Kolayca numaralandırmalar için temel alınan tür uygun işlecini kullanarak aşağıdaki kodda gösterildiği gibi dönüştürebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Numaralandırılmış türler aşağıdaki temel türlerinden biri olabilir: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, ve `char`. Numaralandırma türleri .NET Framework olarak temsil kaynağından devralındı türleri `System.Enum`, sırayla devralınır `System.ValueType`. Bu nedenle, yığın veya satır içeren nesne içinde bulunan değer türleri oldukları ve temel alınan türü herhangi bir değer geçerli bir numaralandırma değeridir. Desen eşleştirme sabit değerleri değiştiğinde adlandırılmamış değerleri yakalayan bir desen sağlamak zorunda olduğu için bu önemlidir.

`enum` İşlevi F # Kitaplığı'nda bir numaralandırma değeri, daha önceden tanımlanmış, biri dışında bir değer üretmek için kullanılabilir değerleri adlı. Kullandığınız `enum` gibi işlev.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Varsayılan `enum` işlevi çalışır türüyle `int32`. Bu nedenle, temel alınan diğer türlerine sahip Numaralandırma türleri ile kullanılamaz. Bunun yerine, aşağıdaki kullanın.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)
