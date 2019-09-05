---
title: biçimindeki telefon numarasıdır. (Üye erişimi) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 1db6be632da90eaa7a761bb213e395182ae42347
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250289"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="c7ce5-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-103">.</span></span> <span data-ttu-id="c7ce5-104">(Üye erişimi) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c7ce5-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="c7ce5-105">Nokta işleci (.) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişim işleçtir.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="c7ce5-106">Yapısal kavramsal model türü örneğinin bir özelliğinin veya alanının değerini elde etmek için üye erişim işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ce5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7ce5-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7ce5-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="c7ce5-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c7ce5-109">Yapısal kavramsal model türünün bir örneği.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="c7ce5-110">Bir nesne örneğine ait olan özellik veya alan.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7ce5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7ce5-111">Remarks</span></span>  
 <span data-ttu-id="c7ce5-112">Nokta (.) işleci bir kayıttaki alanları ayıklamak için, karmaşık veya varlık türünün özelliklerinin ayıklanmasına benzer şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="c7ce5-113">Örneğin, tür adı n, kişi türünde bir üyesiyse ve p, kişi türünde bir örnek ise p. n, tür adı değeri veren yasal bir üye erişim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="c7ce5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7ce5-114">See also</span></span>

- [<span data-ttu-id="c7ce5-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c7ce5-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
