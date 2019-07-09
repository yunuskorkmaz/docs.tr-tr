---
title: return deyimi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661609"
---
# <a name="return-c-reference"></a>return (C# Başvurusu)

`return` Deyimi yöntemin hangi görüntülenir ve çağıran Metoda döndürür denetim yürütülmesini sonlandırır. Ayrıca, isteğe bağlı bir değer de döndürebilir. Yöntem ise bir `void` türü `return` ifade atlanabilir.

 Return deyimi içinde ise bir `try` bloğu `finally` bloğu, varsa, yürütülecek önce denetimini çağıran Metoda döndürür.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte, yöntem `CalculateArea()` yerel değişkeni döndürür `area` olarak bir `double` değeri.

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [return Deyimi](/cpp/cpp/return-statement-cpp)
