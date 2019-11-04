---
title: C# başvuruya göre
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: ccb1463db51510d275b7053955a0257bd4fe621e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422705"
---
# <a name="into-c-reference"></a>into (C# Başvurusu)

`into` bağlamsal anahtar sözcüğü, bir [Grup](group-clause.md), [JOIN](join-clause.md) veya [Select](select-clause.md) yan tümcesinin sonuçlarını yeni bir tanımlayıcıya depolamak üzere geçici bir tanımlayıcı oluşturmak için kullanılabilir. Bu tanımlayıcı, ek sorgu komutları için bir Oluşturucu olabilir. Bir `group` veya `select` yan tümcesinde kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamlılık*olarak adlandırılır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `fruitGroup` bir `IGrouping`türü olan geçici bir tanımlayıcıyı etkinleştirmek için `into` anahtar sözcüğünün kullanımını gösterir. Tanımlayıcıyı kullanarak, her grupta <xref:System.Linq.Enumerable.Count%2A> yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

`group` yan tümcesinde `into` kullanımı yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir. Daha fazla bilgi için bkz. [Group yan tümcesi](group-clause.md).

Bir `join` yan tümcesinde `into` kullanımı örneği için bkz. [JOIN yan tümcesi](join-clause.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [group yan tümcesi](group-clause.md)
