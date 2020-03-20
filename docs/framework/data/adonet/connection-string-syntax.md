---
title: Bağlantı Dizesi Söz Dizimi
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 3df97419391fe17ef77a3b8f24c4f0689a04602f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151656"
---
# <a name="connection-string-syntax"></a>Bağlantı Dizesi Söz Dizimi
Her .NET Framework veri `Connection` sağlayıcısının, <xref:System.Data.Common.DbConnection> sağlayıcıya özgü <xref:System.Data.Common.DbConnection.ConnectionString%2A> bir özelliğin yanı sıra devralan bir nesnesi vardır. Her sağlayıcı için özel bağlantı dize sözdizimi kendi `ConnectionString` özelliği belgelenir. Aşağıdaki tabloda .NET Framework'e dahil edilen dört veri sağlayıcısı listelenir.  
  
|.NET Framework veri sağlayıcısı|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Microsoft SQL Server için veri erişimi sağlar. Bağlantı dize sözdizimi hakkında <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>daha fazla bilgi için bkz.|  
|<xref:System.Data.OleDb>|OLE DB kullanılarak açığa çıkarılan veri kaynakları için veri erişimi sağlar. Bağlantı dize sözdizimi hakkında <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>daha fazla bilgi için bkz.|  
|<xref:System.Data.Odbc>|ODBC kullanılarak açığa çıkarılan veri kaynakları için veri erişimi sağlar. Bağlantı dize sözdizimi hakkında <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>daha fazla bilgi için bkz.|  
|<xref:System.Data.OracleClient>|Oracle sürüm 8.1.7 veya sonraki sürüm için veri erişimi sağlar. Bağlantı dize sözdizimi hakkında <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>daha fazla bilgi için bkz.|  
  
## <a name="connection-string-builders"></a>Bağlantı Dizesi Oluşturucular  
 ADO.NET 2.0 .NET Framework veri sağlayıcıları için aşağıdaki bağlantı dize oluşturucuları tanıttı.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Bağlantı dize oluşturucuları çalışma zamanında sözdizimi olarak geçerli bağlantı dizeleri oluşturmanıza olanak sağlar, böylece kodunuzda bağlantı dize değerlerini el ile yapılandırmanız gerekmez. Daha fazla bilgi için [Bağlantı Dize Oluşturucuları'na](connection-string-builders.md)bakın.  

## <a name="windows-authentication"></a>Windows Kimlik Doğrulaması  
 Onu destekleyen veri kaynaklarına bağlanmak için Windows Kimlik Doğrulamasını (bazen *tümleşik güvenlik*olarak da adlandırılır) kullanmanızı öneririz. Bağlantı dizesinde kullanılan sözdizimi sağlayıcıya göre değişir. Aşağıdaki tabloda .NET Framework veri sağlayıcılarıyla kullanılan Windows Kimlik Doğrulama sözdizimi gösterilmektedir.  
  
|Sağlayıcı|Sözdizimi|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true``OleDb` sağlayıcı ile kullanıldığında bir özel durum atar.  
  
## <a name="sqlclient-connection-strings"></a>SqlClient Bağlantı Dizeleri  
<xref:System.Data.SqlClient.SqlConnection> Bağlantı dizesinin sözdizimi <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> özellikte belgelenmiştir. Bir SQL <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Server veritabanı için bağlantı dizesini almak veya ayarlamak için özelliği kullanabilirsiniz. SQL Server'ın önceki bir sürümüne bağlanmanız gerekiyorsa, OleDb için .NET<xref:System.Data.OleDb>Framework Data Provider () kullanmanız gerekir. Çoğu bağlantı dizeanahtar kelimeleri <xref:System.Data.SqlClient.SqlConnectionStringBuilder>de özellikleri eşleme .  

> [!IMPORTANT]
> Anahtar kelimenin `Persist Security Info` varsayılan ayarı `false`. Bağlantı açıldıktan sonra bağlantıdan kullanıcı kimliği ve parola da dahil olmak üzere güvenliğe duyarlı bilgilerin ayarlanması `true` veya `yes` alınmasına izin verir. Güvenilmeyen `false` bir kaynağın hassas bağlantı dize bilgilerine erişimi olmadığından emin olmak için `Persist Security Info` ayarlanmış tutun.  

### <a name="windows-authentication-with-sqlclient"></a>SqlClient ile Windows kimlik doğrulaması
 Aşağıdaki sözdizimi biçimlerinin her biri, yerel bir sunucudaki **AdventureWorks** veritabanına bağlanmak için Windows Kimlik Doğrulaması kullanır.  
  
```csharp  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>SqlClient ile SQL Server kimlik doğrulaması
 SQL Server'a bağlanmak için Windows Kimlik Doğrulama tercih edilir. Ancak, SQL Server Kimlik Doğrulaması gerekiyorsa, bir kullanıcı adı ve parola belirtmek için aşağıdaki sözdizimini kullanın. Bu örnekte, geçerli bir kullanıcı adı ve parolayı temsil etmek için yıldız işaretleri kullanılır.  
  
```csharp  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Azure SQL Veritabanı'na veya Azure SQL Veri Ambarı'na `user@servername`bağlandığınızda ve `servername` biçimde bir oturum açma sağladığınızda, oturum açmadaki değerin sağlanan değerle eşleştiğinden emin `Server=`olun.

> [!NOTE]
> Windows kimlik doğrulaması, SQL Server oturum açmalarından önce gelir. Hem Tümleşik Güvenlik=doğru, hem de kullanıcı adı ve parola belirtirseniz, kullanıcı adı ve parola yoksayılır ve Windows kimlik doğrulaması kullanılır.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>SQL Server adlı bir örneğe bağlanma
SQL Server adlı bir örneğine bağlanmak için *sunucu adı\instance* sözdizimini kullanın.  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Bağlantı dizesi <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> `SqlConnectionStringBuilder` inşa ederken örnek adı özelliğini de ayarlayabilirsiniz. Bir <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> <xref:System.Data.SqlClient.SqlConnection> nesnenin özelliği salt okunur.  
  
### <a name="type-system-version-changes"></a>Tip Sistemi Sürüm Değişiklikleri  
 Bir `Type System Version` anahtar kelime <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> SQL Server türlerinin istemci tarafı temsilini belirtir. Anahtar kelime hakkında daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> `Type System Version`  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>SQL Server Express Kullanıcı Örneklerine Bağlanma ve Bağlanma  
 Kullanıcı örnekleri SQL Server Express'te bir özelliktir. En az ayrıcalıklı yerel Windows hesabında çalışan bir kullanıcının, yönetim ayrıcalıkları gerektirmeden bir SQL Server veritabanı eklemesine ve çalıştırmasını sağlar. Bir kullanıcı örneği, hizmet olarak değil, kullanıcının Windows kimlik bilgileriyle yürütülür.  
  
 Kullanıcı örnekleriyle çalışma hakkında daha fazla bilgi için [SQL Server Express Kullanıcı Örnekleri'ne](./sql/sql-server-express-user-instances.md)bakın.  
  
## <a name="using-trustservercertificate"></a>TrustServerCertificate'ı kullanma  
 `TrustServerCertificate` Anahtar kelime yalnızca geçerli bir sertifikaya sahip bir SQL Server örneğine bağlanırken geçerlidir. `true`Ayarlandığında, `TrustServerCertificate` aktarım katmanı kanalı şifrelemek ve güveni doğrulamak için sertifika zincirini atlamak için SSL'yi kullanır.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> `TrustServerCertificate` Ayarlanan `true` ve şifreleme açıksa, bağlantı `Encrypt` `false` dizesinde ayarlanmış olsa bile sunucuda belirtilen şifreleme düzeyi kullanılır. Bağlantı aksi takdirde başarısız olur.  
  
### <a name="enabling-encryption"></a>Şifrelemeyi Etkinleştirme  
 Sunucuda bir sertifika sağlanmadıysa şifrelemeyi etkinleştirmek için **Force Protocol Encryption** ve Trust Server **Certificate** seçeneklerinin SQL Server Configuration Manager'da ayarlanabilmesi gerekir. Bu durumda, sunucuda doğrulanabilir bir sertifika sağlanmadıysa şifreleme, doğrulama olmadan kendi imzalanmış bir sunucu sertifikası kullanır.  
  
 Uygulama ayarları SQL Server'da yapılandırılan güvenlik düzeyini azaltamaz, ancak isteğe bağlı olarak güçlendirebilir. Bir `true`uygulama, sunucu sertifikası `TrustServerCertificate` `Encrypt` sağlanmamış ve Force **Protocol Encryption** istemci için yapılandırılmamış olsa bile şifrelemenin gerçekleştiğini garanti eden, anahtar kelimeleri ve anahtar kelimeleri ayarlayarak şifreleme isteyebilir. Ancak, `TrustServerCertificate` istemci yapılandırmasında etkinleştirilen değilse, yine de sağlanan bir sunucu sertifikası gereklidir.  
  
 Aşağıdaki tabloda tüm servis talepleri açıklanmaktadır.  
  
|Kuvvet Protokolü Şifreleme istemci ayarı|Güven Sunucu Sertifikası istemci ayarı|Veri bağlantısı dizesi/özniteliği için Şifreleme/Kullanma Şifrelemesi|Güven Sunucu Sertifikası bağlantı dizesi/özniteliği|Sonuç|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Hayır|Yok|Hayır (varsayılan)|Yoksayıldı|Şifreleme oluşmaz.|  
|Hayır|Yok|Evet|Hayır (varsayılan)|Şifreleme yalnızca doğrulanabilir bir sunucu sertifikası varsa oluşur, aksi takdirde bağlantı girişimi başarısız olur.|  
|Hayır|Yok|Evet|Evet|Şifreleme her zaman oluşur, ancak kendi imzalanmış bir sunucu sertifikası kullanabilir.|  
|Evet|Hayır|Yoksayıldı|Yoksayıldı|Şifreleme yalnızca doğrulanabilir bir sunucu sertifikası varsa oluşur; aksi takdirde, bağlantı girişimi başarısız olur.|  
|Evet|Evet|Hayır (varsayılan)|Yoksayıldı|Şifreleme her zaman oluşur, ancak kendi imzalanmış bir sunucu sertifikası kullanabilir.|  
|Evet|Evet|Evet|Hayır (varsayılan)|Şifreleme yalnızca doğrulanabilir bir sunucu sertifikası varsa oluşur; aksi takdirde, bağlantı girişimi başarısız olur.|  
|Evet|Evet|Evet|Evet|Şifreleme her zaman oluşur, ancak kendi imzalanmış bir sunucu sertifikası kullanabilir.|  
  
 Daha fazla bilgi için [bkz.](/sql/relational-databases/native-client/features/using-encryption-without-validation)
  
## <a name="oledb-connection-strings"></a>OleDb Bağlantı Dizeleri  
 A'nın <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> <xref:System.Data.OleDb.OleDbConnection> özelliği, Microsoft Access gibi bir OLE DB veri kaynağı için bir bağlantı dizesi almanızı veya ayarlamanızı sağlar. Ayrıca sınıfı kullanarak `OleDb` çalışma zamanında bir bağlantı <xref:System.Data.OleDb.OleDbConnectionStringBuilder> dizesi oluşturabilirsiniz.  
  
### <a name="oledb-connection-string-syntax"></a>OleDb Bağlantı Dize Sözdizimi  
 Bağlantı dizesi için <xref:System.Data.OleDb.OleDbConnection> bir sağlayıcı adı belirtmeniz gerekir. Aşağıdaki bağlantı dizesi Jet sağlayıcısını kullanarak microsoft access veritabanına bağlanır. Veritabanı güvenli `User ID` `Password` değilse (varsayılan) ve anahtar kelimelerin isteğe bağlı olduğunu unutmayın.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;
```  
  
 Jet veritabanı kullanıcı düzeyinde güvenlik kullanılarak güvenliyse, çalışma grubu bilgi dosyasının (.mdw) konumunu sağlamanız gerekir. Çalışma grubu bilgi dosyası, bağlantı dizesinde sunulan kimlik bilgilerini doğrulamak için kullanılır.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> Evrensel Veri Bağlantısı (UDL) dosyasında bir **OleDbConnection** bağlantısı için bağlantı bilgileri sağlamak mümkündür; ancak bunu yapmaktan kaçınmalısınız. UDL dosyaları şifrelenmez ve bağlantı dize bilgilerini açık metinde açığa çıkarır. UDL dosyası uygulamanız için harici bir dosya tabanlı kaynak olduğundan, .NET Framework kullanılarak güvenli hale alınamaz. UDL dosyaları **SqlClient**için desteklenmez.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Access/Jet'e Bağlanmak için DataDirectory'yi kullanma  
 `DataDirectory`'ye `SqlClient`özel değildir. Ayrıca <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> .NET veri sağlayıcıları ile kullanılabilir. Aşağıdaki örnek <xref:System.Data.OleDb.OleDbConnection> dize, uygulamanın app_data klasöründe bulunan Northwind.mdb'ye bağlanmak için gereken sözdizimini gösterir. Sistem veritabanı (System.mdw) da bu konumda depolanır.  
  
```csharp  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Access/Jet veritabanı güvenli değilse bağlantı dizesinde sistem veritabanının konumunu belirtmek gerekli değildir. Güvenlik varsayılan olarak kapalıdır ve tüm kullanıcılar boş bir parolayla yerleşik Yönetici kullanıcısı olarak bağlanır. Kullanıcı düzeyinde güvenlik doğru şekilde uygulansa bile, Jet veritabanı saldırılara karşı savunmasız kalır. Bu nedenle, dosya tabanlı güvenlik düzeninin doğal zayıflığı nedeniyle hassas bilgilerin Access/Jet veritabanında depolanması önerilmez.  
  
### <a name="connecting-to-excel"></a>Excel'e Bağlanma  
 Microsoft Jet sağlayıcısı bir Excel çalışma kitabına bağlanmak için kullanılır. Aşağıdaki bağlantı `Extended Properties` dizesinde, anahtar kelime Excel'e özgü özellikleri ayarlar. "HDR=Evet;" ilk satırın veri değil sütun adları içerdiğini belirtir ve "IMEX=1;" sürücüye her zaman "karışık" veri sütunlarını metin olarak okumasını söyler.  
  
```csharp
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Çift tırnak karakteri için `Extended Properties` gerekli de çift tırnak işaretleri eklenmelidir unutmayın.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Veri Şekli Sağlayıcı Bağlantı String Sözdizimi  
 Microsoft Veri `Provider` Şekli `Data Provider` sağlayıcısını kullanırken hem anahtar kelimeleri hem de anahtar kelimeleri kullanın. Aşağıdaki örnek, SQL Server'ın yerel bir örneğine bağlanmak için Şekil sağlayıcısını kullanır.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a>Odbc Bağlantı Dizeleri  
 A <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> <xref:System.Data.Odbc.OdbcConnection> özelliği, Bir OLE DB veri kaynağı için bir bağlantı dizesini almanızı veya ayarlamanızı sağlar. Odbc bağlantı dizeleri de tarafından <xref:System.Data.Odbc.OdbcConnectionStringBuilder>desteklenmektedir.  
  
 Aşağıdaki bağlantı dizesi Microsoft Metin Sürücüsü'nü kullanır.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Visual FoxPro'ya Bağlanmak için DataDirectory'yi Kullanma  
 Aşağıdaki <xref:System.Data.Odbc.OdbcConnection> bağlantı dize örneği, bir Microsoft Visual FoxPro dosyasına bağlanmak için kullanımı `DataDirectory` gösterir.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle Bağlantı Dizeleri  
 A <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> <xref:System.Data.OracleClient.OracleConnection> özelliği, Bir OLE DB veri kaynağı için bir bağlantı dizesini almanızı veya ayarlamanızı sağlar. Oracle bağlantı dizeleri de tarafından <xref:System.Data.OracleClient.OracleConnectionStringBuilder> desteklenir.  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 ODBC bağlantı dize sözdizimi <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>hakkında daha fazla bilgi için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](connection-strings.md)
- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
