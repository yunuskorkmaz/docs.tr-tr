---
description: goto ekstresi-C# başvurusu
title: goto ekstresi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128432"
---
# <a name="goto-c-reference"></a>goto (C# Başvurusu)

`goto`İfade program denetimini doğrudan etiketli bir ifadeye aktarır.

Öğesinin yaygın kullanımı `goto` , denetimin belirli bir anahtar-durum etiketine veya bir deyimdeki varsayılan etikete aktarılmalıdır `switch` .

`goto`Deyimden daha fazla iç içe geçmiş döngüler almak için de yararlıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `goto` bir [Switch](switch.md) deyimindeki kullanımını gösterir.

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, `goto` iç içe döngülerden ayırmak için kullanımını gösterir.

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [goto Deyimi (C++)](/cpp/cpp/goto-statement-cpp)
