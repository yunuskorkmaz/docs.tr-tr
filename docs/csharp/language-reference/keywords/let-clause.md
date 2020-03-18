---
title: let yan tümcesi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173594"
---
# <a name="let-clause-c-reference"></a>let tümcesi (C# Başvurusu)

Sorgu ifadesinde, bir alt ifadenin sonucunu sonraki tümcelerde kullanmak için depolamak bazen yararlıdır. Bunu, yeni bir `let` aralık değişkeni oluşturan ve sağladığınız ifadenin sonucuyla baş harfe çeken anahtar kelimeyle yapabilirsiniz. Bir değerle baş harfe büründükten sonra, aralık değişkeni başka bir değeri depolamak için kullanılamaz. Ancak, aralık değişkeni sorgulanabilir bir tür tutuyorsa, sorgulanabilir bir tür sorgulanabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte `let` iki şekilde kullanılır:

1. Kendisi sorgulanabilir bir sayısal olabilir türü oluşturmak için.

2. Sorgunun aralık değişkeninde `ToLower` `word`yalnızca bir kez aramasını sağlamak için. Kullanmadan, `let`yan tümcedeki her yüklemi `where` çağırmanız `ToLower` gerekir.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [Sorgu Anahtar Kelimeleri (LINQ)](query-keywords.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../programming-guide/concepts/linq/index.md)
- [Sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md)
