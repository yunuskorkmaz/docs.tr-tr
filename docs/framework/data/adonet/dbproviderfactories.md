---
title: DbProviderFactories
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e8c6310b8ce164a60541dae030ce603bccd372e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dbproviderfactories"></a>DbProviderFactories
<xref:System.Data.Common> Ad alanı oluşturmak için sınıflar sağlar <xref:System.Data.Common.DbProviderFactory> belirli veri kaynakları ile çalışacak biçimde örnekleri. Oluştururken bir <xref:System.Data.Common.DbProviderFactory> örneği ve veri sağlayıcısı hakkında bilgi geçirmek `DbProviderFactory` onu sağlamış bilgileri tabanlı döndürmek için doğru kesin türü belirtilmiş bir bağlantı nesnesi belirleyebilirsiniz.  
  
 .NET Framework sürüm 4, veri sağlayıcıları gibi başlayan <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, ve <xref:System.Data.OracleClient> machine.config dosyasının, ancak özel artık listelenen sağlayıcıları devam listelenecek vardır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Fabrika modeline genel bakış](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 Fabrika tasarım deseni ve programlama arabirimi genel bakış sağlar.  
  
 [Bir DbProviderFactory alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 Yüklü veri sağlayıcıları listesi ve oluşturmak nasıl gösteren bir <xref:System.Data.Common.DbConnection> gelen bir `DbProviderFactory`.  
  
 [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 Nasıl oluşturulduğunu gösteren bir <xref:System.Data.Common.DbCommand> ve <xref:System.Data.Common.DbDataReader>ve kullanarak veri hataların nasıl işleneceğini <xref:System.Data.Common.DbException>.  
  
 [Bir DbDataAdapter verilerle değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 Nasıl kullanılacağını gösteren bir <xref:System.Data.Common.DbCommandBuilder> ile bir <xref:System.Data.Common.DbDataAdapter> almak ve veri değiştirmek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Alma ve ADO.NET veri değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
