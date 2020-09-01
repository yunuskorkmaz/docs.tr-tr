---
description: -C# başvurusu
title: -C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 4712a6906195c5d8bc09c7b734dba0df4d2b08c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134529"
---
# <a name="into-c-reference"></a>into (C# Başvurusu)

`into`Bağlamsal anahtar sözcüğü bir [Grup](group-clause.md), [JOIN](join-clause.md) veya [Select](select-clause.md) yan tümcesinin sonuçlarını yeni bir tanımlayıcıya depolamak üzere geçici bir tanımlayıcı oluşturmak için kullanılabilir. Bu tanımlayıcı, ek sorgu komutları için bir Oluşturucu olabilir. `group`Or `select` yan tümcesinde kullanıldığında, yeni tanımlayıcının kullanımı bazen *devamlılık*olarak adlandırılır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `into` `fruitGroup` öğesinin çıkarılan bir türü olan geçici tanımlayıcıyı etkinleştirmek için anahtar sözcüğünün kullanımını gösterir `IGrouping` . Tanımlayıcıyı kullanarak, <xref:System.Linq.Enumerable.Count%2A> her grupta yöntemi çağırabilir ve yalnızca iki veya daha fazla sözcük içeren grupları seçebilirsiniz.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

`into` `group` Yan tümcelerinde kullanılması yalnızca her grupta ek sorgu işlemleri gerçekleştirmek istediğinizde gereklidir. Daha fazla bilgi için bkz. [Group yan tümcesi](group-clause.md).

`into`Bir yan tümcedeki kullanımına bir örnek için `join` bkz. [JOIN yan tümcesi](join-clause.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [group tümcesi](group-clause.md)
