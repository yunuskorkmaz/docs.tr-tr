---
title: DbProviderFactory Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: dd4bca48c35b9b636a96fe5d4a724272abc4f71d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934396"
---
# <a name="obtaining-a-dbproviderfactory"></a>DbProviderFactory Alma
Alma <xref:System.Data.Common.DbProviderFactory> işlemi, <xref:System.Data.Common.DbProviderFactories> sınıfına bir veri sağlayıcısı hakkında bilgi geçirmeyi içerir. Bu bilgilere bağlı olarak, <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> yöntemi türü kesin belirlenmiş bir sağlayıcı fabrikası oluşturur. Örneğin, oluşturmak <xref:System.Data.SqlClient.SqlClientFactory>için, sağlayıcı adı "System. `GetFactory` Data. SqlClient" olarak belirtilen bir dize geçirebilirsiniz. Diğer aşırı yüklemesi `GetFactory` bir <xref:System.Data.DataRow>alır. Sağlayıcı fabrikasını oluşturduktan sonra ek nesneler oluşturmak için yöntemlerini kullanabilirsiniz. Uygulamasının `SqlClientFactory` bazı yöntemleri, <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A> <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>ve içerir.<xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>  
  
> [!NOTE]
> .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>ve sınıflarıbenzerişlevleridesağlar.<xref:System.Data.OleDb.OleDbFactory>  
  
## <a name="registering-dbproviderfactories"></a>DbProviderFactory kaydı yapılıyor  
 Fabrika tabanlı bir sınıfı destekleyen her bir .NET Framework veri sağlayıcısı, yapılandırma bilgilerini yerel bilgisayardaki **Machine. config** dosyasının **DbProviderFactory** bölümünde kaydeder. Aşağıdaki yapılandırma dosyası parçasında için <xref:System.Data.SqlClient>sözdizimi ve biçimi gösterilmektedir.  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 **Sabit** öznitelik, temel alınan veri sağlayıcısını tanımlar. Bu üç parçalı adlandırma sözdizimi Ayrıca, yeni bir fabrika oluştururken ve sağlayıcı adının ilişkili bağlantı dizesiyle birlikte çalışma zamanında alınabilmesi için bir uygulama yapılandırma dosyasında sağlayıcıyı tanımlamak için de kullanılır.  
  
## <a name="retrieving-provider-information"></a>Sağlayıcı bilgileri alınıyor  
 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> Yöntemini kullanarak, yerel bilgisayarda yüklü olan tüm veri sağlayıcıları hakkında bilgi alabilirsiniz. Aşağıdaki tabloda açıklanan <xref:System.Data.DataTable> sütunları içeren adlandırılmış bir **DbProviderFactory** döndürür.  
  
|Sütun sırası|Sütun adı|Örnek çıkış|Açıklama|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Ad**|SqlClient Veri Sağlayıcısı|Veri sağlayıcısı için okunabilir ad|  
|1\.|**Açıklama**|SqlServer için .NET Framework Veri Sağlayıcısı|Veri sağlayıcısının okunabilir açıklaması|  
|2|**InvariantName**|System. Data. SqlClient|Veri sağlayıcısına başvurmak için programlı olarak kullanılabilecek ad|  
|3|**AssemblyQualifiedName**|System. Data. SqlClient. SqlClientFactory, System. Data, Version = 2.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089|Nesneyi başlatmak için yeterli bilgi içeren fabrika sınıfının tam adı|  
  
 Bu `DataTable` , bir kullanıcının çalışma zamanında <xref:System.Data.DataRow> seçmesini sağlamak için kullanılabilir. Daha sonra, kesin bir tür <xref:System.Data.Common.DbProviderFactory>oluşturmak için <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> bu yönteme geçirilebilir. `DataRow` İstenen `GetFactory` <xref:System.Data.DataRow> nesneyioluşturmakiçinbirseçili`DbProviderFactory` olan yönteme geçirilebilir.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Yüklü sağlayıcı fabrikası sınıflarını listeleme  
 Bu örnek, <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> yüklü sağlayıcılar hakkında içeren bir <xref:System.Data.DataTable> bilgi döndürmek için yönteminin nasıl kullanılacağını gösterir. Kod, konsol penceresinde her yüklü sağlayıcı için `DataTable`bilgileri görüntüleyerek içindeki her bir satır boyunca yinelenir.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Fabrika bilgilerini depolamak için uygulama yapılandırma dosyalarını kullanma  
 Fabrikalarla birlikte çalışmak için kullanılan tasarım deseninin, sağlayıcı ve bağlantı dizesi bilgilerinin bir Windows uygulaması için **app. config** ve bir ASP.NET uygulaması için **Web. config** gibi bir uygulama yapılandırma dosyasında depolanması gerekir.  
  
 Aşağıdaki yapılandırma dosyası parçası, "NorthwindSQL" adlı iki bağlantı dizesinin, SQL Server ' deki Northwind veritabanına bağlantı için nasıl kaydedileceğini ve Access/Jet 'teki Northwind veritabanına bağlantı için "NorthwindAccess" olduğunu gösterir. **Sabit** adı **ProviderName** özniteliği için kullanılır.  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Sağlayıcı adına göre bir bağlantı dizesi alınıyor  
 Bir sağlayıcı fabrikası oluşturmak için, sağlayıcı adının yanı sıra bir bağlantı dizesi sağlamanız gerekir. Bu örnek, sağlayıcı adını "*System. Data. ProviderName*" sabit biçiminde geçirerek bir uygulama yapılandırma dosyasından bağlantı dizesinin nasıl alınacağını gösterir. Kod üzerinden <xref:System.Configuration.ConnectionStringSettingsCollection>yinelenir. Başarı <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> durumunda döndürür; Aksi takdirde `null` (`Nothing` Visual Basic). Bir sağlayıcı için birden çok giriş varsa, bulunan ilk değer döndürülür. Yapılandırma dosyalarından bağlantı dizelerini alma hakkında daha fazla bilgi ve örnek için bkz. [bağlantı dizeleri ve yapılandırma dosyaları](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
> Kodun çalışması için `System.Configuration.dll` bir başvuru gereklidir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>DbProviderFactory ve DbConnection oluşturma  
 Bu örnek, sağlayıcı adını " <xref:System.Data.Common.DbProviderFactory> *System. Data. ProviderName*" biçiminde geçirerek ve bir bağlantı dizesinde bir ve <xref:System.Data.Common.DbConnection> nesnesi oluşturmayı gösterir. Başarılı `DbConnection` olduğunda bir nesne döndürülür; `null` (`Nothing` Visual Basic), herhangi bir hata üzerinde.  
  
 Kodu çağırarak `DbProviderFactory` <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>öğesini alır. <xref:System.Data.Common.DbConnection> Sonra Yöntem nesneyi oluşturur ve <xref:System.Data.Common.DbConnection.ConnectionString%2A> özelliği bağlantı dizesine ayarlanır. <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)
- [Yapılandırma sınıflarını kullanma](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
