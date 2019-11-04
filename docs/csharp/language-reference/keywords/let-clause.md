---
title: Let yan tümcesi C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422692"
---
# <a name="let-clause-c-reference"></a>let tümcesi (C# Başvurusu)

Bir sorgu ifadesinde, alt ifadenin sonucunu izleyen yan tümcelerde kullanmak üzere depolamak bazen yararlı olur. Bunu, yeni bir Aralık değişkeni oluşturan ve bunu sağladığınız ifadenin sonucuyla Başlatan `let` anahtar sözcüğüyle yapabilirsiniz. Bir değerle başlatıldıktan sonra, Aralık değişkeni başka bir değeri depolamak için kullanılamaz. Ancak, Aralık değişkeni sorgulanabilir bir tür içeriyorsa, bu, sorgulanabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte `let` iki şekilde kullanılır:

1. Kendisi için sorgulanabilen bir sıralanabilir tür oluşturmak için.

2. Sorgunun `ToLower` Aralık değişkeninde yalnızca bir kez çağırmasını sağlamak için `word`. `let`kullanmadan, `where` yan tümcesindeki her koşulda `ToLower` çağırmanız gerekir.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [C#'de LINQ Kullanmaya Başlama](/dotnet/csharp/programming-guide/concepts/linq/)
- [Sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md)
