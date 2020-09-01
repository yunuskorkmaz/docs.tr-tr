---
description: Return ekstresi-C# başvurusu
title: Return ekstresi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137012"
---
# <a name="return-c-reference"></a>return (C# Başvurusu)

`return`İfadesi, göründüğü yöntemin yürütmesini sonlandırır ve çağırma yöntemine denetim döndürür. Ayrıca, isteğe bağlı bir değer de döndürebilir. Yöntem bir `void` tür ise, `return` ifade atlanabilir.

 Return yöntemi bir blok içindeyse, bir blok varsa, `try` `finally` Denetim çağırma yöntemine döndürmeden önce yürütülür.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, yöntemi `CalculateArea()` yerel değişkeni `area` bir değer olarak döndürür `double` .

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Return ekstresi](/cpp/cpp/return-statement-cpp)
