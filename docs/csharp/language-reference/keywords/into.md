---
title: -içine C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: b209062a2a3e563ea8e70cb7883d9bbfa3662231
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631522"
---
# <a name="into-c-reference"></a>into (C# Başvurusu)

`into` Bağlamsal anahtar sözcüğü, sonuçlarını depolamak için geçici bir tanımlayıcı oluşturmak için kullanılabilir bir [grubu](group-clause.md), [birleştirme](join-clause.md) veya [seçin](select-clause.md) yan tümcesine yeni bir tanımlayıcı. Bu tanımlayıcı kendisini ek sorgu komutları için bir oluşturucuyu olabilir. Kullanıldığında bir `group` veya `select` yan tümcesi, yeni tanımlayıcısı kullanımını bazen olarak adlandırılır bir *devamlılık*.

## <a name="example"></a>Örnek

Aşağıdaki örnek kullanımını gösterir `into` geçici bir tanımlayıcı etkinleştirmek için anahtar sözcüğü `fruitGroup` sahip olduğu bir çıkarsanan tür `IGrouping`. Tanımlayıcısı'nı kullanarak çağırabilirsiniz <xref:System.Linq.Enumerable.Count%2A> yöntemi her grubu ve iki veya daha fazla sözcük içeren grubu seçin.

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

Kullanımını `into` içinde bir `group` yan tümcesi, yalnızca gerekli ek sorgu her grubu işlemleri istediğinizde. Daha fazla bilgi için [group yan tümcesi](group-clause.md).

Kullanımını gösteren bir örnek `into` içinde bir `join` yan tümcesi bkz [JOIN yan tümcesi](join-clause.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Query Keywords (LINQ)](query-keywords.md)
- [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [group yan tümcesi](group-clause.md)
