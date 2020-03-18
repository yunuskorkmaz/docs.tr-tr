---
title: iade deyimi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713137"
---
# <a name="return-c-reference"></a>return (C# Başvurusu)

İfade, `return` görüntülendiği yöntemin yürütülmesini sonlandırır ve denetimi arama yöntemine döndürür. İsteğe bağlı bir değer de döndürebilir. Yöntem bir `void` türse, `return` deyim atlanabilir.

 İade deyimi bir `try` blok içindeyse, `finally` denetim arama yöntemine dönmeden önce blok, varsa yürütülür.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, yöntem `CalculateArea()` yerel değişkeni `area` `double` bir değer olarak döndürür.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [return Deyimi](/cpp/cpp/return-statement-cpp)
