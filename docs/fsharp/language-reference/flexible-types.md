---
title: Esnek Türler
description: 'Bir parametre, değişken veya değerin belirtilen tür ile uyumlu bir türe sahip olduğunu belirten F # esnek tür ek açıklamasını nasıl kullanacağınızı öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 44241ad082cd7f3de9e0cc6a48b8a8946e7b33d3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557756"
---
# <a name="flexible-types"></a>Esnek Türler

*Esnek tür ek açıklaması* , bir parametre, değişken veya değerin belirtilen tür ile uyumlu bir türe sahip olduğunu belirtir; burada uyumluluk, nesne odaklı sınıfların veya arabirimlerin bulunduğu konuma göre belirlenir. Esnek türler özellikle tür hiyerarşisinde daha üst türlere otomatik dönüştürme gerçekleşmezse yararlı olur ancak yine de işlevselliği hiyerarşide herhangi bir türle veya bir arabirim uygulayan herhangi bir tür ile çalışacak şekilde etkinleştirmek istiyorsanız.

## <a name="syntax"></a>Syntax

```fsharp
#type
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *tür* bir temel türü veya arabirimi temsil eder.

Esnek tür, izin verilen türleri temel veya arabirim türüyle uyumlu türlere sınırlayan bir kısıtlamaya sahip genel bir tür ile eşdeğerdir. Diğer bir deyişle, aşağıdaki iki kod satırı eşdeğerdir.

```fsharp
#SomeType

'T when 'T :> SomeType
```

Esnek türler birkaç tür durumda yararlıdır. Örneğin, daha yüksek bir order işleviniz (bağımsız değişken olarak işlev alan bir işlev) olduğunda, işlevin esnek bir tür döndürmesi genellikle yararlı olur. Aşağıdaki örnekte, içinde bir dizi bağımsız değişkeni olan esnek bir tür kullanılması, `iterate2` daha yüksek sıralı işlevin diziler, diziler, listeler ve diğer herhangi bir sıralanabilir tür oluşturan işlevlerle çalışmasını sağlar.

Aşağıdaki iki işlevi göz önünde bulundurun, bunlardan biri bir dizi döndürür, diğeri ise esnek bir tür döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Başka bir örnek olarak, [Seq. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#concat) Kitaplık işlevini göz önünde bulundurun:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Aşağıdaki sıralanabilir dizileri bu işleve geçirebilirsiniz:

- Listelerin listesi
- Dizilerin listesi
- Listelerden oluşan bir dizi
- Dizi dizileri
- Sıralanabilir sıraların diğer birleşimleri

Aşağıdaki kod, `Seq.concat` Esnek türler kullanarak destekleyerek kullanabileceğiniz senaryoları göstermek için kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Çıktı aşağıdaki gibidir:

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

F # ' da, diğer nesne yönelimli dillerde olduğu gibi, arabirimleri uygulayan türetilmiş türlerin veya türlerin otomatik olarak temel tür veya arabirim türüne dönüştürüldüğü bağlamlar vardır. Bu otomatik dönüştürmeler doğrudan bağımsız değişkenlerde oluşur, ancak tür bir alt konumda olduğunda değil, bir işlev türünün dönüş türü veya tür bağımsız değişkeni gibi daha karmaşık bir türün parçası olarak değildir. Bu nedenle, esnek tür gösterimi öncelikle, uyguladığınız tür daha karmaşık bir türün parçası olduğunda faydalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Genel Türler](./generics/index.md)
