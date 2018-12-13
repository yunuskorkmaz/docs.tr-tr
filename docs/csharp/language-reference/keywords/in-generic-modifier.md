---
title: in (genel değiştirici) - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: d43640cbde856ac1df8b5034f904da75de6b077c
ms.sourcegitcommit: 8598d446303b545eed2d520a6ccd061c1a7d00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53334788"
---
# <a name="in-generic-modifier-c-reference"></a>in (Genel Değiştirici) (C# Başvurusu)

Genel tür parametreleri için `in` anahtar sözcüğü, tür parametresi değişken karşıtı olduğunu belirtir. Kullanabileceğiniz `in` genel arabirimlerde ve temsilcilerde anahtar sözcük.

Kontravaryans, genel parametre olarak belirtilenden daha az türetilmiş bir tür belirtmenize olanak sağlar. Bu değişken karşıtı arabirimleri uygulayan sınıflar örtük dönüştürülmesi ve temsilci türlerinin örtük dönüştürme için sağlar. Kovaryans ve kontravaryans, genel tür parametreleri başvuru türleri için desteklenir ancak değer türleri için desteklenmiyor.

Yalnızca bir yöntemin dönüş türü ve bir yöntemin parametre türü tanımlıyorsa türü değişken karşıtı genel arabirim veya temsilci olarak bildirilebilir. `In`, `ref`, ve `out` parametreleri ne olduklarından yani sabit olmalıdır birlikte değişken veya değişken karşıtı.

Yöntemlerinden daha az türetilmiş türler arabirim türü parametresi ile belirtilen değerinden bağımsız değişkenleri kabul etmek bir değişken karşıtı tür parametresine sahip bir arabirim sağlar. Örneğin, <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü değişken karşıtı olduğundan, bir nesnenin atayabilirsiniz `IComparer<Person>` bir nesne türüne `IComparer<Employee>` özel dönüştürme yöntemleri kullanılarak olmadan türü `Employee` devralan `Person`.

Başka bir temsilci aynı türden, ancak daha az türetilmiş bir genel tür parametresi değişken karşıtı temsilci atanabilir.

Daha fazla bilgi için [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Değişken karşıtı genel arabirimi

Aşağıdaki örnek, bildirmek, genişletin ve değişken karşıtı genel bir arabirim uygulamak gösterilmektedir. Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürme nasıl kullanabileceğinizi gösterir.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Değişken karşıtı Genel temsilci

Aşağıdaki örnek, bildirme, oluşturma ve değişken karşıtı Genel temsilci çağırma gösterilmektedir. Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [out](out-generic-modifier.md)  
- [Kovaryans ve Kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)  
- [Değiştiriciler](modifiers.md)  
