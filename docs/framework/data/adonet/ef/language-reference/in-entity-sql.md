---
title: VARLIKTAKİ (SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: f4fa8cbc07513321e59b93503b59af172c0a6f05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211328"
---
# <a name="in-entity-sql"></a>VARLIKTAKİ (SQL)
Değer bir koleksiyondaki herhangi bir değer ile eşleşip eşleşmediğini belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  
 `value`  
 Eşleştirilecek değer döndüren herhangi bir geçerli ifade.  
  
 [NOT]  
 Belirten `Boolean` IN sonucu tasarruflarını.  
  
 `expression`  
 Test etmek için bir eşleşme için koleksiyonu döndüren herhangi bir geçerli ifade. Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş tür olarak olmalıdır `value`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true` değer koleksiyonda bulunursa; değer null ise null ya da koleksiyonu null; Aksi takdirde, `false`. NOT ın kullanarak inç sonuçlarını geçersiz hale getirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusu ın işleci bir değer bir koleksiyondaki herhangi bir değer ile eşleşip eşleşmediğini belirlemek için kullanır. Sorgu, AdventureWorks satış modelini temel alıyor. Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:  
  
1.  Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
