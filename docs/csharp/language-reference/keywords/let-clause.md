---
title: let tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 62294df7f0f2ebb3249dffd72ba4910fbae984c8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47230716"
---
# <a name="let-clause-c-reference"></a>let tümcesi (C# Başvurusu)

Bir sorgu ifadesinde bazen sonraki yan tümcelerinde kullanmak için bir alt ifadenin sonucu depolamak yararlıdır. İle bunu yapabilirsiniz `let` yeni bir aralık değişkenine oluşturan ve sağladığınız ifadenin sonucu ile başlatır anahtar sözcüğü. Bir değerle başlatıldıktan sonra başka bir değeri depolamak için aralık değişkeni kullanılamaz. Ancak, aralık değişkeni bir sorgulanabilir tür tutar, sorgulanabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte `let` iki şekilde kullanılır:

1. Kendisini sorgulanabilir bir numaralandırma türü oluşturmak için.

2. Aranacak sorgu etkinleştirmek için `ToLower` aralık değişkeni üzerinde yalnızca bir kez `word`. Kullanmadan `let`, çağırmak zorunda `ToLower` her koşulda içinde `where` yan tümcesi.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../linq/index.md)
- [C#'de LINQ Kullanmaya Başlama](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [Sorgu ifadelerinde özel durumları işleme](../../linq/handle-exceptions-in-query-expressions.md)