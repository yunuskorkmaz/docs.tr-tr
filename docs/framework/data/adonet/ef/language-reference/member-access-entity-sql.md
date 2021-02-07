---
description: Hakkında daha fazla bilgi edinin:. (Üye erişimi) (Entity SQL)
title: . (Üye erişimi) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 94833d3525c7d17cadaef15065b3dcbdb43a6ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739384"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="d4ec5-105">.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-105">.</span></span> <span data-ttu-id="d4ec5-106">(Üye erişimi) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d4ec5-106">(Member Access) (Entity SQL)</span></span>

<span data-ttu-id="d4ec5-107">Nokta işleci (.) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişim işleçtir.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-107">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="d4ec5-108">Yapısal kavramsal model türü örneğinin bir özelliğinin veya alanının değerini elde etmek için üye erişim işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-108">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ec5-109">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d4ec5-109">Syntax</span></span>  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="d4ec5-110">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="d4ec5-110">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="d4ec5-111">Yapısal kavramsal model türünün bir örneği.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-111">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="d4ec5-112">Bir nesne örneğine ait olan özellik veya alan.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-112">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4ec5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4ec5-113">Remarks</span></span>  

 <span data-ttu-id="d4ec5-114">Nokta (.) işleci bir kayıttaki alanları ayıklamak için, karmaşık veya varlık türünün özelliklerinin ayıklanmasına benzer şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-114">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="d4ec5-115">Örneğin, tür adı n, kişi türünde bir üyesiyse ve p, kişi türünde bir örnek ise p. n, tür adı değeri veren yasal bir üye erişim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-115">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="d4ec5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4ec5-116">See also</span></span>

- [<span data-ttu-id="d4ec5-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d4ec5-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
