---
title: Kullanıcı tanımlı Işlevler (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9e5ad1f6edb0e719733edd2518c5d62a7fc6bdf7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180978"
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="10693-102">Kullanıcı tanımlı Işlevler (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="10693-102">User-Defined Functions (Entity SQL)</span></span>

<span data-ttu-id="10693-103">Entity SQL bir sorgudaki Kullanıcı tanımlı işlevlerin çağrılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="10693-103">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="10693-104">Bu işlevleri sorgu ile satır içi olarak tanımlayabilir (bkz [. nasıl yapılır: Kullanıcı tanımlı bir Işlevi çağırma](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) veya kavramsal modelin bir parçası (bkz. [nasıl yapılır: kavramsal modelde özel işlevler tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="10693-104">You can define these functions inline with the query (see [How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span></span> <span data-ttu-id="10693-105">Kavramsal model işlevleri, kavramsal modeldeki bir [işlev](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) öğesinin [definingexpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) öğesinde bir Entity SQL komutu olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="10693-105">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) element of a [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="10693-106">Entity SQL, sorgu komutunun kendisinde işlevleri tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="10693-106">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="10693-107">[İşlev](function-entity-sql.md) işleci satır içi işlevleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10693-107">The [FUNCTION](function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="10693-108">Tek bir komutta birden çok işlev tanımlayabilirsiniz ve işlev imzaları benzersiz olduğu sürece bu işlevler aynı işlev adına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="10693-108">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="10693-109">Daha fazla bilgi için bkz. [Işlev aşırı yükleme çözünürlüğü](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="10693-109">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10693-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10693-110">See also</span></span>

- [<span data-ttu-id="10693-111">İşlevler</span><span class="sxs-lookup"><span data-stu-id="10693-111">Functions</span></span>](functions-entity-sql.md)
