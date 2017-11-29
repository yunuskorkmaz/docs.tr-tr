---
title: "into (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords: into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a>into (C# Başvurusu)
`into` Bağlamsal anahtar sözcüğü, sonuçlarını depolamak için geçici bir tanımlayıcı oluşturmak için kullanılabilecek bir [grup](../../../csharp/language-reference/keywords/group-clause.md), [birleştirme](../../../csharp/language-reference/keywords/join-clause.md) veya [seçin](../../../csharp/language-reference/keywords/select-clause.md) yan tümcesine yeni bir tanımlayıcısı. Bu tanımlayıcı kendisini ek sorgu komutları için bir oluşturucuyu olabilir. Kullanıldığında bir `group` veya `select` yan tümcesi, yeni tanımlayıcısı kullanımını bazen olarak adlandırılır bir *devamlılık*.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanımı gösterilmiştir `into` geçici bir tanımlayıcı etkinleştirmek için anahtar sözcüğü `fruitGroup` oluşturulursa bir tür olan `IGrouping`. Tanımlayıcısını kullanarak, çağırabilirsiniz <xref:System.Linq.Enumerable.Count%2A> yöntemi her grubu ve iki veya daha fazla sözcükleri içeren gruplar'ı seçin.  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 Kullanımını `into` içinde bir `group` yan tümcesi, yalnızca gerekli her grubu ek sorgu işlemleri istediğinizde. Daha fazla bilgi için bkz: [group yan tümcesi](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Kullanımına ilişkin bir örnek `into` içinde bir `join` yan tümcesi, bkz: [JOIN yan tümcesi](../../../csharp/language-reference/keywords/join-clause.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu anahtar sözcükleri (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Group tümcesi](../../../csharp/language-reference/keywords/group-clause.md)
