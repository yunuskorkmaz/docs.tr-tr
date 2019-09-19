---
title: Esnek Türler
description: Bir parametre, değişken F# veya değerin belirtilen tür ile uyumlu bir türe sahip olduğunu gösteren esnek tür ek açıklamasını nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: bf05f78f163d1f9c73c667df60925b66a5315627
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083072"
---
# <a name="flexible-types"></a>Esnek Türler

*Esnek tür ek açıklaması* , bir parametre, değişken veya değerin belirtilen tür ile uyumlu bir türe sahip olduğunu belirtir; burada uyumluluk, nesne odaklı sınıfların veya arabirimlerin bulunduğu konuma göre belirlenir. Esnek türler özellikle tür hiyerarşisinde daha üst türlere otomatik dönüştürme gerçekleşmezse yararlı olur ancak yine de işlevselliği hiyerarşide herhangi bir türle veya bir arabirim uygulayan herhangi bir tür ile çalışacak şekilde etkinleştirmek istiyorsanız.

## <a name="syntax"></a>Sözdizimi

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

Esnek türler birkaç tür durumda yararlıdır. Örneğin, daha yüksek bir order işleviniz (bağımsız değişken olarak işlev alan bir işlev) olduğunda, işlevin esnek bir tür döndürmesi genellikle yararlı olur. Aşağıdaki örnekte, içinde `iterate2` bir dizi bağımsız değişkeni olan esnek bir tür kullanılması, daha yüksek sıralı işlevin diziler, diziler, listeler ve diğer herhangi bir sıralanabilir tür oluşturan işlevlerle çalışmasını sağlar.

Aşağıdaki iki işlevi göz önünde bulundurun, bunlardan biri bir dizi döndürür, diğeri ise esnek bir tür döndürür.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

Başka bir örnek olarak, [Seq. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) Kitaplık işlevini göz önünde bulundurun:

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

Aşağıdaki sıralanabilir dizileri bu işleve geçirebilirsiniz:

- Listelerin listesi
- Dizilerin listesi
- Listelerden oluşan bir dizi
- Dizi dizileri
- Sıralanabilir sıraların diğer birleşimleri

Aşağıdaki kod, esnek `Seq.concat` türler kullanarak destekleyerek kullanabileceğiniz senaryoları göstermek için kullanır.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

Çıktı aşağıdaki gibidir:

```console
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

' F#De, diğer nesne yönelimli dillerde olduğu gibi, arabirimleri uygulayan türetilmiş türlerin veya türlerin otomatik olarak temel türe veya arabirim türüne dönüştürüldüğü bağlamlar vardır. Bu otomatik dönüştürmeler doğrudan bağımsız değişkenlerde oluşur, ancak tür bir alt konumda olduğunda değil, bir işlev türünün dönüş türü veya tür bağımsız değişkeni gibi daha karmaşık bir türün parçası olarak değildir. Bu nedenle, esnek tür gösterimi öncelikle, uyguladığınız tür daha karmaşık bir türün parçası olduğunda faydalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Genel Türler](./generics/index.md)
