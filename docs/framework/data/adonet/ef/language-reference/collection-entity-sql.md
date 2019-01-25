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
# <a name="collection-entity-sql"></a>KOLEKSİYON (varlık SQL)
KOLEKSİYON anahtar sözcüğü, yalnızca bir satır içi işlev tanımında kullanılır. Toplama işlevleri değerler koleksiyonu üzerinde çalışan ve bir skaler çıkış üretmesi işlevlerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Desteklenen türler, satır veya başvuruları koleksiyonunu döndüren bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 KOLEKSİYON anahtar sözcüğü hakkında daha fazla bilgi için bkz: [tür tanımlarını](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ondalık bir koleksiyon için bir satır içi sorgu işlevi bağımsız değişken olarak bildirmek için KOLEKSİYON anahtar sözcüğü kullanmayı gösterir.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
