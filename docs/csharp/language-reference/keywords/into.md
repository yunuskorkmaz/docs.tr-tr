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
ms.openlocfilehash: dc1e2ee004c21bb3d05155eec3e42ea80bf641a1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608644"
---
# <a name="into-c-reference"></a>into (C# Başvurusu)

Bağlamsal anahtar sözcüğü bir [Grup](group-clause.md), [JOIN](join-clause.md) veya Select yan tümcesinin sonuçlarını yeni bir tanımlayıcıya depolamak üzere geçici bir tanımlayıcı oluşturmak için kullanılabilir. [](select-clause.md) `into` Bu tanımlayıcı, ek sorgu komutları için bir Oluşturucu olabilir. `group` Or`select` yan tümcesinde kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamlılık*olarak adlandırılır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğesinin `into` `IGrouping`çıkarılan bir türü olan geçici tanımlayıcıyı `fruitGroup` etkinleştirmek için anahtar sözcüğünün kullanımını gösterir. Tanımlayıcıyı kullanarak, her grupta <xref:System.Linq.Enumerable.Count%2A> yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

`into` Yan tümcelerinde kullanılması yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir. `group` Daha fazla bilgi için bkz. [Group yan tümcesi](group-clause.md).

`into` Bir`join` yan tümcedeki kullanımına bir örnek için bkz. [JOIN yan tümcesi](join-clause.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [LINQ sorgu Ifadeleri](../../programming-guide/linq-query-expressions/index.md)
- [group yan tümcesi](group-clause.md)
