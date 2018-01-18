---
title: "SQL Server ikili ve değeri büyük veri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5ce85e61ac001ec07c14cebbc8d07e6c031498fc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server ikili ve değeri büyük veri
SQL Server sağlar `max` depolama kapasitesini genişletir belirleyici `varchar`, `nvarchar`, ve `varbinary` veri türleri. `varchar(max)`, `nvarchar(max)`, ve `varbinary(max)` toplu olarak adlandırılır *büyük değer veri türleri*. En fazla 2 depolamak için büyük değer veri türleri kullanabilirsiniz ^ 31-1 veri baytı sayısı.  
  
 SQL Server 2008 dosya sisteminde veritabanında depolanan büyük değer verilerinin vererek FILESTREAM öznitelik, bir veri türü değil, ancak bunun yerine bir sütuna, tanımlı bir öznitelik tanıtır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ADO.NET İçinde Büyük Değerli (Maks) Verileri Değiştirme](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Büyük değer veri türleri ile çalışmak açıklar.  
  
 [FILESTREAM Verileri](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 FILESTREAM özniteliği ile SQL Server 2008'de depolanan değeri büyük veri ile nasıl çalışılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET’te SQL Server Veri İşlemleri](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
