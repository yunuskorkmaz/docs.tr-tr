---
title: LINQ to Entities Sorgularında Çağırma İşlevleri
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 6fa1a7204a91a62c30e8683c449cc2be44132b4f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312091"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>LINQ to Entities Sorgularında Çağırma İşlevleri
Bu bölümdeki konular, LINQ to Entities sorgularında işlevlerini açıklar.  
  
 <xref:System.Data.Objects.EntityFunctions> Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıflar, Entity Framework bir parçası olarak kurallı erişimi ve veritabanı işlevleri sunar. Daha fazla bilgi için [nasıl yapılır: Kurallı işlevler çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) ve [nasıl yapılır: Veritabanı işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Özel bir işlev çağırma işlemi üç temel adımları gerektirir:  
  
1. Kavramsal modelinizde bir fonksiyon tanımlayın veya depolama modelinizdeki bir işlev bildirir.  
  
2. Uygulamanız için bir yöntem ekleyin ve işlevine modeliyle eşlemek bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3. Bir LINQ to Entities sorgusunda işlevi çağırın.  
  
 Daha fazla bilgi için bu bölümdeki konular, bkz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Kurallı İşlevleri Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Nasıl yapılır: Veritabanı İşlevleri Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Nasıl yapılır: Sorgularda Model Tanımlı İşlevler Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Nasıl yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- [.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Nasıl yapılır: Kavramsal modelde özel işlevleri tanımlayın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
