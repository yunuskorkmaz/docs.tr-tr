---
title: "(Varlık SQL) kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cc69dba9e70bb6bcc870b1cb92e98cb656cad98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-entity-sql"></a>(Varlık SQL) kullanma
Ad alanları sorgu ifadesinde kullanılan belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  
 `alias`  
 Bir ad alanıyla nitelemek için daha kısa bir diğer ad belirtir.  
  
 `namespace`  
 Tüm geçerli ad alanı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu kullanarak işleci sorgu ifadesinde kullanılan ad alanları belirtmek için kullanır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ad Alanları](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
