---
title: BREAK deyimi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 9dc71cce3cc0ca4035df483d2b3a3ab9a3bab9c5
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929227"
---
# <a name="break-c-reference"></a>break (C# Başvurusu)

`break` Deyimi en yakın kapsayan döngüyü sonlandırır veya [geçiş](../../../csharp/language-reference/keywords/switch.md) göründüğü deyimi. Denetim, varsa, sonlandırılmış deyimi takip eden deyime geçirilir.

## <a name="example"></a>Örnek

Bu örnekte, 100'e 1 ila count için beklenen sayaç koşullu deyim içerir. Ancak, `break` deyimi sonra 4 sayıları döngüyü sonlandırır.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Örnek

Bu örnekte, `break` deyimi bir iç iç içe geçmiş döngüden ve denetim için dış döngü döndürmek için kullanılır.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Örnek

Bu örnek kullanımını gösterir `break` içinde bir [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimi.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Girerseniz `4`, çıktı aşağıdaki gibi olur:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [switch](../../../csharp/language-reference/keywords/switch.md)  
- [Atlama Deyimleri](../../../csharp/language-reference/keywords/jump-statements.md)  
- [Yineleme Deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)
