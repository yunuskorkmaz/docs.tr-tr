---
title: "Burada (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2ad170500770bc370eb67a04ab29d0c9f9dcaabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="where-entity-sql"></a>Burada (varlık SQL)
WHERE yan tümcesi doğrudan sonra uygulanan [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) yan tümcesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir Boolean türü.  
  
## <a name="remarks"></a>Açıklamalar  
 WHERE yan tümcesi için açıklandığı gibi aynı semantiğine sahip [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]. Bu koşul geçirmek için kaynak koleksiyonlarını öğelerini sınırlayarak sorgu ifadesi tarafından üretilen nesnelerin kısıtlar.  
  
```  
select c from cs as c where e  
```  
  
 İfade `e` Boolean türünde olmalıdır.  
  
 WHERE yan tümcesi FROM yan tümcesi hemen sonra ve hiçbir gruplandırma, sıralama veya yansıtma önce uygulandığı yerini alır. FROM yan tümcesinde tanımlanan tüm öğe adları WHERE yan tümcesi ifade için görünür durumdadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
