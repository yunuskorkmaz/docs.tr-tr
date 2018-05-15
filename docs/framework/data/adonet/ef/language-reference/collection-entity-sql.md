---
title: KOLEKSİYON (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 2b13d373e6c54221249b17de4fa91347cbc0f9e6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="collection-entity-sql"></a><span data-ttu-id="e31a0-102">KOLEKSİYON (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e31a0-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="e31a0-103">KOLEKSİYON anahtar sözcüğü yalnızca bir satır içi işlev tanımı'nda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e31a0-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="e31a0-104">Toplama işlevleri değerler koleksiyonu üzerinde çalışan ve skaler bir çıktı oluşturmak işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="e31a0-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e31a0-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="e31a0-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e31a0-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="e31a0-107">Desteklenen türler, satır veya başvuruları koleksiyonu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e31a0-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e31a0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e31a0-108">Remarks</span></span>  
 <span data-ttu-id="e31a0-109">KOLEKSİYON anahtar sözcüğü hakkında daha fazla bilgi için bkz: [tür tanımları](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e31a0-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e31a0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e31a0-110">Example</span></span>  
 <span data-ttu-id="e31a0-111">Aşağıdaki örnek, KOLEKSİYON anahtar sözcüğü ondalık bir koleksiyon için bir satır içi sorgu işlevi bağımsız değişken olarak bildirmek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e31a0-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="e31a0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e31a0-112">See Also</span></span>  
 [<span data-ttu-id="e31a0-113">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e31a0-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
