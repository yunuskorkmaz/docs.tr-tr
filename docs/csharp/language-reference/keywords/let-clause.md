---
title: Let yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: a6eee9a23fa28b78343e6479106eaa24ecf4caa6
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795371"
---
# <a name="let-clause-c-reference"></a>let tümcesi (C# Başvurusu)

Bir sorgu ifadesinde, alt ifadenin sonucunu izleyen yan tümcelerde kullanmak üzere depolamak bazen yararlı olur. Bunu `let` , yeni bir Aralık değişkeni oluşturan ve bunu sağladığınız ifadenin sonucuyla Başlatan anahtar sözcüğü ile yapabilirsiniz. Bir değerle başlatıldıktan sonra, Aralık değişkeni başka bir değeri depolamak için kullanılamaz. Ancak, Aralık değişkeni sorgulanabilir bir tür içeriyorsa, bu, sorgulanabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte `let` iki şekilde kullanılır:

1. Kendisi için sorgulanabilen bir sıralanabilir tür oluşturmak için.

2. Sorgunun, `ToLower` Aralık değişkeninde yalnızca bir kez çağırmasını sağlamak için `word` . Kullanmadan `let` , `ToLower` yan tümcesindeki her bir koşula çağrı yapmanız gerekir `where` .

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../programming-guide/concepts/linq/index.md)
- [Sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md)
