---
title: "Bir DbDataAdapter verilerle değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: fc821aeb1fb7812b3a858bf901e91ccc625f142a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Bir DbDataAdapter verilerle değiştirme
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Yöntemi bir <xref:System.Data.Common.DbProviderFactory> nesne size bir <xref:System.Data.Common.DbDataAdapter> Fabrika oluşturduğunuz sırada belirtilen temel alınan veri sağlayıcı için kesin türü belirtilmiş nesnesi. Daha sonra kullanabileceğiniz bir <xref:System.Data.Common.DbCommandBuilder> komutları eklemek için oluşturmak, güncelleştirmek ve verileri silmek bir <xref:System.Data.DataSet> bir veri kaynağına.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Bir DbDataAdapter ile veri alma  
 Bu örnek nasıl kesin türü belirtilmiş oluşturulduğunu gösteren `DbDataAdapter` bir sağlayıcı adı ve bağlantı dizesine dayalı. Kod kullanan <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> yöntemi <xref:System.Data.Common.DbProviderFactory> oluşturmak için bir <xref:System.Data.Common.DbConnection>. Ardından, kod kullanır <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> yöntemi oluşturmak için bir <xref:System.Data.Common.DbCommand> ayarlayarak verileri seçmek için kendi `CommandText` ve `Connection` özellikleri. Son olarak, kod oluşturur bir <xref:System.Data.Common.DbDataAdapter> kullanarak nesne <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> yöntemi ve kümelerini kendi `SelectCommand` özelliği. `Fill` Yöntemi `DbDataAdapter` verileri yükleyen bir <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Bir DbDataAdapter verilerle değiştirme  
 Bu örnek verilerde değişiklik yapmayı gösteren bir `DataTable` kullanarak bir <xref:System.Data.Common.DbDataAdapter> kullanarak bir <xref:System.Data.Common.DbCommandBuilder> veri kaynağında verileri güncelleştirmek için gerekli komutları oluşturmak için. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> , `DbDataAdapter` CustomerID ve şirket adı Müşteriler tablosundan alacak şekilde ayarlanmış. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Ayarlamak için kullanılan yöntemi <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> özelliği, <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> ayarlamak için kullanılan yöntemi <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> özelliği ve <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> yöntemi ayarlamak için kullanılır <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özelliği. Kod Customers tablosuna yeni bir satır ekler ve veri kaynağını güncelleştirir. Kod tanımlanan Müşteriler tablosu için birincil anahtar CustomerID arayarak eklenen satır ardından bulur. ŞirketAdı değiştirir ve veri kaynağını güncelleştirir. Son olarak, kod satırı siler.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>İşleme parametreleri  
 .NET Framework veri sağlayıcıları adlandırma ve parametreleri ve parametre yer tutucuları farklı belirterek işleyin. Bu sözdiziminin belirli veri kaynağı için aşağıdaki tabloda açıklandığı gibi özel olarak oluşturulmuştur.  
  
|Veri sağlayıcısı|Parametre adlandırma söz dizimi|  
|-------------------|-----------------------------|  
|`SqlClient`|Adlı parametre biçimde kullanır `@` *parametername*.|  
|`OracleClient`|Adlı parametre biçimde kullanır `:` *parmname* (veya *parmname*).|  
|`OleDb`|Bir soru işaretiyle gösterilen konumsal parametre işaretçileri kullanır (`?`).|  
|`Odbc`|Bir soru işaretiyle gösterilen konumsal parametre işaretçileri kullanır (`?`).|  
  
 Fabrika modeli parametreli oluşturmak için yararlı değildir `DbCommand` ve `DbDataAdapter` nesneleri. Veri sağlayıcınıza uyarlanmış parametrelerini oluşturmak üzere, kodunuzda dal gerekecektir.  
  
> [!IMPORTANT]
>  Sağlayıcıya özgü parametreler önleme tamamen doğrudan SQL deyimlerini oluşturmak için dize birleştirme kullanarak güvenlik nedenleriyle önerilmez. Dize birleştirme yerine parametrelerini kullanarak uygulamanızı SQL ekleme saldırılara karşı savunmasız bırakır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [DbProviderFactory Alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
