---
title: Esnek Türler (F#)
description: 'Bir parametre, değişken veya değer belirtilen tür ile uyumlu bir türe sahip olduğunu gösterir F # esnek türü açıklama kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: a54d462d04e4e65680a4612f58da72173f04d1f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563356"
---
# <a name="flexible-types"></a>Esnek Türler

A *esnek türü ek açıklama* bir parametre, değişken veya değer uyumluluk sınıfların veya arabirimleri nesne yönelimli bir hiyerarşinin konuma göre belirlendiği belirtilen bir tür ile uyumlu bir türü olduğunu gösterir. Esnek türler, özellikle türleri tür hiyerarşisinde daha yüksek otomatik dönüştürme oluşmaz ancak hala hiyerarşideki herhangi bir tür veya bir arabirimini uygulayan herhangi bir türü ile çalışmak, işlevselliğini etkinleştirmek istediğinizde faydalıdır.

## <a name="syntax"></a>Sözdizimi

```fsharp
#type
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *türü* bir taban türü veya bir arabirimi temsil eder.

Esnek bir türü, temel veya arabirim türü ile uyumlu türleri için izin verilen türleri sınırlayan bir kısıtlamaya sahip genel bir tür eşdeğerdir. Diğer bir deyişle, aşağıdaki iki kod satırı eşdeğerdir.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Esnek türler çeşitli türlerde durumlarda, yararlı olur. Daha yüksek bir sipariş işlevi (işlev bağımsız değişken olarak alan işlevi) varsa, örneğin, genellikle bir esnek türü dönüş işlevi yararlı olacaktır. Aşağıdaki örnekte, bir sıra bağımsız değişkeni bir esnek türüyle kullanımını `iterate2` sıraları, diziler, listeler ve herhangi bir numaralandırma türü oluşturan işlevler ile çalışmak daha yüksek sipariş işlevini etkinleştirir.

Aşağıdaki iki işlevleri, bir sıralı bir hangi verir, biri diğer esnek bir tür döndüren göz önünde bulundurun.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Başka bir örnek olarak, göz önünde bulundurun [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) kitaplığı işlevi:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Bu işleve aşağıdaki numaralandırılabilir sıralarının geçirebilirsiniz:

- Liste listesini
- Diziler listesi
- Bir dizi listeler
- Bir dizi sıraları
- Herhangi bir birleşimini numaralandırılabilir sıralarının

Aşağıdaki kod `Seq.concat` esnek türler kullanarak destekleyebilir senaryolarını göstermek için.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Çıktı aşağıdaki gibidir:

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

F #'ta nesne yönelimli diğer diller olduğu gibi yok bağlamları içinde türetilmiş türler veya arabirimlerini türleri otomatik olarak bir taban türü veya arabirim türü dönüştürülür. Bu otomatik dönüşümler doğrudan bağımsız değişkenleri, ancak türü bir işlev türü dönüş türü gibi daha karmaşık türde bir parçası olarak ya da bir tür bağımsız değişkeni olarak bir alt konumda olmadığında oluşur. Bu nedenle, bu uygulamaya uygulama türü daha karmaşık bir tür parçası olduğunda esnek türü gösterimi özellikle yararlıdır.

## <a name="see-also"></a>Ayrıca Bkz.

[F# Dili Başvurusu](index.md)

[Genel Türler](generics/index.md)
