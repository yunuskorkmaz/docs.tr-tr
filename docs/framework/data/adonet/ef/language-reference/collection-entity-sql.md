---
title: KOLEKSİYON (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: d4e52bb62412e61e1a71e0fe9a8555068ca18dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506465"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="ffdd9-102">KOLEKSİYON (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="ffdd9-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="ffdd9-103">KOLEKSİYON anahtar sözcüğü, yalnızca bir satır içi işlev tanımında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ffdd9-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="ffdd9-104">Toplama işlevleri değerler koleksiyonu üzerinde çalışan ve bir skaler çıkış üretmesi işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="ffdd9-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdd9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ffdd9-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="ffdd9-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ffdd9-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="ffdd9-107">Desteklenen türler, satır veya başvuruları koleksiyonunu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="ffdd9-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffdd9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffdd9-108">Remarks</span></span>  
 <span data-ttu-id="ffdd9-109">KOLEKSİYON anahtar sözcüğü hakkında daha fazla bilgi için bkz: [tür tanımlarını](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ffdd9-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffdd9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffdd9-110">Example</span></span>  
 <span data-ttu-id="ffdd9-111">Aşağıdaki örnek, ondalık bir koleksiyon için bir satır içi sorgu işlevi bağımsız değişken olarak bildirmek için KOLEKSİYON anahtar sözcüğü kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffdd9-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="ffdd9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffdd9-112">See also</span></span>
- [<span data-ttu-id="ffdd9-113">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ffdd9-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
