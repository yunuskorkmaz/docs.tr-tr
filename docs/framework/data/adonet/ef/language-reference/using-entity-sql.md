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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d1a47102c7057918c981b53f920afef09b20afad
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
