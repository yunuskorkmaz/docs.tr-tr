---
title: "MULTISET (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6389051ae1244a2a38699704c67217d9807fe7e4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="multiset-entity-sql"></a>MULTISET (varlık SQL)
Değerler listesinden bir çoklu küme örneği oluşturur. Çok KÜMELİ Oluşturucusu tüm değerleri uyumlu bir türü olmalıdır `T`. Boş multiset oluşturucular izin verilmiyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Geçerli tüm değerlerin listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 MULTISET türünden bir koleksiyona\<T >.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]üç tür oluşturucular sağlar: satır Oluşturucular, nesne oluşturucuları ve multiset (veya koleksiyon) oluşturucular. Daha fazla bilgi için bkz: [oluşturma türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).  
  
 Çok kümeli Oluşturucusu değerler listesinden bir çoklu küme örneği oluşturur. Oluşturucu tüm değerleri uyumlu bir türü olmalıdır.  
  
 Örneğin, aşağıdaki ifade tamsayıların çoklu küme oluşturur.  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  İç içe geçmiş çok kümeli değişmez değerler, yalnızca tek bir çok kümeli öğe kaydırma mutiset sahip olduğunda desteklenir; Örneğin, `{{1, 2, 3}}`. Birden çok çok kümeli öğe kaydırma multiset sahip olduğunda (örneğin, `{{1, 2}, {3, 4}}`), iç içe geçmiş çok kümeli değişmez değerler desteklenmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu MULTISET işleci değerler listesinden bir çoklu küme örneği oluşturmak için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma Türleri](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
