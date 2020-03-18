---
title: goto deyimi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715282"
---
# <a name="goto-c-reference"></a>goto (C# Başvurusu)

İfade, `goto` program denetimini doğrudan etiketli bir bildirime aktarMaktadır.

Denetimin `goto` yaygın kullanımı, denetimi belirli bir anahtar-servis talebi etiketine veya bir `switch` deyimdeki varsayılan etikete aktarmaktır.

İfade, `goto` derin iç içe giden döngülerden çıkmak için de yararlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `goto` [anahtar](switch.md) deyiminde kullanımı gösterir.

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, iç `goto` içe giden döngülerden çıkmak için kullanımı gösterir.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [goto Deyimi (C++)](/cpp/cpp/goto-statement-cpp)
