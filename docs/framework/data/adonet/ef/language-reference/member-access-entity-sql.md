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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c90c908e567ac05f344292411978ff0c80919a65
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
