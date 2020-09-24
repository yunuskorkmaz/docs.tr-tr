---
title: DbDataAdapter ile Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 5272a53ae0b3ac1888d01dc2a59778c6c7231619
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150771"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter ile Verileri Değiştirme

<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A>Bir nesne yöntemi, <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbDataAdapter> fabrikanızı oluşturduğunuz sırada belirtilen temel alınan veri sağlayıcısına kesin olarak yazılmış bir nesne sağlar. Daha sonra bir <xref:System.Data.Common.DbCommandBuilder> veri kaynağına veri eklemek, güncelleştirmek ve silmek için komut oluşturmak üzere bir kullanabilirsiniz <xref:System.Data.DataSet> .  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>DbDataAdapter ile veri alma  

 Bu örnek `DbDataAdapter` , bir sağlayıcı adı ve bağlantı dizesi temelinde kesin bir tür oluşturmayı nasıl oluşturacağınızı gösterir. Kod, <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> <xref:System.Data.Common.DbProviderFactory> oluşturmak için yöntemini kullanır <xref:System.Data.Common.DbConnection> . Daha sonra kod, <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> <xref:System.Data.Common.DbCommand> ve özelliklerini ayarlayarak verileri seçmek üzere bir oluşturmak için yöntemini kullanır `CommandText` `Connection` . Son olarak, kod <xref:System.Data.Common.DbDataAdapter> yöntemini kullanarak bir nesnesi oluşturur <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> ve `SelectCommand` özelliğini ayarlar. `Fill`Öğesinin yöntemi, `DbDataAdapter` verileri bir öğesine yükler <xref:System.Data.DataTable> .  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter ile Verileri Değiştirme  

 Bu örnek `DataTable` <xref:System.Data.Common.DbDataAdapter> , veri <xref:System.Data.Common.DbCommandBuilder> kaynağındaki verileri güncelleştirmek için gereken komutları oluşturmak için kullanılarak kullanılarak kullanarak verileri nasıl değiştireceğiniz gösterilmektedir. , <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> `DbDataAdapter` Müşteriler tablosundan CustomerID ve CompanyName ' i almak üzere ayarlanır. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A>Yöntemi özelliği ayarlamak için kullanılır <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> , <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> yöntemi özelliği ayarlamak için kullanılır <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> ve <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> yöntemi özelliği ayarlamak için kullanılır <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> . Kod, Müşteriler tablosuna yeni bir satır ekler ve veri kaynağını güncelleştirir. Daha sonra kod, müşteriler tablosu için tanımlanan birincil anahtar olan CustomerID üzerinde arayarak eklenen satırı bulur. CompanyName ' i değiştirir ve veri kaynağını güncelleştirir. Son olarak, kod satırı siler.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Parametreleri işleme  

 .NET Framework veri sağlayıcıları, adlandırma ve parametreleri ve parametre yer tutucuları farklı şekilde belirtmeyi işler. Bu sözdizimi, aşağıdaki tabloda açıklandığı gibi belirli bir veri kaynağına uyarlanmış olarak belirlenir.  
  
|Veri sağlayıcısı|Parametre adlandırma sözdizimi|  
|-------------------|-----------------------------|  
|`SqlClient`|Parametre adı olarak adlandırılmış parametreleri kullanır `@` *parametername*.|  
|`OracleClient`|, `:` *Parmname* (veya *parmname*) biçiminde adlandırılmış parametreleri kullanır.|  
|`OleDb`|Bir soru işaretiyle () belirtilen Konumsal parametre işaretçilerini kullanır `?` .|  
|`Odbc`|Bir soru işaretiyle () belirtilen Konumsal parametre işaretçilerini kullanır `?` .|  
  
 Fabrika modeli parametreli ve nesneler oluşturmak için yararlı değildir `DbCommand` `DbDataAdapter` . Veri sağlayıcınıza uyarlanmış parametreler oluşturmak için kodunuzda dallandırma yapmanız gerekir.  
  
> [!IMPORTANT]
> Doğrudan SQL deyimlerini oluşturmak için dize birleştirmesini kullanarak sağlayıcıya özgü parametrelerin tamamen engellenmesinin güvenlik nedenleriyle önerilmez. Parametreler yerine dize birleştirme kullanmak, uygulamanızı SQL ekleme saldırılarına karşı savunmasız bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactories](dbproviderfactories.md)
- [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
