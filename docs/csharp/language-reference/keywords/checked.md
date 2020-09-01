---
description: Checked anahtar sözcüğü-C# başvurusu
title: Checked anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: 4dd8bc02d3af89d6bab3aef55a88cb8b40704da6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138286"
---
# <a name="checked-c-reference"></a>checked (C# Başvurusu)

`checked`Anahtar sözcüğü, tam sayı türü aritmetik işlemler ve dönüştürmeler için taşma denetimini açık bir şekilde etkinleştirmek üzere kullanılır.

Varsayılan olarak, ifade hedef türü aralığının dışında bir değer üretirse yalnızca sabit değerler içeren bir ifade bir derleyici hatasına neden olur. İfade bir veya daha fazla sabit olmayan değer içeriyorsa, derleyici taşmayı algılamaz. Aşağıdaki örnekte öğesine atanan ifadenin değerlendirilmesi, `i2` bir derleyici hatasına neden olmaz.

[!code-csharp[csrefKeywordsChecked#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#3)]

Varsayılan olarak, bu sabit olmayan ifadeler çalışma zamanında taşma için denetlenmez ve taşma özel durumları oluşturmaz. Önceki örnekte iki pozitif tamsayının toplamı olarak-2.147.483.639 görüntülenir.

Taşma denetimi derleyici seçenekleri, ortam yapılandırması veya anahtar sözcüğünün kullanımı ile etkinleştirilebilir `checked` . Aşağıdaki örneklerde, `checked` `checked` çalışma zamanında önceki Sum tarafından üretilen taşmayı algılamak için bir ifadenin veya bloğun nasıl kullanılacağı gösterilmektedir. Her iki örnek de bir taşma özel durumu yükseltir.

[!code-csharp[csrefKeywordsChecked#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#4)]

[İşaretlenmemiş](./unchecked.md) anahtar sözcük, taşma denetimini engellemek için kullanılabilir.

## <a name="example"></a>Örnek

Bu örnek, `checked` çalışma zamanında taşma denetimini etkinleştirmek için nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsChecked#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#1)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [Checked ve Unchecked](./checked-and-unchecked.md)
- [unchecked](./unchecked.md)
