---
title: KOLEKSIYON (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 0e611add4ce3f20e42bb01b0bf0392bbe81ec548
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251193"
---
# <a name="collection-entity-sql"></a>KOLEKSIYON (Entity SQL)
KOLEKSIYON anahtar sözcüğü yalnızca bir satır içi işlevin tanımında kullanılır. Koleksiyon işlevleri, bir değer koleksiyonunda çalışan ve skaler bir çıktı üreten işlevlerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Desteklenen türlerin, satırların veya başvuruların koleksiyonunu döndüren bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 KOLEKSIYON anahtar sözcüğü hakkında daha fazla bilgi için bkz. [tür tanımları](type-definitions-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir satır içi sorgu işlevi için bir bağımsız değişken olarak bir ondalık toplamayı bildirmek üzere COLLECTION anahtar sözcüğünün nasıl kullanılacağını göstermektedir.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
