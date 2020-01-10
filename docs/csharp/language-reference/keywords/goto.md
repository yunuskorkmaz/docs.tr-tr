---
title: goto bildirisi- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715282"
---
# <a name="goto-c-reference"></a>goto (C# Başvurusu)

`goto` ifade program denetimini doğrudan etiketli bir ifadeye aktarır.

`goto` ortak kullanımı, denetimin belirli bir anahtar-durum etiketine veya bir `switch` deyimindeki varsayılan etikete aktarılmalıdır.

`goto` deyimleri, derin iç içe geçmiş döngüler almak için de kullanışlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir [Switch](switch.md) deyimindeki `goto` kullanmayı gösterir.

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, iç içe döngülerden kesmek için `goto` kullanmayı gösterir.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [goto Deyimi (C++)](/cpp/cpp/goto-statement-cpp)
