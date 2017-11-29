---
title: "ADO.NET veri kaynağına bağlanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0d21c571b659e9d7aef65893db18b034d614e2af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET veri kaynağına bağlanma
ADO.NET kullandığınız bir **bağlantı** bağlantı dizesinde gerekli kimlik doğrulama bilgileri sağlayarak bir özel veri kaynağına bağlanmak için nesne. **Bağlantı** kullandığınız nesne veri kaynağı türüne bağlıdır.  
  
 .NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir <xref:System.Data.Common.DbConnection> nesnesi: OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbConnection> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlConnection> nesnesi. NET Framework veri sağlayıcısı için ODBC içeren bir <xref:System.Data.Odbc.OdbcConnection> nesne ve Oracle için .NET Framework veri sağlayıcısı içeren bir <xref:System.Data.OracleClient.OracleConnection> nesnesi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı oluşturma](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Nasıl kullanılacağını açıklar bir **bağlantı** bir veri kaynağı bağlantı kurmak için nesne.  
  
 [Bağlantı olayları](../../../../docs/framework/data/adonet/connection-events.md)  
 Nasıl kullanılacağını açıklar bir **InfoMessage** bilgilendirici iletileri bir veri kaynağından veri almak için olay.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Bağlantı havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Komutları ve parametreleri](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapters ve DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [İşlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
