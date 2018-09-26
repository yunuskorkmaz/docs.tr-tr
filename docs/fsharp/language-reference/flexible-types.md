---
title: Esnek Türler (F#)
description: 'Bir parametre, değişken veya değer belirtilen bir tür ile uyumlu bir türe sahip olduğunu gösterir F # esnek türü açıklama kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: b6c97c3cc19f15b2c8db74b2c55660a16b2858f7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210051"
---
# <a name="flexible-types"></a>Esnek Türler

A *esnek tür ek açıklamasına* bir parametre, değişken veya değer uyumluluk sınıfları arabirimler ve nesne yönelimli bir hiyerarşideki konuma göre belirlendiği belirtilen bir tür ile uyumlu bir türe sahip olduğunu gösterir. Esnek türler, özellikle otomatik dönüştürme türü hiyerarşinin üst düzeylerindeki türlerine oluşmaz ancak yine de hiyerarşideki herhangi bir türü veya bir arabirimi uygulayan herhangi bir türü ile çalışmak, işlevselliğini etkinleştirmek istediğinizde kullanışlıdır.

## <a name="syntax"></a>Sözdizimi

```fsharp
#type
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *türü* bir taban türü veya bir arabirimi temsil eder.

Esnek bir tür, taban veya arabirim türü ile uyumlu türlere izin verilen türlerden sınırlayan bir kısıtlamaya sahip genel bir tür eşdeğerdir. Diğer bir deyişle, aşağıdaki iki kod satırlarını eşdeğerdir.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Esnek türler, çeşitli türlerde durumlarda, kullanışlıdır. Daha yüksek sıralı işlev (işlev bağımsız değişken olarak alan bir işlev) sahip olduğunuzda, örneğin, genellikle işlev dönüş esnek bir türü sahip olmak yararlı olur. Aşağıdaki örnekte, bir sıra bağımsız değişkeni ile esnek bir türü kullanımını `iterate2` dizileri, diziler, listeler ve numaralandırılabilir herhangi bir türü oluşturan işlevler ile çalışmak daha yüksek sıralı işlev sağlar.

Aşağıdaki iki işlevi, bir dizisini döndüren biri diğerinin esnek bir tür döndüren bir göz önünde bulundurun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Başka bir örnek olarak göz önünde bulundurun [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) kitaplığı işlevi:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Bu işleve aşağıdaki numaralandırılabilir sıralarının geçirebilirsiniz:

- Bir liste
- Bir diziler listesi
- Bir dizi listeler
- Bir dizi sırası
- Herhangi bir birleşimini numaralandırılabilir sırası

Aşağıdaki kod `Seq.concat` esnek türlerini kullanarak destekleyebilir senaryoları göstermek için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Çıktı aşağıdaki gibidir:

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

F # nesne yönelimli diğer dillerde olduğu gibi var. türetilmiş türler veya arabirimlerini uygulayan türler otomatik olarak bir taban türü veya arabirim türü dönüştürüldüğü bağlamları Otomatik dönüştürmeler doğrudan bağımsız, ancak türü bir işlev türünün bir dönüş türü gibi daha karmaşık bir türün bir parçası olarak ya da bir tür bağımsız değişkeni olarak bir alt konumda olmadığında oluşur. Bu nedenle, kendisine uyguladığınızı türü daha karmaşık bir türün bir parçası olduğunda esnek türü gösterimi özellikle yararlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Genel Türler](generics/index.md)
