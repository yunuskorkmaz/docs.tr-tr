---
title: "ÜST (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9b1d3d1b07a349ab1a5efb4a7c41f9b9b34fc55f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="top-entity-sql"></a>ÜST (varlık SQL)
SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştiricisi izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir. TOP alt yan tümcesi, yalnızca ilk satır kümesini sorgu sonuç döndürülür belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Sayısal ifade döndürülecek satır sayısını belirtir. `n`tek bir sayısal dize veya tek bir parametre olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 TOP ifadesi tek sayısal sabit değer ya da tek bir parametre olması gerekir. Bir sabit değişmez değeri kullanılırsa, değişmez değer türü örtük olarak yükseltilebilir EDM.Int64 (bayt, int16, int32 veya Int64 veya EDM.Int64 için yükseltilebilir türü eşlendiği herhangi bir sağlayıcı türü) için olmalıdır ve değeri sıfırdan büyük veya sıfıra eşit olmalıdır. Aksi takdirde bir özel durum oluşturulur. Bir ifade olarak kullanılan bir parametre, parametre türü de EDM.Int64 için örtük olarak yükseltilebilir olmalıdır, ancak parametre değerlerini geç ilişkisindeki çünkü asıl parametre değerinin hiçbir doğrulama derleme sırasında olacaktır.  
  
 Sabit TOP ifadesi örneği verilmiştir:  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 Parametreli TOP ifadesi örneği verilmiştir:  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 Sorgu sıralanmış sürece üst belirleyici değildir. Belirleyici bir sonuç gerekiyorsa kullanın [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi. TOP ve SKIP/LIMIT karşılıklı olarak birbirini dışlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu üst sorgu sonuç döndürülecek üst bir satır belirlemek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SEÇİN](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [ATLA](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [SINIRI](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [SIRALAMA ÖLÇÜTÜ](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
