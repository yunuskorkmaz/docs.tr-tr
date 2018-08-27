---
title: into (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: eb0cde84ff57d1c4b927850ffddb1e862ea8f8dc
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925704"
---
# <a name="into-c-reference"></a>into (C# Başvurusu)

`into` Bağlamsal anahtar sözcüğü, sonuçlarını depolamak için geçici bir tanımlayıcı oluşturmak için kullanılabilir bir [grubu](group-clause.md), [birleştirme](join-clause.md) veya [seçin](select-clause.md) yan tümcesine yeni bir tanımlayıcı. Bu tanımlayıcı kendisini ek sorgu komutları için bir oluşturucuyu olabilir. Kullanıldığında bir `group` veya `select` yan tümcesi, yeni tanımlayıcısı kullanımını bazen olarak adlandırılır bir *devamlılık*.

## <a name="example"></a>Örnek

Aşağıdaki örnek kullanımını gösterir `into` geçici bir tanımlayıcı etkinleştirmek için anahtar sözcüğü `fruitGroup` sahip olduğu bir çıkarsanan tür `IGrouping`. Tanımlayıcısı'nı kullanarak çağırabilirsiniz <xref:System.Linq.Enumerable.Count%2A> yöntemi her grubu ve iki veya daha fazla sözcük içeren grubu seçin.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Kullanımını `into` içinde bir `group` yan tümcesi, yalnızca gerekli ek sorgu her grubu işlemleri istediğinizde. Daha fazla bilgi için [group yan tümcesi](group-clause.md).

Kullanımını gösteren bir örnek `into` içinde bir `join` yan tümcesi bkz [JOIN yan tümcesi](join-clause.md).

## <a name="see-also"></a>Ayrıca bkz.

[Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)  
[LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
[group yan tümcesi](group-clause.md)  