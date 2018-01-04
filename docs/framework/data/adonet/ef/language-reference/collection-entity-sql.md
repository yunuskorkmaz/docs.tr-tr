---
title: "KOLEKSİYON (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c850fe215c692f204c6762d82a3d37b29c556a7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="collection-entity-sql"></a>KOLEKSİYON (varlık SQL)
KOLEKSİYON anahtar sözcüğü yalnızca bir satır içi işlev tanımı'nda kullanılır. Toplama işlevleri değerler koleksiyonu üzerinde çalışan ve skaler bir çıktı oluşturmak işlevlerdir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a>Arguments  
 `type_definition`  
 Desteklenen türler, satır veya başvuruları koleksiyonu döndüren bir ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 KOLEKSİYON anahtar sözcüğü hakkında daha fazla bilgi için bkz: [tür tanımları](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, KOLEKSİYON anahtar sözcüğü ondalık bir koleksiyon için bir satır içi sorgu işlevi bağımsız değişken olarak bildirmek için nasıl kullanılacağını gösterir.  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
