---
title: DbDataAdapter ile Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 3038e35947cd8f97266d374a367a77380df440dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158879"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter ile Verileri Değiştirme
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Yöntemi bir <xref:System.Data.Common.DbProviderFactory> nesne size bir <xref:System.Data.Common.DbDataAdapter> Fabrika oluşturduğunuz sırada belirtilen temel alınan veri sağlayıcısı için kesin belirlenmiş bir nesne. Daha sonra kullanabileceğiniz bir <xref:System.Data.Common.DbCommandBuilder> komutları eklemek için oluşturmak için güncelleştirme ve verileri silme bir <xref:System.Data.DataSet> bir veri kaynağı.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>DbDataAdapter ile verileri alınıyor  
 Bu örnek, türü kesin belirlenmiş oluşturma işlemini gösterir `DbDataAdapter` sağlayıcı adı ve bağlantı dizesini temel alan. Kod <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> yöntemi <xref:System.Data.Common.DbProviderFactory> oluşturmak için bir <xref:System.Data.Common.DbConnection>. Ardından, kod kullanır <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> yöntemi oluşturmak için bir <xref:System.Data.Common.DbCommand> ayarlayarak verileri seçmek için kendi `CommandText` ve `Connection` özellikleri. Son olarak, kod oluşturur bir <xref:System.Data.Common.DbDataAdapter> kullanarak nesne <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> yöntemi ve kümeleri kendi `SelectCommand` özelliği. `Fill` Yöntemi `DbDataAdapter` yükler verileri bir <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>DbDataAdapter ile Verileri Değiştirme  
 Bu örnek verilerde değişiklik yapmayı gösteren bir `DataTable` kullanarak bir <xref:System.Data.Common.DbDataAdapter> kullanarak bir <xref:System.Data.Common.DbCommandBuilder> veri kaynağındaki verileri güncelleştirmek için gereken komutlarını oluşturmak için. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> , `DbDataAdapter` CustomerID ve CompanyName Müşteriler tablosundan almak için ayarlanır. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Yöntemi ayarlamak için kullanılır <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> özelliği <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> yöntemi ayarlamak için kullanılır <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> özelliği ve <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> yöntemi ayarlamak için kullanılan <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> özelliği. Bu kod müşterilerin tabloya yeni satır ekler ve veri kaynağını güncelleştirir. Kodu daha sonra eklenen satır Müşteriler tablosu için birincil anahtar tanımlı CustomerID arayarak bulur. CompanyName değiştirir ve veri kaynağını güncelleştirir. Son olarak, kod satırı siler.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>İşlem parametreleri  
 .NET Framework veri sağlayıcıları adlandırma ve parametreleri ve parametre yer tutucuları farklı belirterek işleyin. Bu sözdizimi, aşağıdaki tabloda açıklandığı gibi belirli veri kaynağına uyarlanmıştır.  
  
|Veri sağlayıcısı|Parametre adlandırma söz dizimi|  
|-------------------|-----------------------------|  
|`SqlClient`|Adlı parametreleri biçimde `@` *parametername*.|  
|`OracleClient`|Adlı parametreleri biçimde `:` *parmname* (veya *parmname*).|  
|`OleDb`|Bir soru işaretiyle gösterilen konumsal parametre işareti kullanır (`?`).|  
|`Odbc`|Bir soru işaretiyle gösterilen konumsal parametre işareti kullanır (`?`).|  
  
 Fabrika modeline parametreli oluşturmak için yararlı değildir `DbCommand` ve `DbDataAdapter` nesneleri. Kodunuzda, veri sağlayıcısı için uyarlanmış parametreleri oluşturmak için dal gerekecektir.  
  
> [!IMPORTANT]
>  Sağlayıcıya özgü parametreler önleme tamamen doğrudan SQL deyimlerini oluşturmak için dize birleştirme kullanarak güvenlik nedenleriyle önerilmez. Dize birleştirme yerine parametreleri kullanarak uygulamanızı SQL ekleme saldırılarına karşı savunmasız bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [DbProviderFactory Alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
