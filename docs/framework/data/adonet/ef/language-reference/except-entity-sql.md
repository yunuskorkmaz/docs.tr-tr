---
title: "(Varlık SQL) dışında"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de4455e997e0fc644fdc5bbef8ff52f84735d133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="except-entity-sql"></a>(Varlık SQL) dışında
Tüm farklı değerler koleksiyonu sorgu ifadesinden de sorgu ifadesinden EXCEPT işleneni sağındaki döndürülmez EXCEPT işleneni sola döndürür. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `expression`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyonu ile karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aynı türde veya ortak bir temel veya türetilmiş türde bir koleksiyonu `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 DIŞINDA biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir. Aşağıdaki tabloda önceliği gösterilmektedir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.  
  
|Önceliği|İşleçler|  
|----------------|---------------|  
|En yüksek|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||DIŞINDA|  
|En düşük|VAR<br /><br /> ÇAKIŞIYOR<br /><br /> DÜZLEŞTİRME<br /><br /> AYARLAMA|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu EXCEPT işleci gelen iki sorgu ifadeleri herhangi farklı değerler koleksiyonu döndürmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
