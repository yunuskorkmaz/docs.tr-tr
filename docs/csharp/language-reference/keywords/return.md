---
title: Return bildirisi- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713137"
---
# <a name="return-c-reference"></a>return (C# Başvurusu)

`return` ifadesi, göründüğü yöntemin yürütmesini sonlandırır ve çağırma yöntemine denetimi döndürür. Ayrıca, isteğe bağlı bir değer de döndürebilir. Yöntem bir `void` türüdür, `return` deyimleri atlanabilir.

 Return ifadesinin bir `try` bloğu içindeyse, varsa `finally` bloğu, Denetim çağıran yönteme döndürmeden önce yürütülür.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, yöntemi `CalculateArea()` `area` yerel değişkeni `double` değeri olarak döndürür.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [return Deyimi](/cpp/cpp/return-statement-cpp)
