---
title: KOLEKSIYON (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 5a1af1aab8a084b19e48fbdbb159d7ddd8a8dd7c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039903"
---
# <a name="collection-entity-sql"></a>KOLEKSIYON (Entity SQL)
KOLEKSIYON anahtar sözcüğü yalnızca bir satır içi işlevin tanımında kullanılır. Koleksiyon işlevleri, bir değer koleksiyonunda çalışan ve skaler bir çıktı üreten işlevlerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp  
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
