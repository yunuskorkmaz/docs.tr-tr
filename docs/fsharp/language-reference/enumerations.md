---
title: "Numaralandırmalar (F#)"
description: "F # numaralandırmalar değişmez değerler yerine kodunuzu daha okunabilir ve korunabilir hale getirmek için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9272bf5a-9a9f-4314-9e34-a3248e5244f5
ms.openlocfilehash: de0273900b707c99e6fb1bcc84e5c2b9ef2bc725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
[F # dili başvurusu](index.md)

[Atama ve dönüştürmeler](casting-and-conversions.md)
