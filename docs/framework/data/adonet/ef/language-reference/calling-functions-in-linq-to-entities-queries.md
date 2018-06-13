---
title: LINQ to Entities sorgularında işlevleri çağırma
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 690f1a2cdcd8726d40a6627c1ceb05c9ae7e7fdd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760147"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>LINQ to Entities sorgularında işlevleri çağırma
Bu bölümdeki konular, LINQ to Entities sorgularında işlevlerini açıklar.  
  
 <xref:System.Data.Objects.EntityFunctions> Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfları, Entity Framework'ün bir parçası olarak erişim kurallı ve veritabanı işlevleri sağlar. Daha fazla bilgi için bkz [nasıl yapılır: çağrı kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) ve [nasıl yapılır: çağrı veritabanı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).  
  
 Özel bir işlev çağırma işlemi üç temel adımlar gerektirir:  
  
1.  Kavramsal modelde bir işlev tanımlayın veya depolama modelinizi işlevinde bildirin.  
  
2.  Uygulamanız için bir yöntem ekleyin ve modelle işlevinde Eşle bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3.  Bir LINQ to Entities sorgusunda işlevini çağırın.  
  
 Bu bölümdeki konular, daha fazla bilgi için bkz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Kurallı İşlevler Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Nasıl yapılır: Veritabanı İşlevleri Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Kurallı İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [.edmx dosyasının genel bakış](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Nasıl yapılır: özel işlevler kavramsal modelde tanımlayın](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
