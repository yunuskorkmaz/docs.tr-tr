---
title: "VARLIĞINDAKİ (SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d32e5012b4acbf0ecd6830f549de5dccf79bb38b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="in-entity-sql"></a>VARLIĞINDAKİ (SQL)
Bir değer bir koleksiyondaki herhangi bir değer eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Eşleştirilecek değerini döndüren herhangi bir geçerli ifadeler.  
  
 [ NOT ]  
 Belirleyen `Boolean` IN sonucunu tasarruflarını.  
  
 `expression`  
 Bir eşleşme için test etmek için bir koleksiyon döndürür herhangi geçerli ifade. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `value`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`değer koleksiyonda bulunursa; değer null ise null ya da koleksiyon null; Aksi takdirde `false`. NOT ın kullanarak inç sonuçlarını üzerindeki geçersiz kılar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu ın işleci bir değer bir koleksiyondaki herhangi bir değer eşleşip eşleşmediğini belirlemek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
