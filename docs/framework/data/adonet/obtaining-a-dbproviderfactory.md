---
title: Bir DbProviderFactory alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 9e9cf91559fe164fc42d5f9532428310fa1b16ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759471"
---
# <a name="obtaining-a-dbproviderfactory"></a>Bir DbProviderFactory alma
Alma işlemi bir <xref:System.Data.Common.DbProviderFactory> bir veri sağlayıcısı hakkında bilgi geçirilmesi ile ilgilidir <xref:System.Data.Common.DbProviderFactories> sınıfı. Bu bilgilere göre <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> yöntemi, kesin türü belirtilmiş sağlayıcı üreteci oluşturur. Örneğin, oluşturmak için bir <xref:System.Data.SqlClient.SqlClientFactory>, geçirebilirsiniz `GetFactory` "System.Data.SqlClient" Belirtilen sağlayıcı adına sahip bir dize. Bir aşırı yüklemesini `GetFactory` geçen bir <xref:System.Data.DataRow>. Sağlayıcı fabrikası oluşturduktan sonra ek nesneler oluşturmak için yöntemlerini kullanabilirsiniz. Bazı yöntemlerinden birini bir `SqlClientFactory` dahil <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, ve <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, ve <xref:System.Data.OleDb.OleDbFactory> sınıfları da benzer bir işlevsellik sağlar.  
  
## <a name="registering-dbproviderfactories"></a>DbProviderFactories kaydetme  
 Yapılandırma bilgilerini Fabrika tabanlı sınıfı destekleyen her .NET Framework veri sağlayıcısı kaydeder **DbProviderFactories** bölümünü **machine.config** dosyasını yerel bilgisayarda. Aşağıdaki yapılandırma dosyası parça biçimini ve sözdizimini gösterir <xref:System.Data.SqlClient>.  
  
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
  
 **Değişmez** özniteliği temel alınan veri sağlayıcı tanımlar. Bu üç bölümlük sözdizimini, yeni bir Fabrika oluştururken ve böylece sağlayıcı adı, ilişkili bağlantı dizesi ile birlikte çalışma zamanında alınabilmesi için bir uygulama yapılandırma dosyasında sağlayıcının tanımlamak için de kullanılır.  
  
## <a name="retrieving-provider-information"></a>Sağlayıcı bilgileri alınıyor  
 Tüm kullanarak yerel bilgisayarda yüklü veri sağlayıcıları hakkında bilgi alabilirsiniz <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> yöntemi. Döndürdüğü bir <xref:System.Data.DataTable> adlı **DbProviderFactories** aşağıdaki tabloda açıklanan sütunları içerir.  
  
|Sütun sırası|Sütun adı|Örnek çıktı|Açıklama|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Ad**|SqlClient veri sağlayıcısı|Veri sağlayıcısı için okunabilir adı|  
|1.|**Açıklama**|SqlServer için .net framework veri sağlayıcısı|Veri sağlayıcısı okunabilir açıklaması|  
|2|**InvariantName**|System.Data.SqlClient|Program aracılığıyla veri sağlayıcısı başvurmak için kullanılabilir adı|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, sürüm 2.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089|Nesne örneği oluşturmak için yeterli bilgiye sahip Fabrika sınıfın tam adı|  
  
 Bu `DataTable` seçmek bir kullanıcı etkinleştirmek için kullanılan bir <xref:System.Data.DataRow> çalışma zamanında. Seçili `DataRow` için geçirilebilir <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> kesin türü belirtilmiş oluşturmak için yöntemi <xref:System.Data.Common.DbProviderFactory>. Seçili <xref:System.Data.DataRow> için geçirilen `GetFactory` istenen oluşturmak için yöntemi `DbProviderFactory` nesnesi.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Yüklü sağlayıcı Üreteç sınıflarını listeleme  
 Bu örnek nasıl kullanılacağı ortaya <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> döndürülecek yöntemi bir <xref:System.Data.DataTable> yüklü sağlayıcıları hakkında bilgi içeren. Her satır kod dolaşır `DataTable`, bilgi yüklü her sağlayıcı için konsol penceresinde görüntüler.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Fabrika bilgilerini depolamak için uygulama yapılandırma dosyalarını kullanma  
 Oluşturucuları ile çalışmak için kullanılan tasarım deseni kapsar sağlayıcısı ve bağlantı dizesi bilgileri gibi bir uygulama yapılandırma dosyasında depolamak **app.config** bir Windows uygulaması için ve **web.config**  bir ASP.NET uygulaması için.  
  
 Aşağıdaki yapılandırma dosyası parça iki adlandırılmış bağlantı dizeleri nasıl kaydedileceği SQL Server'da Northwind veritabanına bir bağlantı için "NorthwindSQL" ve "NorthwindAccess" erişim/Jet Northwind veritabanına bir bağlantı için gösterilmektedir. **Değişmez** adı için kullanıldığından **providerName** özniteliği.  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Bir bağlantı dizesi sağlayıcı ada göre alma  
 Sağlayıcı fabrikası oluşturmak için bir bağlantı dizesi ve bunun yanı sıra sağlayıcı adı belirtmeniz gerekir. Bu örnek, sağlayıcı adı değişmez biçiminde geçirerek bir uygulama yapılandırma dosyasından bağlantı dizesini almak gösterilmiştir "*System.Data.ProviderName*". Kod dolaşır <xref:System.Configuration.ConnectionStringSettingsCollection>. Döndürdüğü <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> başarı; Aksi halde `null` (`Nothing` Visual Basic'te). Sağlayıcı için birden fazla giriş varsa, ilk döndürülür. Daha fazla bilgi ve örnekler bağlantı dizelerini yapılandırma dosyalarından alınması için bkz: [bağlantı dizeleri ve yapılandırma dosyalarını](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Bir başvuru `System.Configuration.dll` sırayla çalıştırmak için kod için gereklidir.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>DbConnection ve DbProviderFactory oluşturma  
 Bu örnek nasıl oluşturulduğunu gösteren bir <xref:System.Data.Common.DbProviderFactory> ve <xref:System.Data.Common.DbConnection> sağlayıcı adı biçiminde geçirerek nesne "*System.Data.ProviderName*" ve bir bağlantı dizesi. A `DbConnection` nesne başarı; döndürdü `null` (`Nothing` Visual Basic'te) tüm hata.  
  
 Kod edinir `DbProviderFactory` çağırarak <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Ardından <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> yöntemi oluşturur <xref:System.Data.Common.DbConnection> nesne ve <xref:System.Data.Common.DbConnection.ConnectionString%2A> özelliğini bağlantı dizesine ayarlayın.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Yapılandırma sınıflarını kullanma](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
