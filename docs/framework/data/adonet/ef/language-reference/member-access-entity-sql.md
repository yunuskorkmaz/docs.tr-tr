---
title: biçimindeki telefon numarasıdır. (Üye erişimi) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: e2874e5bff8d8c34f700a81bf52c6729df49aca5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626680"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="21678-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="21678-103">.</span></span> <span data-ttu-id="21678-104">(Üye erişimi) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="21678-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="21678-105">Nokta işleci (.), [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişimi işleci.</span><span class="sxs-lookup"><span data-stu-id="21678-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="21678-106">Üye erişim işleci, bir özellik veya alan yapısal kavramsal model türünün bir örneğinin değerini elde etmek üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="21678-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21678-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21678-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="21678-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="21678-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="21678-109">Yapısal kavramsal model türünün bir örneği.</span><span class="sxs-lookup"><span data-stu-id="21678-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="21678-110">Bir özellik veya alan bir nesne örneğine ait.</span><span class="sxs-lookup"><span data-stu-id="21678-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21678-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21678-111">Remarks</span></span>  
 <span data-ttu-id="21678-112">Nokta (.) işleci, karmaşık veya varlık türünün özelliklerini ayıklanması için benzer bir kaydın alanlarını ayıklamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21678-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="21678-113">Örneğin, tür adı n kişi türündeki bir üyesi olduğundan ve p kişi türünün bir örneği p.n adı türünde bir değer döndüren bir yasal üye erişim ifadesi olan.</span><span class="sxs-lookup"><span data-stu-id="21678-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="21678-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21678-114">See also</span></span>
- [<span data-ttu-id="21678-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="21678-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
