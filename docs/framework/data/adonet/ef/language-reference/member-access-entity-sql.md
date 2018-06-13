---
title: biçimindeki telefon numarasıdır. (Üye erişimi) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: fdcd026d245b3f6d6ecaccc0f828f3d77fd6ce1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764638"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="36b55-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="36b55-103">.</span></span> <span data-ttu-id="36b55-104">(Üye erişimi) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="36b55-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="36b55-105">Nokta işleci (.) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişimi işleci.</span><span class="sxs-lookup"><span data-stu-id="36b55-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="36b55-106">Üye erişimi işleci bir özelliği veya alanı yapısal kavramsal model türünün bir örneği, değeri elde etmek üzere kullanın.</span><span class="sxs-lookup"><span data-stu-id="36b55-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36b55-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36b55-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="36b55-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="36b55-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="36b55-109">Bir yapısal kavramsal model türünün bir örneği.</span><span class="sxs-lookup"><span data-stu-id="36b55-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="36b55-110">Bir özellik veya bir nesne örneğine ait alan.</span><span class="sxs-lookup"><span data-stu-id="36b55-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36b55-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36b55-111">Remarks</span></span>  
 <span data-ttu-id="36b55-112">Nokta (.) işleci, karmaşık veya varlık türünün özelliklerini ayıklanması için benzer bir kaydın alanlarını ayıklamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36b55-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="36b55-113">Örneğin, n türü adı türü kişi bir üyesidir ve p kişi türünde bir örnek ise, ardından p.n adı türünde bir değer döndüren bir yasal üye erişimi ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="36b55-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="36b55-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36b55-114">See Also</span></span>  
 [<span data-ttu-id="36b55-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="36b55-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
