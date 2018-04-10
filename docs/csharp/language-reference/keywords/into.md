---
title: into (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a><span data-ttu-id="b2e1f-102">into (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b2e1f-102">into (C# Reference)</span></span>
<span data-ttu-id="b2e1f-103">`into` Bağlamsal anahtar sözcüğü, sonuçlarını depolamak için geçici bir tanımlayıcı oluşturmak için kullanılabilecek bir [grup](../../../csharp/language-reference/keywords/group-clause.md), [birleştirme](../../../csharp/language-reference/keywords/join-clause.md) veya [seçin](../../../csharp/language-reference/keywords/select-clause.md) yan tümcesine yeni bir tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b2e1f-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) or [select](../../../csharp/language-reference/keywords/select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="b2e1f-104">Bu tanımlayıcı kendisini ek sorgu komutları için bir oluşturucuyu olabilir.</span><span class="sxs-lookup"><span data-stu-id="b2e1f-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="b2e1f-105">Kullanıldığında bir `group` veya `select` yan tümcesi, yeni tanımlayıcısı kullanımını bazen olarak adlandırılır bir *devamlılık*.</span><span class="sxs-lookup"><span data-stu-id="b2e1f-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2e1f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2e1f-106">Example</span></span>  
 <span data-ttu-id="b2e1f-107">Aşağıdaki örnek kullanımı gösterilmiştir `into` geçici bir tanımlayıcı etkinleştirmek için anahtar sözcüğü `fruitGroup` oluşturulursa bir tür olan `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="b2e1f-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="b2e1f-108">Tanımlayıcısını kullanarak, çağırabilirsiniz <xref:System.Linq.Enumerable.Count%2A> yöntemi her grubu ve iki veya daha fazla sözcükleri içeren gruplar'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b2e1f-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 <span data-ttu-id="b2e1f-109">Kullanımını `into` içinde bir `group` yan tümcesi, yalnızca gerekli her grubu ek sorgu işlemleri istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="b2e1f-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="b2e1f-110">Daha fazla bilgi için bkz: [group yan tümcesi](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2e1f-110">For more information, see [group clause](../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="b2e1f-111">Kullanımına ilişkin bir örnek `into` içinde bir `join` yan tümcesi, bkz: [JOIN yan tümcesi](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b2e1f-111">For an example of the use of `into` in a `join` clause, see [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e1f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2e1f-112">See Also</span></span>  
 [<span data-ttu-id="b2e1f-113">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b2e1f-113">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="b2e1f-114">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="b2e1f-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="b2e1f-115">Group tümcesi</span><span class="sxs-lookup"><span data-stu-id="b2e1f-115">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)
