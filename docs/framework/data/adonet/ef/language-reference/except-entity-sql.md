---
title: (Varlık SQL) dışında
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32c8c418056231e98696eb8f4e9cb372d6c5740c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089464"
---
# <a name="except-entity-sql"></a>(Varlık SQL) dışında
Ayrıca sorgu ifadesinden EXCEPT işlecinin sağa döndürülmez EXCEPT işlecinin sol sorgu ifadesinden farklı değerleri koleksiyonunu döndürür. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `expression`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Başka bir sorgu ifadesinden döndürülen koleksiyon karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli ifade.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir koleksiyonu aynı türde veya ortak bir temel veya türetilmiş tür `expression`.  
  
## <a name="remarks"></a>Açıklamalar  
 DIŞINDA biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın. Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir. Aşağıdaki tablo önceliği gösterir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.  
  
|Önceliği|İşleçler|  
|----------------|---------------|  
|En yüksek|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||EXCEPT|  
|En düşük|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu EXCEPT işlecinin herhangi ayrı değerler koleksiyonu gelen iki sorgu ifadeleri döndürmek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
