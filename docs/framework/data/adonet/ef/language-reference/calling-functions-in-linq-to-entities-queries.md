---
title: "LINQ to Entities sorgularında işlevleri çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6e50147d356ad9e389a87868205bb9b8b6b3e7b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nasıl yapılır: çağrı kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [Nasıl yapılır: çağrı veritabanı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [Nasıl yapılır: özel veritabanı işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [Nasıl yapılır: Model tarafından tanımlanan işlevler sorgularda çağırın](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [Nasıl yapılır: çağrı nesne yöntemleri olarak modeli tarafından tanımlanan İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [Kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [.edmx dosyasının genel bakış](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Nasıl yapılır: özel işlevler kavramsal modelde tanımlayın](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)
