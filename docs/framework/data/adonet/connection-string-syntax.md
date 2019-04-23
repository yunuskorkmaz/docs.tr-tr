---
title: Bağlantı Dizesi Söz Dizimi
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 4c5ed5000f075fb637915dc40e122a9337176e36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084981"
---
# <a name="connection-string-syntax"></a>Bağlantı Dizesi Söz Dizimi
Her .NET Framework veri sağlayıcısı sahip bir `Connection` devralınan nesne <xref:System.Data.Common.DbConnection> sağlayıcıya özgü yanı sıra <xref:System.Data.Common.DbConnection.ConnectionString%2A> özelliği. Belirli bir bağlantı dizesi söz dizimi tüm sağlayıcılar için belgelenen kendi `ConnectionString` özelliği. Aşağıdaki tablo, .NET Framework'e dahil edilen dört veri sağlayıcıları listeler.  
  
|.NET framework veri sağlayıcısı|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Microsoft SQL Server için veri erişim sağlar. Bağlantı dizesi söz dizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|OLE DB kullanılarak kullanıma sunulan veri kaynakları için veri erişim sağlar. Bağlantı dizesi söz dizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|ODBC kullanarak kullanıma sunulan veri kaynakları için veri erişim sağlar. Bağlantı dizesi söz dizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Version 8.1.7 Oracle için veri erişimi sağlar veya üzeri. Bağlantı dizesi söz dizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Bağlantı Dizesi Oluşturucular  
 ADO.NET 2.0, .NET Framework veri sağlayıcıları için aşağıdaki bağlantı dizesi oluşturucular kullanıma sunuldu.  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Bağlantı dizesi Oluşturucular, kodunuzdaki bağlantı dizesi değerlerini el ile birleştirilecek zorunda kalmazsınız sözdizimsel açıdan geçerli bağlantı dizeleri çalışma zamanında oluşturmak olanak tanır. Daha fazla bilgi için [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  

## <a name="windows-authentication"></a>Windows Kimlik Doğrulaması  
 Windows kimlik doğrulaması kullanmanızı öneririz (bazen denir *tümleşik güvenliği*) destekleyen veri kaynaklarına bağlanmak için. Bağlantı dizesinde kullanılan söz dizimi sağlayıcıya göre değişir. Aşağıdaki tablo, .NET Framework veri sağlayıcıları ile kullanılan Windows kimlik doğrulaması söz dizimini gösterir.  
  
|Sağlayıcı|Sözdizimi|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  `Integrated Security=true` ile kullanıldığında bir özel durum oluşturur `OleDb` sağlayıcısı.  
  
## <a name="sqlclient-connection-strings"></a>SqlClient bağlantı dizeleri  
Söz diziminin bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesi belirtilmiştir <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> özelliği. Kullanabileceğiniz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> alınacak veya ayarlanacak bir SQL Server veritabanı için bir bağlantı dizesi özelliği. SQL Server'ın önceki bir sürüme bağlanmanız gerekirse, OleDb için .NET Framework veri sağlayıcısı kullanmanız gerekir (<xref:System.Data.OleDb>). Çoğu bağlantı dizesi anahtar sözcükleri de özelliklerinde eşleyin <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  

> [!IMPORTANT]
>  Varsayılan ayarı `Persist Security Info` anahtar sözcüğü `false`. Bu ayarın `true` veya `yes` bağlantı açıldıktan sonra bağlantıdan alınacağı kullanıcı kimliği ve parola gibi güvenlik bakımından hassas bilgiler sağlar. Tutun `Persist Security Info` kümesine `false` güvenilmeyen bir kaynağa erişim hassas bağlantı dizesi bilgilerini yok emin olmak için.  

### <a name="windows-authentication-with-sqlclient"></a>Windows kimlik doğrulaması ile SqlClient 
 Bağlanmak için Windows kimlik doğrulaması kullanan her sözdizimi aşağıdaki biçimlerden birini **AdventureWorks** yerel bir sunucuda veritabanı.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>SQL Server kimlik doğrulamasını SqlClient   
 Windows kimlik doğrulaması, SQL Server'a bağlanmak için tercih edilir. Ancak, SQL Server kimlik doğrulaması gerekiyorsa, bir kullanıcı adı ve parola belirtmek için aşağıdaki sözdizimini kullanın. Bu örnekte, yıldız işareti, geçerli kullanıcı adı ve parola temsil etmek için kullanılır.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Ne zaman Azure SQL veritabanı veya Azure SQL Data warehouse'a bağlanmak ve biçiminde bir oturum açma adı sağlamak `user@servername`, emin `servername` oturum açma değeri eşler için sağlanan değer `Server=`.

> [!NOTE]
>  Windows kimlik doğrulaması SQL Server oturumları daha önceliklidir. Tümleşik güvenlik belirtmek iyi bir kullanıcı adı ve parola, kullanıcı adı ve parola yoksayılacak ve Windows kimlik doğrulaması kullanılır = true.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>SQL Server'ın adlandırılmış bir örneğine bağlanın
SQL Server'ın adlandırılmış bir örneğine bağlanmak için *sunucu adı\örnek adı* söz dizimi.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
Ayrıca <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> özelliği `SqlConnectionStringBuilder` bir bağlantı dizesi oluştururken örneği adı. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> Özelliği bir <xref:System.Data.SqlClient.SqlConnection> nesne, salt okunur.  
  
### <a name="type-system-version-changes"></a>Tür sistemi sürüm değişikliği  
 `Type System Version` Anahtar sözcüğü bir <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> SQL Server türleri istemci-tarafı gösterimini belirtir. Bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> hakkında daha fazla bilgi için `Type System Version` anahtar sözcüğü.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Express kullanıcı örnekleri bağlanmak ve SQL sunucusuna iliştiriliyor  
 Kullanıcı örnekleri, SQL Server Express özelliğidir. Ekleme ve yönetici ayrıcalıklarına gerek duymadan bir SQL Server veritabanını çalıştırmak bir en az ayrıcalıklı yerel Windows hesabı çalıştıran kullanıcının sağlarlar. Bir kullanıcı örneği, kullanıcının Windows kimlik bilgileri ile değil hizmet olarak yürütür.  
  
 Kullanıcı örnekleri ile çalışma hakkında daha fazla bilgi için bkz. [SQL Server Express kullanıcı örnekleri](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>TrustServerCertificate kullanma  
 `TrustServerCertificate` Anahtar sözcüğü, yalnızca geçerli bir sertifika ile bir SQL Server örneğine bağlanırken geçerlidir. Zaman `TrustServerCertificate` ayarlanır `true`, Aktarım katmanı kanalını şifrelemek ve güven doğrulamak için sertifika zinciri walking atlamak için SSL kullanır.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  Varsa `TrustServerCertificate` ayarlanır `true` ve şifreleme açıktır, sunucuda belirtilen şifreleme düzeyini kullanılacak bile `Encrypt` ayarlanır `false` bağlantı dizesindeki. Aksi halde bağlantı başarısız olur.  
  
### <a name="enabling-encryption"></a>Şifrelemeyi etkinleştirme  
 Sunucuda bir sertifika sağlanmadığı durumlarda şifrelemeyi etkinleştirmek için **zorla Protokolü şifreleme** ve **güvenilir sunucu sertifikası** seçenekleri, SQL Server Yapılandırma Yöneticisi'nde ayarlanmış olması gerekir. Bu durumda, sunucuda doğrulanabilir sertifika sağladıysanız şifreleme otomatik olarak imzalanan sertifikasını doğrulama olmadan kullanın.  
  
 Uygulama ayarları, SQL Server'da yapılandırılan güvenlik düzeyini indiremezsiniz, ancak isteğe bağlı olarak güçlendirebilirsiniz. Bir uygulama şifreleme ayarlayarak isteyebilir `TrustServerCertificate` ve `Encrypt` anahtar sözcükler `true`, olduğunda bile sunucu sertifikası sağlanmamış şifreleme gerçekleşir, güvence altına alır ve **zorla Protokolü şifreleme**  istemci için yapılandırılmadı. Ancak, varsa `TrustServerCertificate` etkin istemci yapılandırmasında sağlanan sunucu sertifikası hala gereklidir.  
  
 Aşağıdaki tablo, tüm durumları açıklar.  
  
|Şifreleme Protokolü istemci ayarı zorla|Sunucu sertifikası istemci ayarı güven|Veri bağlantı dizesi/özniteliği için şifreleme kullan şifreleme|Güvenilir sunucu sertifikası bağlantı dizesi/özniteliği|Sonuç|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Hayır|Yok|Hayır (varsayılan)|Yoksayıldı|Şifreleme gerçekleşir.|  
|Hayır|Yok|Evet|Hayır (varsayılan)|Şifreleme, yalnızca bağlantı denemesi başarısız doğrulanabilir sunucu sertifikası, aksi durumda ise oluşur.|  
|Hayır|Yok|Evet|Evet|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan sertifikasını kullanabilir.|  
|Evet|Hayır|Yoksayıldı|Yoksayıldı|Doğrulanabilen bir sunucu sertifikası yoksa, şifreleme oluşur; Aksi takdirde, bağlantı denemesi başarısız olur.|  
|Evet|Evet|Hayır (varsayılan)|Yoksayıldı|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan sertifikasını kullanabilir.|  
|Evet|Evet|Evet|Hayır (varsayılan)|Doğrulanabilen bir sunucu sertifikası yoksa, şifreleme oluşur; Aksi takdirde, bağlantı denemesi başarısız olur.|  
|Evet|Evet|Evet|Evet|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan sertifikasını kullanabilir.|  
  
 Daha fazla bilgi için [kullanarak şifreleme olmadan doğrulama](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>OleDb bağlantı dizeleri  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Özelliği bir <xref:System.Data.OleDb.OleDbConnection> almak veya ayarlamak için bir OLE DB veri kaynağı Microsoft Access gibi bir bağlantı dizesi sağlar. Ayrıca oluşturabileceğiniz bir `OleDb` bağlantı dizesi kullanarak çalışma zamanında <xref:System.Data.OleDb.OleDbConnectionStringBuilder> sınıfı.  
  
### <a name="oledb-connection-string-syntax"></a>OleDb bağlantı dizesi söz dizimi  
 İçin bir sağlayıcı adı belirtmeniz gerekir bir <xref:System.Data.OleDb.OleDbConnection> bağlantı dizesi. Aşağıdaki bağlantı dizesi, Jet sağlayıcısını kullanarak bir Microsoft Access veritabanına bağlanır. Unutmayın `User ID` ve `Password` sözcükler veritabanına (varsayılan) güvenli olmayan isteğe bağlı.  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Jet veritabanı kullanıcı düzeyinde güvenlik kullanarak güvenli hale getirilmişse, çalışma grubu bilgi dosyası (.mdw) konumu sağlamanız gerekir. Çalışma grubu bilgi dosyası bağlantı dizesinde sunulan kimlik bilgilerini doğrulamak için kullanılır.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  İlgili bağlantı bilgilerini sağlamak olası bir **OleDbConnection** evrensel veri bağlantısı (UDL) dosyasında; Bununla birlikte, kaçının bunu. UDL dosyaları şifreli olmayan ve düz metin bağlantı dizesi bilgilerini kullanıma sunar. UDL dosyası uygulamanız için bir dış dosya tabanlı kaynak olduğundan, .NET Framework kullanarak korunamıyor. UDL dosyaları için desteklenmez **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>DataDirectory kullanarak erişim/Jet bağlanma  
 `DataDirectory` Özel değil `SqlClient`. İle de kullanılabilir <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> .NET veri sağlayıcıları. Aşağıdaki örnek <xref:System.Data.OleDb.OleDbConnection> dize uygulamanın app_data klasöründe bulunan Northwind.mdb bağlanmak için gereken söz dizimini gösterir. Sistem veritabanı (System.mdw), ayrıca söz konusu konumda depolanır.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  Bağlantı dizesinde sistem veritabanı konumunu belirtme, erişim/Jet veritabanı güvenli değilse gerekli değildir. Güvenlik varsayılan olarak, boş bir parola ile yerleşik yönetici kullanıcı olarak bağlanma tüm kullanıcılarla kapalıdır. Kullanıcı düzeyinde güvenliği daha doğru bir şekilde uygulandığından, Jet veritabanı saldırıya açık kalır. Bu nedenle, hassas bilgileri bir erişim/Jet veritabanı depolama, dosya tabanlı güvenlik düzeninin devralınan zayıflık nedeniyle önerilmez.  
  
### <a name="connecting-to-excel"></a>Excel'e bağlanma  
 Microsoft Jet Sağlayıcısı, bir Excel çalışma kitabına bağlanmak için kullanılır. Aşağıdaki bağlantı dizesinde `Extended Properties` anahtar sözcüğü Excel'e özgü özelliklerini ayarlar. "HDR = Evet;" ilk satırı sütun adları, verileri değil, içerdiğini gösterir ve "IMEX = 1;" her zaman "Karıştırılmış" veri sütunları metin olarak okumak için sürücü söyler.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Çift tırnak karakteri gerekli Not `Extended Properties` çift tırnak içine alınmalıdır.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Veri şekli sağlayıcısına bağlantı dizesi söz dizimi  
 İkisi de `Provider` ve `Data Provider` Microsoft Veri Şekli Sağlayıcısı kullanılırken anahtar sözcükleri. Aşağıdaki örnek, yerel bir SQL Server örneğine bağlanmak için Şekil sağlayıcısı kullanır.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>ODBC bağlantı dizeleri  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> Özelliği bir <xref:System.Data.Odbc.OdbcConnection> alınacak veya ayarlanacak bir OLE DB veri kaynağı için bir bağlantı dizesi sağlar. ODBC bağlantı dizeleri tarafından da desteklenir <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 Aşağıdaki bağlantı dizesi, Microsoft metin sürücüsünü kullanır.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Visual FoxPro için bağlanmak için DataDirectory'ı kullanma  
 Aşağıdaki <xref:System.Data.Odbc.OdbcConnection> bağlantı dizesi örneği gösterir kullanarak `DataDirectory` bir Microsoft Visual FoxPro dosyasına bağlanmak için.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle bağlantı dizeleri  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Özelliği bir <xref:System.Data.OracleClient.OracleConnection> alınacak veya ayarlanacak bir OLE DB veri kaynağı için bir bağlantı dizesi sağlar. Oracle bağlantı dizeleri tarafından da desteklenir <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 ODBC bağlantı dizesi söz dizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)
- [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
