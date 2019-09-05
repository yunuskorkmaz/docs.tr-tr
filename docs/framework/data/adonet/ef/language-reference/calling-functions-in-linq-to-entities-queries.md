---
title: LINQ to Entities Sorgularında Çağırma İşlevleri
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251260"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>LINQ to Entities Sorgularında Çağırma İşlevleri
Bu bölümdeki konular, LINQ to Entities sorgularda işlevlerin nasıl çağrılacağını açıklamaktadır.  
  
 <xref:System.Data.Objects.EntityFunctions> Ve<xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfları, Entity Framework bir parçası olarak kurallı ve veritabanı işlevlerine erişim sağlar. Daha fazla bilgi için [nasıl yapılır: Kurallı işlevleri](how-to-call-canonical-functions.md) çağırın ve [şunları yapın: Veritabanı Işlevlerini](how-to-call-database-functions.md)çağırın.  
  
 Özel bir işlevi çağırma işlemi üç temel adım gerektirir:  
  
1. Kavramsal modelinizde bir işlev tanımlayın veya depolama modelinizde bir işlev bildirin.  
  
2. Uygulamanıza bir yöntem ekleyin ve bunu ile <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>modeldeki işlevle eşleyin.  
  
3. İşlevi bir LINQ to Entities sorgusunda çağırın.  
  
 Daha fazla bilgi için bu bölümdeki konulara bakın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Kurallı Işlevleri çağırın](how-to-call-canonical-functions.md)  
  
 [Nasıl yapılır: Arama veritabanı Işlevleri](how-to-call-database-functions.md)  
  
 [Nasıl yapılır: Özel veritabanı Işlevlerini çağırma](how-to-call-custom-database-functions.md)  
  
 [Nasıl yapılır: Sorgularda model tanımlı Işlevleri çağırma](how-to-call-model-defined-functions-in-queries.md)  
  
 [Nasıl yapılır: Model tanımlı Işlevleri nesne yöntemleri olarak çağırma](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
- [Kurallı İşlevler](canonical-functions.md)
- [. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Nasıl yapılır: Kavramsal modelde özel Işlevleri tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
