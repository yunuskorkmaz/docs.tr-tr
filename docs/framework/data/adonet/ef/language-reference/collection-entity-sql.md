---
description: KOLEKSIYON hakkında daha fazla bilgi edinin (Entity SQL)
title: KOLEKSIYON (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 1269680b2a9009277e79337cfe4df154885b7c1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697055"
---
# <a name="collection-entity-sql"></a>KOLEKSIYON (Entity SQL)

KOLEKSIYON anahtar sözcüğü yalnızca bir satır içi işlevin tanımında kullanılır. Koleksiyon işlevleri, bir değer koleksiyonunda çalışan ve skaler bir çıktı üreten işlevlerdir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `type_definition`  
 Desteklenen türlerin, satırların veya başvuruların koleksiyonunu döndüren bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 KOLEKSIYON anahtar sözcüğü hakkında daha fazla bilgi için bkz. [tür tanımları](type-definitions-entity-sql.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir satır içi sorgu işlevi için bir bağımsız değişken olarak bir ondalık toplamayı bildirmek üzere COLLECTION anahtar sözcüğünün nasıl kullanılacağını göstermektedir.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
