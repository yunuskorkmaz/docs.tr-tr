---
title: Çakışma (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: f0c5d79b437ff06603ea10404357aa0b3270bc53
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150784"
---
# <a name="overlaps-entity-sql"></a>Çakışma (varlık SQL)
İki koleksiyon ortak öğeler sahip olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyon karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli ifade. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `expression`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` iki koleksiyon ortak öğeler varsa, Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlevsel olarak eşdeğerdir aşağıdaki ÇAKIŞAN sağlar:  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 ÇAKIŞAN biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir. Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu ÇAKIŞIYOR işleci belirler için iki koleksiyon ortak değerine sahip olup olmadığını kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu çalıştırma için şu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
