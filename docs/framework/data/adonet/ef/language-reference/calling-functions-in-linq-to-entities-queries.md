---
title: LINQ to Entities Sorgularında Çağırma İşlevleri
description: EntityFunctions ve SqlFunctions sınıflarının Entity Framework bir parçası olarak kurallı ve veritabanı işlevlerine nasıl erişim sağlayakullandığını görmek için bu makaleleri kullanın.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: faa6406713592f10e5e7371cd73f29bec4b03b7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286863"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>LINQ to Entities Sorgularında Çağırma İşlevleri
Bu bölümdeki konular, LINQ to Entities sorgularda işlevlerin nasıl çağrılacağını açıklamaktadır.  
  
 <xref:System.Data.Objects.EntityFunctions>Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfları, Entity Framework bir parçası olarak kurallı ve veritabanı işlevlerine erişim sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: kurallı Işlevleri çağırma](how-to-call-canonical-functions.md) ve [nasıl yapılır: veritabanı işlevlerini çağırma](how-to-call-database-functions.md).  
  
 Özel bir işlevi çağırma işlemi üç temel adım gerektirir:  
  
1. Kavramsal modelinizde bir işlev tanımlayın veya depolama modelinizde bir işlev bildirin.  
  
2. Uygulamanıza bir yöntem ekleyin ve bunu ile modeldeki işlevle eşleyin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .  
  
3. İşlevi bir LINQ to Entities sorgusunda çağırın.  
  
 Daha fazla bilgi için bu bölümdeki konulara bakın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Kurallı İşlevler Çağırma](how-to-call-canonical-functions.md)  
  
 [Nasıl yapılır: Veritabanı İşlevleri Çağırma](how-to-call-database-functions.md)  
  
 [Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma](how-to-call-custom-database-functions.md)  
  
 [Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma](how-to-call-model-defined-functions-in-queries.md)  
  
 [Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
- [Kurallı İşlevler](canonical-functions.md)
- [. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Nasıl yapılır: kavramsal modelde özel Işlevleri tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
