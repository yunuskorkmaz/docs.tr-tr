---
title: goto deyimi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: d4fd9f1f26b82b409d704c45e4bcf18cceef8282
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405822"
---
# <a name="goto-c-reference"></a>goto (C# Başvurusu)

`goto` Deyimi programın denetimini doğrudan etiketli bir deyime aktarır.

Yaygın `goto` belirli bir anahtar durumu etiket ya da varsayılan etiket, denetimin aktarmaktır bir `switch` deyimi.

`goto` Deyimi, ayrıca iç içe döngüleri dışında almak kullanışlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örneği kullanarak göstermektedir `goto` içinde bir [geçiş](switch.md) deyimi.

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Örnek

Aşağıdaki örneği kullanarak göstermektedir `goto` iç içe döngüleri ayırmak için.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [goto Deyimi (C++)](/cpp/cpp/goto-statement-cpp)  
- [Atlama Deyimleri](jump-statements.md)  
