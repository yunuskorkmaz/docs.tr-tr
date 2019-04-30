---
title: goto deyimi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: e4642d0e43a538217493298b58d572e435db5dae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661548"
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
