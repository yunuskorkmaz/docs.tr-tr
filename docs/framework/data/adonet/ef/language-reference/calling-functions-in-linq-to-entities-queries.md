---
title: LINQ to Entities sorgularında çağırma işlevleri
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 012f55113cbea00c95c92712d640313a960ef8ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542724"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>LINQ to Entities sorgularında çağırma işlevleri
Bu bölümdeki konular, LINQ to Entities sorgularında işlevlerini açıklar.  
  
 <xref:System.Data.Objects.EntityFunctions> Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıflar, Entity Framework bir parçası olarak kurallı erişimi ve veritabanı işlevleri sunar. Daha fazla bilgi için [nasıl yapılır: Kurallı işlevler çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) ve [nasıl yapılır: Veritabanı işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Özel bir işlev çağırma işlemi üç temel adımları gerektirir:  
  
1.  Kavramsal modelinizde bir fonksiyon tanımlayın veya depolama modelinizdeki bir işlev bildirir.  
  
2.  Uygulamanız için bir yöntem ekleyin ve işlevine modeliyle eşlemek bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Bir LINQ to Entities sorgusunda işlevi çağırın.  
  
 Daha fazla bilgi için bu bölümdeki konular, bkz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Kurallı işlevler çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Nasıl yapılır: Veritabanı işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Nasıl yapılır: Özel veritabanı işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Nasıl yapılır: Sorgularda model tanımlı işlevler çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Nasıl yapılır: Model tanımlı işlevleri nesne yöntemleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- [.edmx dosyasını genel bakış](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)
- [Nasıl yapılır: Kavramsal modelde özel işlevleri tanımlayın](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
