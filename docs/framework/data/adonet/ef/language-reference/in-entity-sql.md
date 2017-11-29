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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553b2037ef9b1eead3a3f4745d0cb6fdfcde27ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
  
 [NOT]  
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
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
