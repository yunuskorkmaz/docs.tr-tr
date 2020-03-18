---
title: kontrol edilen anahtar kelime - C# Referans
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 5963bb85ef4b61c1dc478667fb0e2e5438f3e4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713703"
---
# <a name="checked-c-reference"></a>checked (C# Başvurusu)

Anahtar `checked` kelime, integral türü aritmetik işlemleri ve dönüşümleri için taşma denetimini açıkça etkinleştirmek için kullanılır.

Varsayılan olarak, yalnızca sabit değerler içeren bir ifade, ifade hedef türünün aralığıdışında bir değer üretirse derleyici hatasına neden olur. İfade bir veya daha fazla sabit olmayan değerler içeriyorsa, derleyici taşma algılamaz. Aşağıdaki `i2` örnekte atanan ifadeyi değerlendirmek derleyici hatasına neden olmaz.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Varsayılan olarak, bu sabit olmayan ifadeler de çalışma zamanında taşma için denetlenmez ve taşma özel durumları yükseltmez. Önceki örnekte -2,147,483,639 iki pozitif tamsaın toplamı olarak görüntülenir.

Taşma denetimi derleyici seçenekleri, ortam yapılandırması `checked` veya anahtar kelimenin kullanımı yla etkinleştirilebilir. Aşağıdaki örnekler, önceki toplamın çalışma zamanında ürettiği taşmayı algılamak için bir `checked` ifadenin veya bloğun `checked` nasıl kullanılacağını gösterir. Her iki örnek de bir taşma özel durum yükseltmek.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[Denetlenemeyen](./unchecked.md) anahtar kelime taşma denetimini önlemek için kullanılabilir.

## <a name="example"></a>Örnek

Bu örnek, çalışma `checked` zamanında taşma denetimini etkinleştirmek için nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Checked ve Unchecked](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
