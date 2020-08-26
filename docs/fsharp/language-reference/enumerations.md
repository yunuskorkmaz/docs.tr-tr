---
title: Listelemeler
description: 'Kodunuzun daha okunabilir ve sürdürülebilir olmasını sağlamak için sabit değer yerine F # numaralandırmaları nasıl kullanacağınızı öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812113"
---
# <a name="enumerations"></a>Listelemeler

*Numaralandırmalar*olarak da bilinen *numaralandırmalar*, etiketlerin değerlerinin bir alt kümesine atandığı integral türleridir. Kodu daha okunaklı ve bakım yapılabilir hale getirmek için bunları değişmez değerler yerine kullanabilirsiniz.

## <a name="syntax"></a>Syntax

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Açıklamalar

Bir numaralandırma, değerlerin belirtilemesi dışında basit değerleri olan ayrılmış bir birleşime benzer şekilde görünür. Değerler genellikle 0 veya 1 ' den başlayan tamsayılar veya bit konumlarını temsil eden tamsayılardır. Bir numaralandırma, bit konumlarını temsil etmek için tasarlanıyorsa, [Flags](xref:System.FlagsAttribute) özniteliğini de kullanmalısınız.

Sabit listesinin temel alınan türü, kullanılan değişmez değere göre belirlenir, böylece örneğin, bir `1u` `2u` işaretsiz tamsayı () türü için,, ve gibi bir soneke sahip değişmez değerler kullanabilirsiniz `uint32` .

Adlandırılmış değerlere başvurduğunuzda, sabit listesi türünün adını bir niteleyici olarak kullanmanız gerekir, yani, `enum-name.value1` yalnızca değil `value1` . Bu davranış, ayrılmış birleşimlerden farklıdır. Bunun nedeni, Numaralandırmaların her zaman [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) özniteliğine sahip olmasından kaynaklanır.

Aşağıdaki kod, bir numaralandırmanın bildirimini ve kullanımını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Aşağıdaki kodda gösterildiği gibi, uygun işleci kullanarak numaralandırmaları kolayca temel alınan türe dönüştürebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Numaralandırılmış türler aşağıdaki temel türlerden birine sahip olabilir: `sbyte` ,,, `byte` `int16` `uint16` , `int32` , `uint32` , `int64` , `uint16` , `uint64` ve `char` . Sabit listesi türleri, ' den devralınan türler olarak .NET Framework temsil edilir `System.Enum` ve bundan sonra öğesinden devralınır `System.ValueType` . Bu nedenle, yığın üzerinde bulunan veya kapsayan nesnede satır içi olan değer türlerdir ve temel alınan türün herhangi bir değeri numaralandırmanın geçerli bir değeridir. Bu, adlandırılmamış değerleri yakalayan bir model sağlamanız gerektiğinden, numaralandırma değerleri üzerinde kalıp eşleştirilirken önemlidir.

`enum`F # kitaplığındaki işlev, önceden tanımlanmış adlandırılmış değerlerden biri dışında bir değer olan bir sabit listesi değeri oluşturmak için kullanılabilir. `enum`İşlevini aşağıdaki şekilde kullanırsınız.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Varsayılan `enum` işlev, türüyle çalışır `int32` . Bu nedenle, diğer temel türlerine sahip sabit listesi türleriyle kullanılamaz. Bunun yerine, aşağıdakileri kullanın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

Ayrıca, numaralandırmalar için durumlar her zaman olarak yayılır `public` . Bu, C# ve .NET platformunun geri kalanı ile hizalanır.

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Atama ve Dönüştürmeler](casting-and-conversions.md)
