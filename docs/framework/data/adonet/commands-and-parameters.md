---
title: "Komutları ve parametreleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e1bfd3e88df4bd90cbcebfa645c2a50159f836db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="commands-and-parameters"></a>Komutları ve parametreleri
Bir veri kaynağına bağlantı kurulduktan sonra komutları yürütün ve sonuçları kullanarak veri kaynağının dönmek bir <xref:System.Data.Common.DbCommand> nesnesi. Komut oluşturuculardan birine çalıştığınız .NET Framework veri sağlayıcısı kullanarak bir komut oluşturabilirsiniz. Oluşturucular, veri kaynağında yürütmek için bir SQL deyimi gibi isteğe bağlı bağımsız değişkenler gerçekleştirebileceğiniz bir <xref:System.Data.Common.DbConnection> nesnesi veya bir <xref:System.Data.Common.DbTransaction> nesnesi. Bu nesneler komutu özelliklerini de yapılandırabilirsiniz. Belirli bir bağlantısı kullanmak için bir komut oluşturabilirsiniz <xref:System.Data.Common.DbConnection.CreateCommand%2A> yöntemi bir `DbConnection` nesnesi. Komutu tarafından yürütülen SQL deyimi kullanılarak yapılandırılabilir <xref:System.Data.Common.DbCommand.CommandText%2A> özelliği.  
  
 .NET Framework ile dahil her .NET Framework veri sağlayıcısı sahip bir `Command` nesnesi. OLE DB için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.OleDb.OleDbCommand> nesnesi, SQL Server için .NET Framework veri sağlayıcısı içerir bir <xref:System.Data.SqlClient.SqlCommand> nesne ODBC için .NET Framework veri sağlayıcısı içeren bir <xref:System.Data.Odbc.OdbcCommand> nesne ve .NET Framework Oracle için veri sağlayıcı içeren bir <xref:System.Data.OracleClient.OracleCommand> nesnesi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir komutu yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)  
 ADO.NET açıklar `Command` nesne ve nasıl sorgular ve bir veri kaynağına karşı komutları yürütmek için kullanılır.  
  
 [Yapılandırma parametreleri ve parametre veri türleri](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 İle çalışmayı açıklar `Command` yönü, veri türleri ve parametre söz dizimi dahil parametreleri.  
  
 [Komutları CommandBuilders ile oluşturma](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 Komut oluşturucuları için INSERT, UPDATE ve DELETE komutları otomatik olarak oluşturmak için nasıl kullanılacağını açıklar bir `DataAdapter` tek tablo SELECT komutu sahip.  
  
 [Tek bir değer veritabanından alma](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 Nasıl kullanılacağını açıklar `ExecuteScalar` yöntemi bir `Command` nesnesi bir veritabanından döndürdüğünüz tek bir değer.  
  
 [Verileri değiştirmek için komutları kullanarak](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 Bir veri sağlayıcısı saklı yordamları veya veri tanım dili (DDL) deyimlerini yürütmek için nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Bir veri kaynağına bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
