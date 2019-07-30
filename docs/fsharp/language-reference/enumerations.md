---
title: Numaralandırmalar
description: Kodunuzun daha okunabilir ve F# sürdürülebilir olmasını sağlamak için sabit değerlerin yerine Numaralandırmaların nasıl kullanılacağını öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630343"
---
# <a name="enumerations"></a>Numaralandırmalar

Numaralandırmalar olarak da bilinen *numaralandırmalar*, etiketlerin değerlerinin bir alt kümesine atandığı integral türleridir. Kodu daha okunaklı ve bakım yapılabilir hale getirmek için bunları değişmez değerler yerine kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Açıklamalar

Bir numaralandırma, değerlerin belirtilemesi dışında basit değerleri olan ayrılmış bir birleşime benzer şekilde görünür. Değerler genellikle 0 veya 1 ' den başlayan tamsayılar veya bit konumlarını temsil eden tamsayılardır. Bir numaralandırma, bit konumlarını temsil etmek için tasarlanıyorsa, [Flags](xref:System.FlagsAttribute) özniteliğini de kullanmalısınız.

Sabit listesinin temel alınan türü, kullanılan değişmez değere göre belirlenir, böylece örneğin, bir işaretsiz tamsayı ( `1u``uint32`) türü için,, ve gibi bir soneke `2u`sahip değişmez değerler kullanabilirsiniz.

Adlandırılmış değerlere başvurduğunuzda, sabit listesi türünün adını bir niteleyici olarak kullanmanız gerekir, yani `enum-name.value1`, yalnızca `value1`değil. Bu davranış, ayrılmış birleşimlerden farklıdır. Bunun nedeni, Numaralandırmaların her zaman [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) özniteliğine sahip olmasından kaynaklanır.

Aşağıdaki kod, bir numaralandırmanın bildirimini ve kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Aşağıdaki kodda gösterildiği gibi, uygun işleci kullanarak numaralandırmaları kolayca temel alınan türe dönüştürebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Numaralandırılmış türler aşağıdaki `sbyte`temel türlerden birine sahip olabilir:, `int64` `int32` `uint16` `byte`, `int16`,,, `uint32`,, `uint16`, `uint64`ve. `char` Sabit listesi türleri, ' den devralınan türler `System.Enum`olarak .NET Framework temsil edilir ve bundan sonra öğesinden `System.ValueType`devralınır. Bu nedenle, yığın üzerinde bulunan veya kapsayan nesnede satır içi olan değer türlerdir ve temel alınan türün herhangi bir değeri numaralandırmanın geçerli bir değeridir. Bu, adlandırılmamış değerleri yakalayan bir model sağlamanız gerektiğinden, numaralandırma değerleri üzerinde kalıp eşleştirilirken önemlidir.

F# Kitaplığındaki işlev, önceden tanımlanmış adlandırılmış değerlerden biri dışında bir değer olan bir sabit listesi değeri oluşturmak için `enum` kullanılabilir. `enum` İşlevini aşağıdaki şekilde kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Varsayılan `enum` işlev, türüyle `int32`çalışır. Bu nedenle, diğer temel türlerine sahip sabit listesi türleriyle kullanılamaz. Bunun yerine, aşağıdakileri kullanın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

Ayrıca, numaralandırmalar için durumlar her zaman olarak `public`yayılır. Bu sayede, ve .NET platformunun geri C# kalanı ile hizalanır.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)
