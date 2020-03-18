---
title: into - C# Referans
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: f0f5ff1e56a65e83385f814df2fadd957f53561e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713621"
---
# <a name="into-c-reference"></a>into (C# Başvurusu)

Bağlamsal anahtar kelime, bir [grubun](group-clause.md)sonuçlarını depolamak, yeni bir tanımlayıcıya yan tümceyi birleştirmek veya [seçmek](select-clause.md) için geçici bir tanımlayıcı oluşturmak için kullanılabilir. [join](join-clause.md) `into` Bu tanımlayıcı, ek sorgu komutları için bir jeneratör olabilir. Bir `group` veya `select` yan tümcede kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamı*olarak adlandırılır.

## <a name="example"></a>Örnek

Aşağıdaki `into` örnekte, çıkarılan bir tür `fruitGroup` `IGrouping`. Tanımlayıcıyı kullanarak, her gruptaki <xref:System.Linq.Enumerable.Count%2A> yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Bir `group` yan `into` tümcenin kullanımı yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir. Daha fazla bilgi için [grup yan tümcesi'ne](group-clause.md)bakın.

Bir yan tümcenin `into` kullanımına `join` ilişkin bir örnek için, [birleştirme yan tümcesi'ne](join-clause.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Anahtar Kelimeleri (LINQ)](query-keywords.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [group yan tümcesi](group-clause.md)
