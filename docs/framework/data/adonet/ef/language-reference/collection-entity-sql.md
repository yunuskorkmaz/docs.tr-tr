---
title: KOLEKSİYON (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 8cd440571726796ee3d2c91e0d2f6b50571e8e27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785333"
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
