---
title: Bağlantı Dizesi Söz Dizimi
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 9e9e330b7195e5c04b6e9e2d086a04209e1c0e13
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040153"
---
# <a name="connection-string-syntax"></a>Bağlantı Dizesi Söz Dizimi
Her .NET Framework veri sağlayıcısının, sağlayıcıya özgü <xref:System.Data.Common.DbConnection.ConnectionString%2A> özelliği ve <xref:System.Data.Common.DbConnection> devralan bir `Connection` nesnesi vardır. Her sağlayıcının özel bağlantı dizesi söz dizimi `ConnectionString` özelliğinde belgelenmiştir. Aşağıdaki tabloda .NET Framework bulunan dört veri sağlayıcısı listelenmektedir.  
  
|.NET Framework veri sağlayıcısı|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Microsoft SQL Server için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|OLE DB kullanılarak sunulan veri kaynakları için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|ODBC kullanılarak sunulan veri kaynakları için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Oracle sürüm 8.1.7 veya üzeri için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Bağlantı Dizesi Oluşturucular  
 ADO.NET 2,0, .NET Framework veri sağlayıcıları için aşağıdaki bağlantı dizesi oluşturuculara tanıtılmıştır.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Bağlantı dizesi oluşturucuları, çalışma zamanında sözdizimsel olarak geçerli bağlantı dizeleri oluşturma izni verir, bu nedenle kodunuzda bağlantı dizesi değerlerini el ile birleştirmek zorunda değilsiniz. Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](connection-string-builders.md).  

## <a name="windows-authentication"></a>Windows Kimlik Doğrulaması  
 Bunu destekleyen veri kaynaklarına bağlanmak için Windows kimlik doğrulaması (bazen *Tümleşik güvenlik*olarak adlandırılır) kullanmanızı öneririz. Bağlantı dizesinde kullanılan sözdizimi sağlayıcıya göre değişir. Aşağıdaki tabloda .NET Framework veri sağlayıcılarıyla kullanılan Windows kimlik doğrulama sözdizimi gösterilmektedir.  
  
|Sağlayıcı|Sözdizimi|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true`, `OleDb` sağlayıcısıyla kullanıldığında bir özel durum oluşturur.  
  
## <a name="sqlclient-connection-strings"></a>SqlClient bağlantı dizeleri  
Bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesinin sözdizimi <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> özelliğinde belgelenmiştir. SQL Server veritabanına yönelik bağlantı dizesi almak veya ayarlamak için <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> özelliğini kullanabilirsiniz. SQL Server önceki bir sürümüne bağlanmanız gerekiyorsa, OleDb için .NET Framework Veri Sağlayıcısı kullanmanız gerekir (<xref:System.Data.OleDb>). Birçok bağlantı dizesi anahtar sözcüğü de <xref:System.Data.SqlClient.SqlConnectionStringBuilder>özelliklere eşlenir.  

> [!IMPORTANT]
> `Persist Security Info` anahtar sözcüğünün varsayılan ayarı `false`' dir. `true` veya `yes` olarak ayarlamak, bağlantı açıldıktan sonra bağlantıdan elde edilecek kullanıcı KIMLIĞI ve parola dahil güvenlikle hassas bilgilerin yapılmasına izin verir. Güvenilir olmayan bir kaynağın hassas bağlantı dizesi bilgilerine erişiminin olmadığından emin olmak için `Persist Security Info` `false` olarak ayarlayın.  

### <a name="windows-authentication-with-sqlclient"></a>SqlClient ile Windows kimlik doğrulaması 
 Aşağıdaki sözdizimi biçimlerinin her biri, yerel bir sunucuda **AdventureWorks** veritabanına bağlanmak Için Windows kimlik doğrulamasını kullanır.  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>SqlClient SQL Server kimlik doğrulaması   
 SQL Server bağlanmak için Windows kimlik doğrulaması tercih edilir. Ancak, SQL Server kimlik doğrulaması gerekliyse, bir Kullanıcı adı ve parola belirtmek için aşağıdaki sözdizimini kullanın. Bu örnekte, geçerli bir Kullanıcı adı ve parolasını göstermek için yıldız işaretleri kullanılır.  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Azure SQL veritabanı veya Azure SQL veri ambarı 'na bağlanıp `user@servername`biçimde bir oturum açma sağladığınızda, oturum açma içindeki `servername` değerinin `Server=`için belirtilen değerle eşleştiğinden emin olun.

> [!NOTE]
> Windows kimlik doğrulaması SQL Server oturum açma bilgilerine göre önceliklidir. Hem tümleşik güvenlik = doğru hem de bir Kullanıcı adı ve parola belirtirseniz, Kullanıcı adı ve parola yok sayılır ve Windows kimlik doğrulaması kullanılır.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Adlandırılmış bir SQL Server örneğine bağlanma
Adlandırılmış bir SQL Server örneğine bağlanmak için *sunucu adı \ örnek adı* sözdizimini kullanın.  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Ayrıca, bir bağlantı dizesi oluştururken `SqlConnectionStringBuilder` <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> özelliğini örnek adına ayarlayabilirsiniz. <xref:System.Data.SqlClient.SqlConnection> nesnesinin <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> özelliği salt okunurdur.  
  
### <a name="type-system-version-changes"></a>Sistem sürümü değişikliklerini yazın  
 Bir <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> `Type System Version` anahtar sözcüğü SQL Server türlerin istemci tarafı gösterimini belirtir. `Type System Version` anahtar sözcüğü hakkında daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>SQL Server Express Kullanıcı örneklerine bağlanma ve Iliştirme  
 Kullanıcı örnekleri SQL Server Express bir özelliktir. Bu kişiler, en az ayrıcalıklı yerel Windows hesabında çalışan bir kullanıcının yönetici ayrıcalıklarına gerek duymadan bir SQL Server veritabanı eklemesi ve çalıştırmasına izin verir. Kullanıcı örneği, bir hizmet olarak değil kullanıcının Windows kimlik bilgileriyle yürütülür.  
  
 Kullanıcı örnekleriyle çalışma hakkında daha fazla bilgi için bkz. [SQL Server Express Kullanıcı örnekleri](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>TrustServerCertificate kullanma  
 `TrustServerCertificate` anahtar sözcüğü yalnızca geçerli bir sertifikayla bir SQL Server örneğine bağlanılırken geçerlidir. `TrustServerCertificate` `true`olarak ayarlandığında, aktarım katmanı, kanalı şifrelemek ve güveni doğrulamak üzere sertifika zincirini atlamak için SSL kullanır.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> `TrustServerCertificate` `true` olarak ayarlanırsa ve şifreleme açıksa, bağlantı dizesinde `Encrypt` `false` olarak ayarlanmış olsa bile, sunucuda belirtilen şifreleme düzeyi kullanılır. Aksi takdirde bağlantı başarısız olur.  
  
### <a name="enabling-encryption"></a>Şifrelemeyi etkinleştirme  
 Bir sertifika sunucuda sağlanmamışsa şifrelemeyi etkinleştirmek için, SQL Server Yapılandırma Yöneticisi ' de **zorlamalı protokol şifrelemesi** ve **güven sunucusu sertifikası** seçenekleri ayarlanmalıdır. Bu durumda, sunucuda herhangi bir doğrulanabilen sertifika sağlanmadıysa şifreleme, doğrulama olmadan otomatik olarak imzalanan bir sunucu sertifikası kullanacaktır.  
  
 Uygulama ayarları SQL Server ' de yapılandırılan güvenlik düzeyini azaltamaz, ancak isteğe bağlı olarak güçlendirebilirsiniz. Bir uygulama, `TrustServerCertificate` ve `Encrypt` anahtar sözcüklerini `true`olarak ayarlayarak şifrelemeyi isteyebilir ve bir sunucu sertifikası sağlanmamışsa ve **protokol şifrelemesini zorla** yapılandırılmamışsa bile şifrelemeyi garanti altına alır. istemci için. Ancak, istemci yapılandırmasında `TrustServerCertificate` etkinleştirilmemişse, sağlanan bir sunucu sertifikası yine de gereklidir.  
  
 Aşağıdaki tabloda tüm durumlar açıklanmaktadır.  
  
|Protokol şifrelemesini zorla istemci ayarı|Güven sunucusu sertifika istemci ayarı|Veri bağlantısı dizesi/özniteliği için şifrelemeyi şifreleme/kullanma|Güven sunucusu sertifika bağlantı dizesi/özniteliği|Sonuç|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Hayır|Yok|Hayır (varsayılan)|Yoksayıldı|Şifreleme gerçekleşmez.|  
|Hayır|Yok|Evet|Hayır (varsayılan)|Şifreleme yalnızca doğrulanabilir bir sunucu sertifikası varsa oluşur; Aksi takdirde bağlantı girişimi başarısız olur.|  
|Hayır|Yok|Evet|Evet|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan bir sunucu sertifikası kullanabilir.|  
|Evet|Hayır|Yoksayıldı|Yoksayıldı|Şifreleme yalnızca doğrulanabilir sunucu sertifikası varsa oluşur; Aksi takdirde bağlantı girişimi başarısız olur.|  
|Evet|Evet|Hayır (varsayılan)|Yoksayıldı|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan bir sunucu sertifikası kullanabilir.|  
|Evet|Evet|Evet|Hayır (varsayılan)|Şifreleme yalnızca doğrulanabilir sunucu sertifikası varsa oluşur; Aksi takdirde bağlantı girişimi başarısız olur.|  
|Evet|Evet|Evet|Evet|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan bir sunucu sertifikası kullanabilir.|  
  
 Daha fazla bilgi için bkz. [doğrulama olmadan şifrelemeyi kullanma](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>OleDb bağlantı dizeleri  
 Bir <xref:System.Data.OleDb.OleDbConnection> <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> özelliği, Microsoft Access gibi OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanak sağlar. Ayrıca, <xref:System.Data.OleDb.OleDbConnectionStringBuilder> sınıfını kullanarak çalışma zamanında `OleDb` bir bağlantı dizesi oluşturabilirsiniz.  
  
### <a name="oledb-connection-string-syntax"></a>OleDb bağlantı dizesi sözdizimi  
 <xref:System.Data.OleDb.OleDbConnection> bağlantı dizesi için bir sağlayıcı adı belirtmeniz gerekir. Aşağıdaki bağlantı dizesi, Jet Sağlayıcısı kullanılarak bir Microsoft Access veritabanına bağlanır. Veritabanı güvenli değilse (varsayılan) `User ID` ve `Password` anahtar kelimelerin isteğe bağlı olduğunu unutmayın.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 Jet veritabanının güvenliği, Kullanıcı düzeyinde güvenlik kullanılarak korunuyorsa, çalışma grubu bilgi dosyasının (. mdw) konumunu sağlamanız gerekir. Çalışma grubu bilgi dosyası, bağlantı dizesinde sunulan kimlik bilgilerini doğrulamak için kullanılır.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> Bir evrensel veri bağlantısı (UDL) dosyasında bir **OleDbConnection** için bağlantı bilgilerini sağlamak mümkündür; Ancak bunu yapmaktan kaçınmalısınız. UDL dosyaları şifrelenmez ve bağlantı dizesi bilgilerini şifresiz metin olarak kullanıma sunar. Bir UDL dosyası uygulamanıza yönelik dış dosya tabanlı bir kaynak olduğundan .NET Framework kullanılarak güvenliği alınamaz. UDL dosyaları **SqlClient**için desteklenmez.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Access/Jet 'e bağlanmak için DataDirectory kullanma  
 `DataDirectory`, `SqlClient`için özel değildir. Ayrıca, <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> .NET veri sağlayıcılarıyla birlikte kullanılabilir. Aşağıdaki örnek <xref:System.Data.OleDb.OleDbConnection> dize, uygulamanın App_Data klasöründe bulunan Northwind. mdb ' ye bağlanmak için gereken söz dizimini gösterir. Sistem veritabanı (System. mdw) de o konumda depolanır.  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Erişim/Jet veritabanı güvenli değilse, bağlantı dizesinde sistem veritabanının konumunu belirtmek gerekli değildir. Varsayılan ayar olarak, tüm kullanıcılar yerleşik yönetici kullanıcı olarak boş bir parolayla bağlantı kurarak. Kullanıcı düzeyi güvenlik doğru şekilde uygulansa bile, bir Jet veritabanı saldırılara karşı savunmasız kalır. Bu nedenle, bir erişim/Jet veritabanında gizli bilgilerin depolanması, dosya tabanlı güvenlik düzeninin büyük bir düzeyi nedeniyle önerilmez.  
  
### <a name="connecting-to-excel"></a>Excel 'e bağlanma  
 Microsoft Jet Sağlayıcısı, bir Excel çalışma kitabına bağlanmak için kullanılır. Aşağıdaki bağlantı dizesinde, `Extended Properties` anahtar sözcüğü Excel 'e özgü özellikleri ayarlar. "HDR = Yes;" değeri, ilk satırın sütun adlarını içerdiğini, veri ve "ıMEX = 1;" ise, sürücüye her zaman "karma" veri sütunlarını metin olarak okumasını söyler.  
  
```csharp 
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 `Extended Properties` için gereken çift tırnak karakterinin Ayrıca çift tırnak işareti içine alınması gerektiğini unutmayın.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Veri şekli sağlayıcısı bağlantı dizesi sözdizimi  
 Microsoft veri şekli sağlayıcısını kullanırken hem `Provider` hem de `Data Provider` anahtar sözcüklerini kullanın. Aşağıdaki örnek, SQL Server yerel bir örneğine bağlanmak için şekil sağlayıcısını kullanır.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>ODBC bağlantı dizeleri  
 Bir <xref:System.Data.Odbc.OdbcConnection> <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> özelliği OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanak sağlar. ODBC bağlantı dizeleri de <xref:System.Data.Odbc.OdbcConnectionStringBuilder>tarafından desteklenir.  
  
 Aşağıdaki bağlantı dizesi Microsoft metin sürücüsünü kullanır.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Visual FoxPro 'ya bağlanmak için DataDirectory kullanma  
 Aşağıdaki <xref:System.Data.Odbc.OdbcConnection> bağlantı dizesi örneği, bir Microsoft Visual FoxPro dosyasına bağlanmak için `DataDirectory` kullanmayı gösterir.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle bağlantı dizeleri  
 Bir <xref:System.Data.OracleClient.OracleConnection> <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> özelliği OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanak sağlar. Oracle bağlantı dizeleri de <xref:System.Data.OracleClient.OracleConnectionStringBuilder> tarafından desteklenir.  
  
```csharp 
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 ODBC bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz. <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](connection-strings.md)
- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
