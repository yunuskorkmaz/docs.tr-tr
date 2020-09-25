---
title: KOLEKSIYON (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: c960ee69f8188f6dd3184b6fb31f3432f8d58fee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197956"
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
