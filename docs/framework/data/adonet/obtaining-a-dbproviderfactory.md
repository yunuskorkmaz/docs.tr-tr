---
title: DbProviderFactory alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: daaa93c4da16ac67b7f7018fdafdc2b2d9f0784a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692788"
---
# <a name="obtaining-a-dbproviderfactory"></a>DbProviderFactory alma
Alma işlemi bir <xref:System.Data.Common.DbProviderFactory> geçirme için bir veri sağlayıcısı hakkında bilgi içerir <xref:System.Data.Common.DbProviderFactories> sınıfı. Bu bilgilere göre <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> yöntemi, kesin türü belirtilmiş sağlayıcı üreteci oluşturur. Örneğin, oluşturmak için bir <xref:System.Data.SqlClient.SqlClientFactory>, geçirebilirsiniz `GetFactory` "System.Data.SqlClient" Belirtilen sağlayıcı adı olan bir dize. Bir aşırı yüklemesini `GetFactory` götüren bir <xref:System.Data.DataRow>. Sağlayıcı üreteci oluşturduktan sonra ek nesneler oluşturmak için yöntemlerini kullanabilirsiniz. Yöntemlerinin bazılarını bir `SqlClientFactory` dahil <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, ve <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, ve <xref:System.Data.OleDb.OleDbFactory> sınıfları da benzer bir işlevsellik sağlar.  
  
## <a name="registering-dbproviderfactories"></a>DbProviderFactories kaydediliyor  
 Fabrika tabanlı bir sınıf destekleyen her .NET Framework veri sağlayıcısı yapılandırma bilgilerini kaydeder **DbProviderFactories** bölümünü **machine.config** dosyasını yerel bilgisayarda. Aşağıdaki yapılandırma dosyası parçası söz dizimi ve biçimini gösterir <xref:System.Data.SqlClient>.  
  
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
  
 **Sabit** özniteliğini tanımlayan temel alınan veri sağlayıcısı. Bu üç bölümlük sözdizimini, ayrıca yeni fabrikası oluştururken ve sağlayıcı adı, ilişkili bağlantı dizesini, birlikte çalışma zamanında alınabilmesi için bir uygulama yapılandırma dosyasında sağlayıcının tanımlamak için kullanılır.  
  
## <a name="retrieving-provider-information"></a>Sağlayıcı bilgileri alınıyor  
 Tüm kullanarak yerel bilgisayarda yüklü veri sağlayıcıları hakkında bilgi alabilirsiniz <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> yöntemi. Döndürür bir <xref:System.Data.DataTable> adlı **DbProviderFactories** aşağıdaki tabloda açıklanan sütunları içerir.  
  
|Sütun sırası|Sütun adı|Örnek çıktı|Açıklama|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Ad**|SqlClient veri sağlayıcısı|Okunabilir veri sağlayıcısı adı|  
|1.|**Açıklama**|SQL Server için .net framework veri sağlayıcısı|Veri sağlayıcısı okunabilir açıklaması|  
|2|**Invariantname**|System.Data.SqlClient|Program aracılığıyla veri sağlayıcısına başvurmak için kullanılan ad|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Nesne örneği oluşturmak için yeterli bilgi içerdiğinden Fabrika sınıfının tam adı|  
  
 Bu `DataTable` seçmesini etkinleştirmek için kullanılan bir <xref:System.Data.DataRow> çalışma zamanında. Seçili `DataRow` ardından geçirilebilir <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> türü kesin belirlenmiş yöntemini <xref:System.Data.Common.DbProviderFactory>. Seçili <xref:System.Data.DataRow> geçirilebilir `GetFactory` istenen yöntemini `DbProviderFactory` nesne.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Yüklü sağlayıcı üreteci sınıfları listeleme  
 Bu örnek nasıl kullanılacağını gösterir <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> döndürülecek yöntemi bir <xref:System.Data.DataTable> yüklü sağlayıcıları hakkında bilgi içeren. Her satırda kod gezinir `DataTable`, konsol penceresinde her yüklü sağlayıcısının bilgilerini görüntüleme.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Factory bilgileri Store için uygulama yapılandırma dosyaları kullanma  
 Fabrikaları ile çalışmak için kullanılan tasarım deseni kapsar sağlayıcısı ve bağlantı dizesi bilgileri gibi bir uygulama yapılandırma dosyasında saklamak **app.config** Windows uygulaması ve **web.config**  ASP.NET uygulaması için.  
  
 Aşağıdaki yapılandırma dosyası parçası iki adlandırılmış bağlantı dizesini kaydetmek nasıl SQL Server Northwind veritabanına bir bağlantı için "NorthwindSQL" ve "NorthwindAccess" erişim/Jet Northwind veritabanına bir bağlantı gösterir. **Sabit** adı için kullanılan **providerName** özniteliği.  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Sağlayıcı adı ile bir bağlantı dizesini alma  
 Bir sağlayıcı üreteci oluşturabilmek için bir bağlantı dizesi, hem de sağlayıcı adı sağlamanız gerekir. Bu örnek, sağlayıcı adı sabit bir biçimde geçirerek bir uygulama yapılandırma dosyasından bağlantı dizesini almak nasıl gösterir. "*System.Data.ProviderName*". Kod gezinir <xref:System.Configuration.ConnectionStringSettingsCollection>. Döndürür <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> başarı; Aksi takdirde `null` (`Nothing` Visual Basic'te). Sağlayıcı için birden çok girişi varsa, ilk döndürülür. Daha fazla bilgi ve örnek bağlantı dizeleri yapılandırma dosyalarından alma için bkz. [bağlantı dizeleri ve yapılandırma dosyalarını](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Bir başvuru `System.Configuration.dll` kodu çalıştırmak için gereklidir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>DbProviderFactory ve DbConnection oluşturma  
 Bu örnek nasıl oluşturulacağını gösterir. bir <xref:System.Data.Common.DbProviderFactory> ve <xref:System.Data.Common.DbConnection> geçirerek sağlayıcı adı biçiminde nesne "*System.Data.ProviderName*" ve bir bağlantı dizesi. A `DbConnection` başarı; nesne döndürülür `null` (`Nothing` Visual Basic'te) herhangi bir hata.  
  
 Kod alır `DbProviderFactory` çağırarak <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Ardından <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> yöntemi oluşturur <xref:System.Data.Common.DbConnection> nesne ve <xref:System.Data.Common.DbConnection.ConnectionString%2A> özelliği bağlantı dizesine ayarlayın.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)
- [Yapılandırma sınıflarını kullanma](https://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
