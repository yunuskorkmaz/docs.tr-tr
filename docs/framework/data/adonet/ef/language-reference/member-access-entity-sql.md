---
title: "biçimindeki telefon numarasıdır. (Üye erişimi) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 36699b403241e9a5496e722e81c833be0ed63101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="-member-access-entity-sql"></a>biçimindeki telefon numarasıdır. (Üye erişimi) (Varlık SQL)
Nokta işleci (.) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üye erişimi işleci. Üye erişimi işleci bir özelliği veya alanı yapısal kavramsal model türünün bir örneği, değeri elde etmek üzere kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Bir yapısal kavramsal model türünün bir örneği.  
  
 `identifier`  
 Bir özellik veya bir nesne örneğine ait alan.  
  
## <a name="remarks"></a>Açıklamalar  
 Nokta (.) işleci, karmaşık veya varlık türünün özelliklerini ayıklanması için benzer bir kaydın alanlarını ayıklamak için kullanılabilir. Örneğin, n türü adı türü kişi bir üyesidir ve p kişi türünde bir örnek ise, ardından p.n adı türünde bir değer döndüren bir yasal üye erişimi ifadesidir.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
