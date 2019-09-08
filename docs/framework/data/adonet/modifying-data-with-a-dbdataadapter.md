---
title: DbDataAdapter ile Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: cd1f5faa0efe141dc064f0150b94807b90e7e2b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794826"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter ile Verileri Değiştirme
Bir <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> <xref:System.Data.Common.DbDataAdapter> nesne yöntemi, fabrikanızı oluşturduğunuz sırada belirtilen temel alınan veri sağlayıcısına kesin olarak yazılmış bir nesne sağlar. <xref:System.Data.Common.DbProviderFactory> Daha sonra bir veri kaynağına <xref:System.Data.Common.DbCommandBuilder> veri <xref:System.Data.DataSet> eklemek, güncelleştirmek ve silmek için komut oluşturmak üzere bir kullanabilirsiniz.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>DbDataAdapter ile veri alma  
 Bu örnek, bir sağlayıcı adı ve bağlantı dizesi `DbDataAdapter` temelinde kesin bir tür oluşturmayı nasıl oluşturacağınızı gösterir. Kod, oluşturmak <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> içinyöntemini<xref:System.Data.Common.DbProviderFactory> kullanır. <xref:System.Data.Common.DbConnection> Daha sonra <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> kod, `CommandText` ve <xref:System.Data.Common.DbCommand> özellikleriniayarlayarakverileriseçmeküzerebiroluşturmakiçinyönteminikullanır.`Connection` Son olarak, kod <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> yöntemini kullanarak bir nesnesi oluşturur ve `SelectCommand` özelliğini ayarlar. Öğesinin yöntemi, verileri bir <xref:System.Data.DataTable>öğesine yükler.`DbDataAdapter` `Fill`  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter ile Verileri Değiştirme  
 Bu örnek, veri kaynağındaki verileri güncelleştirmek için gereken `DataTable` komutları oluşturmak <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbCommandBuilder> için kullanılarak kullanılarak kullanarak verileri nasıl değiştireceğiniz gösterilmektedir. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> ,MüşterilertablosundanCustomerIDveCompanyName'`DbDataAdapter` i almak üzere ayarlanır. <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> Yöntemi özelliği ayarlamak için kullanılır, yöntemi özelliği ayarlamak için kullanılır ve yöntemi <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özelliği ayarlamak için kullanılır. <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Kod, Müşteriler tablosuna yeni bir satır ekler ve veri kaynağını güncelleştirir. Daha sonra kod, müşteriler tablosu için tanımlanan birincil anahtar olan CustomerID üzerinde arayarak eklenen satırı bulur. CompanyName ' i değiştirir ve veri kaynağını güncelleştirir. Son olarak, kod satırı siler.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Parametreleri işleme  
 .NET Framework veri sağlayıcıları, adlandırma ve parametreleri ve parametre yer tutucuları farklı şekilde belirtmeyi işler. Bu sözdizimi, aşağıdaki tabloda açıklandığı gibi belirli bir veri kaynağına uyarlanmış olarak belirlenir.  
  
|Veri sağlayıcısı|Parametre adlandırma sözdizimi|  
|-------------------|-----------------------------|  
|`SqlClient`|Parametre adı olarak `@`adlandırılmış parametreleri *kullanır.*|  
|`OracleClient`|, *Parmname* (veya `:` *parmname*) biçiminde adlandırılmış parametreleri kullanır.|  
|`OleDb`|Bir soru işaretiyle (`?`) belirtilen Konumsal parametre işaretçilerini kullanır.|  
|`Odbc`|Bir soru işaretiyle (`?`) belirtilen Konumsal parametre işaretçilerini kullanır.|  
  
 Fabrika modeli parametreli `DbCommand` ve `DbDataAdapter` nesneler oluşturmak için yararlı değildir. Veri sağlayıcınıza uyarlanmış parametreler oluşturmak için kodunuzda dallandırma yapmanız gerekir.  
  
> [!IMPORTANT]
> Doğrudan SQL deyimlerini oluşturmak için dize birleştirmesini kullanarak sağlayıcıya özgü parametrelerin tamamen engellenmesinin güvenlik nedenleriyle önerilmez. Parametreler yerine dize birleştirme kullanmak, uygulamanızı SQL ekleme saldırılarına karşı savunmasız bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactories](dbproviderfactories.md)
- [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
