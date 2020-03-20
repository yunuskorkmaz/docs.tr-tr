---
title: DbProviderFactory Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 0e2efd593019199ff641610b8602825cc60d4661
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149472"
---
# <a name="obtaining-a-dbproviderfactory"></a>DbProviderFactory Alma
Bir alma işlemi <xref:System.Data.Common.DbProviderFactory> sınıfa bir veri sağlayıcısı <xref:System.Data.Common.DbProviderFactories> hakkında bilgi aktarma içerir. Bu bilgilere dayanarak, <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> yöntem güçlü bir şekilde yazılan sağlayıcı fabrikası nı oluşturur. Örneğin, bir <xref:System.Data.SqlClient.SqlClientFactory>, "System.Data.SqlClient" olarak belirtilen sağlayıcı adı ile bir dize geçirebilirsiniz `GetFactory` oluşturmak için. Diğer aşırı yük `GetFactory` bir <xref:System.Data.DataRow>alır . Sağlayıcı fabrikasını oluşturduktan sonra, ek nesneler oluşturmak için yöntemlerini kullanabilirsiniz. Bazı yöntemler `SqlClientFactory` içerir <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>ve .  
  
> [!NOTE]
> .NET Framework <xref:System.Data.OracleClient.OracleClientFactory> <xref:System.Data.Odbc.OdbcFactory>ve <xref:System.Data.OleDb.OleDbFactory> sınıflar da benzer işlevsellik sağlar.  
  
## <a name="registering-dbproviderfactories"></a>DbProviderFactorys'in Kaydedilmesi  
 Fabrika tabanlı bir sınıfı destekleyen her .NET Framework veri sağlayıcısı, **machine.config** dosyasının yerel bilgisayardaki **DbProviderFactorys** bölümünde yapılandırma bilgilerini kaydeder. Aşağıdaki yapılandırma dosyası parçası için <xref:System.Data.SqlClient>sözdizimi ve biçimini gösterir.  
  
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
  
 **Değişmez** öznitelik, temel veri sağlayıcısını tanımlar. Bu üç bölümlü adlandırma sözdizimi, yeni bir fabrika oluştururken ve sağlayıcıyı bir uygulama yapılandırma dosyasında tanımlamak için de kullanılır, böylece sağlayıcı adı, ilişkili bağlantı dizesiyle birlikte çalışma zamanında alınabilir.  
  
## <a name="retrieving-provider-information"></a>Sağlayıcı Bilgilerini Alma  
 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> Yöntemi kullanarak yerel bilgisayara yüklenen tüm veri sağlayıcıları hakkında bilgi alabilirsiniz. Aşağıdaki tabloda açıklanan sütunları içeren <xref:System.Data.DataTable> adlandırılmış **DbProviderFactorys** döndürür.  
  
|Sütun ordinal|Sütun adı|Örnek çıktı|Açıklama|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Adı**|SqlClient Veri Sağlayıcısı|Veri sağlayıcısı için okunabilir ad|  
|1|**Açıklama**|.SqlServer için .Net Çerçeve Veri Sağlayıcısı|Veri sağlayıcısının okunabilir açıklaması|  
|2|**DeğişmezAd**|System.Data.SqlClient|Veri sağlayıcısına başvurmak için programlı olarak kullanılabilecek ad|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Nesneyi anında anımsamaya yetecek kadar bilgi içeren fabrika sınıfının tam nitelikli adı|  
  
 Bu, `DataTable` bir kullanıcının çalışma zamanında <xref:System.Data.DataRow> bir seçim yapabilmesini sağlamak için kullanılabilir. Seçili `DataRow` daha sonra güçlü <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> bir şekilde yazılan <xref:System.Data.Common.DbProviderFactory>bir yöntem oluşturmak için yönteme geçirilebilir. Seçili <xref:System.Data.DataRow> bir istenilen `GetFactory` `DbProviderFactory` nesneyi oluşturmak için yönteme geçirilebilir.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Yüklü Sağlayıcı Fabrika Sınıfları Listeleme  
 Bu örnek, yüklenilen sağlayıcılar <xref:System.Data.DataTable> hakkında bilgi içeren bir yöntemi nasıl döndürüleceklerini <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> gösterir. `DataTable`Kod, konsol penceresindeki her yüklü sağlayıcının bilgilerini görüntüleyen her satırda yinelenir.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Fabrika Bilgilerini Depolamak için Uygulama Yapılandırma Dosyalarını Kullanma  
 Fabrikalarla çalışmak için kullanılan tasarım deseni, sağlayıcı ve bağlantı dize bilgilerini bir uygulama yapılandırma dosyasında depolamayı gerektirir(örneğin, windows uygulaması için **app.config** ve ASP.NET bir uygulama için **web.config.**  
  
 Aşağıdaki yapılandırma dosyası parçası, SQL Server'daki Northwind veritabanına bağlantı için "NorthwindSQL" ve Access/Jet'teki Northwind veritabanına bağlantı için "NorthwindAccess" adlı iki bağlantı dizesini nasıl kaydedilebildiğini gösterir. **Değişmez** ad **sağlayıcıAdı** özniteliği için kullanılır.  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Sağlayıcı Adına Göre Bağlantı Dizesi Alma  
 Sağlayıcı fabrikası oluşturmak için, sağlayıcı adının yanı sıra bir bağlantı dizesi sağlamanız gerekir. Bu örnek, sağlayıcı adını değişmez biçiminde "*System.Data.ProviderName*" olarak geçirerek bir uygulama yapılandırma dosyasından bağlantı dizesi nasıl alınır gösterilmektedir. Kod, <xref:System.Configuration.ConnectionStringSettingsCollection>.. Bu başarı <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> döner; aksi `null` `Nothing` takdirde (Visual Basic'te). Bir sağlayıcı için birden çok giriş varsa, bulunan ilk giriş döndürülür. Daha fazla bilgi ve bağlantı dizeleri yapılandırma dosyalarından alma örnekleri için Bkz. [Bağlantı Dizeleri ve Yapılandırma Dosyaları.](connection-strings-and-configuration-files.md)  
  
> [!NOTE]
> `System.Configuration.dll` Kodun çalışması için başvuru gereklidir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>DbProviderFactory ve DbConnection oluşturma  
 Bu örnek, " <xref:System.Data.Common.DbProviderFactory> *System.Data.ProviderName*" biçiminde sağlayıcı adını ve bağlantı dizesini geçirerek bir ve <xref:System.Data.Common.DbConnection> nesnenin nasıl oluşturulup oluşturulabildiğini gösterir. Bir `DbConnection` nesne başarı yla döndürülür; `null` (Visual`Nothing` Basic'te) herhangi bir hata.  
  
 Kod `DbProviderFactory` arayarak <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>elde eder. Sonra <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> yöntem nesne <xref:System.Data.Common.DbConnection> oluşturur ve <xref:System.Data.Common.DbConnection.ConnectionString%2A> özellik bağlantı dizesine ayarlanır.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactories](dbproviderfactories.md)
- [Bağlantı Dizeleri](connection-strings.md)
- [Yapılandırma Sınıflarını Kullanma](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
