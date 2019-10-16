---
title: biçimindeki telefon numarasıdır. (Üye erişimi) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 8e63caba9e9efb91d5c4629b9da0b1feca905ace
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319656"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="ae754-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae754-103">.</span></span> <span data-ttu-id="ae754-104">(Üye erişimi) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ae754-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="ae754-105">Nokta işleci (.) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişim işleçtir.</span><span class="sxs-lookup"><span data-stu-id="ae754-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="ae754-106">Yapısal kavramsal model türü örneğinin bir özelliğinin veya alanının değerini elde etmek için üye erişim işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ae754-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae754-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae754-107">Syntax</span></span>  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae754-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae754-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ae754-109">Yapısal kavramsal model türünün bir örneği.</span><span class="sxs-lookup"><span data-stu-id="ae754-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="ae754-110">Bir nesne örneğine ait olan özellik veya alan.</span><span class="sxs-lookup"><span data-stu-id="ae754-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae754-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae754-111">Remarks</span></span>  
 <span data-ttu-id="ae754-112">Nokta (.) işleci bir kayıttaki alanları ayıklamak için, karmaşık veya varlık türünün özelliklerinin ayıklanmasına benzer şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae754-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="ae754-113">Örneğin, tür adı n, kişi türünde bir üyesiyse ve p, kişi türünde bir örnek ise p. n, tür adı değeri veren yasal bir üye erişim deyimidir.</span><span class="sxs-lookup"><span data-stu-id="ae754-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="ae754-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae754-114">See also</span></span>

- [<span data-ttu-id="ae754-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ae754-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
