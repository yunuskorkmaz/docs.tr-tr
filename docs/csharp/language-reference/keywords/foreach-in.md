---
title: "foreach, in (C# Başvurusu)"
ms.date: 10/11/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5601682d53a01ff07aba7e416aa81ded4c03e4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="foreach-in-c-reference"></a>foreach, in (C# Başvurusu)
`foreach` Deyimi bir dizi veya uygulayan bir nesne koleksiyonu her öğe için bir grup katıştırılmış ifadeler yineler <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi. `foreach` Deyimi istiyor, ancak öğe eklemek veya beklenmeyen yan etkileri önlemek için kaynak koleksiyondan kaldırmak için kullanılamaz bilgileri almak için koleksiyon yinelemek için kullanılır. Gerekirse eklemek veya kaynak koleksiyondan öğeleri, kullanmak bir [için](for.md) döngü.
  
 Katıştırılmış ifadeler dizisi ya da koleksiyonu her öğe için yürütme devam edin. Koleksiyondaki tüm öğeler için yineleme tamamladıktan sonra sonraki deyimi aşağıdaki denetimi aktarılır `foreach` bloğu.
  
 Bir oranda noktası içinde `foreach` bloğu kullanarak döngü dışında bölünebilir [sonu](break.md) anahtar sözcüğü ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) anahtar sözcüğü.

 A `foreach` döngü ayrıca çıkıldı tarafından [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.

 Hakkında daha fazla bilgi için `foreach` anahtar sözcüğü ve kodu örnekleri, aşağıdaki konulara bakın:  

 [Dizilerle foreach kullanma](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [Nasıl yapılır: foreach ile koleksiyon sınıfına erişme](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a>Örnek
 Aşağıdaki kod üç örnekler gösterilmektedir.

> [!TIP]
> Sözdizimiyle denemek ve kullanım örneğine daha benzer farklı kullanımları denemek için örnekler değiştirebilirsiniz. Kodu çalıştırmak için "Çalıştır" tuşlarına basın, sonra düzenleme ve basın "yeniden çalıştır".

-   Tipik bir `foreach` dizisi içeriğini görüntüler döngüsü

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   bir [için](../../../csharp/language-reference/keywords/for.md) aynı şeyi yapar döngüsü

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   bir `foreach` dizideki öğelerin sayısını tutar döngüsü

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a>C# Dil Belirtimi
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.  

[C# başvurusu](../index.md)

[C# programlama kılavuzu](../../programming-guide/index.md)

[C# anahtar sözcükleri](index.md)

[Yineleme deyimleri](iteration-statements.md)

[için](for.md)
