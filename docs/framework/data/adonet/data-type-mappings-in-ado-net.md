---
title: "ADO.NET veri türü eşlemeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 65f9d8a6182c5882a173a3a3733c1c0c220efbf6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-type-mappings-in-adonet"></a>ADO.NET veri türü eşlemeleri
.NET Framework nasıl türleri bildirilen kullanılan ve çalışma zamanı'nda yönetilen tanımlar ortak tür sistemi dayanır. Değer türleri ve türetilen tüm hangi başvuru türleri oluşur <xref:System.Object> temel türü. Açıkça belirtilmezse, bir veri kaynağı ile çalışırken, veri türü veri sağlayıcısı'ndan algılanır. Örneğin, bir <xref:System.Data.DataSet> nesnesidir herhangi belirli veri kaynağından bağımsız. Verileri bir `DataSet` bir veri kaynağından alınan ve değişiklikleri kullanarak veri kaynağına geri kaldı bir `DataAdapter`. Yani bir `DataAdapter` doldurur bir <xref:System.Data.DataTable> içinde bir `DataSet` sütunları sonuç veri türleri bir veri kaynağından alınan değerlerle `DataTable` olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri için belirli yerine türleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri veri kaynağına bağlanmak için kullanılan sağlayıcı.  
  
 Benzer şekilde, bir `DataReader` bir veri kaynağı, sonuçlanan değer arasında bir değer olan yerel bir değişkende depolanan döndürür bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü. Her ikisi için de `Fill` işlemlerini `DataAdapter` ve `Get` yöntemlerinin `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] döndürülen değerin türü olayla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı.  
  
 Çıkarsanan veri türüne bağlı olan yerine yazılan erişimci yöntemlerini kullanabilirsiniz `DataReader` belirli türde bir döndürülen değer bildiğinizde. Yazılı erişimci yöntemleri size daha iyi performans belirli bir olarak bir değer döndürerek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ek tür dönüştürme ihtiyacını ortadan kaldıran türü.  
  
> [!NOTE]
>  Null değerler için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcı veri türlerini temsil ettiği `DBNull.Value`.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server veri türü eşlemeleri](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.SqlClient>.  
  
 [OLE DB veri türü eşlemeleri](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.OleDb>.  
  
 [ODBC veri türü eşlemeleri](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.Odbc>.  
  
 [Oracle veri türü eşlemeleri](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.OracleClient>.  
  
 [Kayan nokta sayıları](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Geliştiriciler kayan nokta sayıları ile çalışırken sık karşılaştığınız sorunları açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server veri türleri ve ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Yapılandırma parametreleri ve parametre veri türleri](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Veritabanı şema bilgileri alınıyor](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Ortak tür sistemi](../../../../docs/standard/base-types/common-type-system.md)  
 [Türleri dönüştürme](http://msdn.microsoft.com/en-us/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
