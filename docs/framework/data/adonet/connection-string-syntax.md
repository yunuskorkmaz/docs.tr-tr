---
title: Bağlantı Dizesi Söz Dizimi
description: ADO.NET içinde bağlantı dizelerinin sözdizimi hakkında bilgi edinin. Her sağlayıcının sözdizimi ConnectionString özelliğinde belgelenmiştir.
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 5942307535e9a6e10009f193289daf94a07cd950
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148417"
---
# <a name="connection-string-syntax"></a>Bağlantı Dizesi Söz Dizimi

Her .NET Framework veri sağlayıcısının, `Connection` sağlayıcıya özgü bir özelliği ve öğesinden devralan bir nesnesi vardır <xref:System.Data.Common.DbConnection> <xref:System.Data.Common.DbConnection.ConnectionString%2A> . Her sağlayıcının özel bağlantı dizesi söz dizimi, `ConnectionString` özelliğinde belgelenmiştir. Aşağıdaki tabloda .NET Framework bulunan dört veri sağlayıcısı listelenmektedir.  
  
|.NET Framework veri sağlayıcısı|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Microsoft SQL Server için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> ..|  
|<xref:System.Data.OleDb>|OLE DB kullanılarak sunulan veri kaynakları için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> ..|  
|<xref:System.Data.Odbc>|ODBC kullanılarak sunulan veri kaynakları için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> ..|  
|<xref:System.Data.OracleClient>|Oracle sürüm 8.1.7 veya üzeri için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> ..|  
  
## <a name="connection-string-builders"></a>Bağlantı Dizesi Oluşturucular  

 ADO.NET 2,0, .NET Framework veri sağlayıcıları için aşağıdaki bağlantı dizesi oluşturuculara tanıtılmıştır.  
  
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
- <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
- <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
- <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Bağlantı dizesi oluşturucuları, çalışma zamanında sözdizimsel olarak geçerli bağlantı dizeleri oluşturma izni verir, bu nedenle kodunuzda bağlantı dizesi değerlerini el ile birleştirmek zorunda değilsiniz. Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](connection-string-builders.md).  

## <a name="windows-authentication"></a>Windows Kimlik Doğrulaması  

 Bunu destekleyen veri kaynaklarına bağlanmak için Windows kimlik doğrulaması (bazen *Tümleşik güvenlik*olarak adlandırılır) kullanmanızı öneririz. Bağlantı dizesinde kullanılan sözdizimi sağlayıcıya göre değişir. Aşağıdaki tabloda .NET Framework veri sağlayıcılarıyla kullanılan Windows kimlik doğrulama sözdizimi gösterilmektedir.  
  
|Sağlayıcı|Syntax|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
> `Integrated Security=true` sağlayıcıyla birlikte kullanıldığında bir özel durum oluşturur `OleDb` .  
  
## <a name="sqlclient-connection-strings"></a>SqlClient bağlantı dizeleri  

Bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesinin sözdizimi, <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> özelliğinde belgelenmiştir. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>Özelliği, bir SQL Server veritabanı için bağlantı dizesi almak veya ayarlamak için kullanabilirsiniz. SQL Server önceki bir sürümüne bağlanmanız gerekiyorsa, OleDb için .NET Framework Veri Sağlayıcısı kullanmanız gerekir ( <xref:System.Data.OleDb> ). Birçok bağlantı dizesi anahtar sözcüğü, içindeki özellikleriyle da eşlenir <xref:System.Data.SqlClient.SqlConnectionStringBuilder> .  

> [!IMPORTANT]
> Anahtar sözcüğü için varsayılan ayar `Persist Security Info` `false` . `true` `yes` Bağlantı açıldıktan sonra bağlantıdan alınabilmesi için, Kullanıcı kimliği ve parola dahil olmak üzere güvenliğe duyarlı bilgilerin olarak ayarlanması veya buna izin vermek için. `Persist Security Info` `false` Güvenilir olmayan bir kaynağın hassas bağlantı dizesi bilgilerine erişimi olmadığından emin olmak için olarak ayarlayın.  

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

Azure SQL veritabanı veya Azure SQL veri ambarı 'na bağlanıp biçimde bir oturum açma sağladığınızda `user@servername` , `servername` oturum açma alanındaki değerin için belirtilen değerle eşleştiğinden emin olun `Server=` .

> [!NOTE]
> Windows kimlik doğrulaması SQL Server oturum açma bilgilerine göre önceliklidir. Hem tümleşik güvenlik = doğru hem de bir Kullanıcı adı ve parola belirtirseniz, Kullanıcı adı ve parola yok sayılır ve Windows kimlik doğrulaması kullanılır.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Adlandırılmış bir SQL Server örneğine bağlanma

Adlandırılmış bir SQL Server örneğine bağlanmak için *sunucu adı \ örnek adı* sözdizimini kullanın.  
  
```csharp  
"Data Source=MySqlServer\MSSQL1;"  
```  

Ayrıca <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> , `SqlConnectionStringBuilder` bir bağlantı dizesi oluştururken öğesinin özelliğini örnek adı olarak ayarlayabilirsiniz. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A>Bir <xref:System.Data.SqlClient.SqlConnection> nesnenin özelliği salt okunurdur.  
  
### <a name="type-system-version-changes"></a>Sistem sürümü değişikliklerini yazın  

 `Type System Version`İçindeki anahtar sözcüğü <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> SQL Server türlerinin istemci tarafı gösterimini belirler. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>Anahtar sözcüğü hakkında daha fazla bilgi için bkz `Type System Version` ..  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>SQL Server Express Kullanıcı örneklerine bağlanma ve Iliştirme  

 Kullanıcı örnekleri SQL Server Express bir özelliktir. Bu kişiler, en az ayrıcalıklı yerel Windows hesabında çalışan bir kullanıcının yönetici ayrıcalıklarına gerek duymadan bir SQL Server veritabanı eklemesi ve çalıştırmasına izin verir. Kullanıcı örneği, bir hizmet olarak değil kullanıcının Windows kimlik bilgileriyle yürütülür.  
  
 Kullanıcı örnekleriyle çalışma hakkında daha fazla bilgi için bkz. [SQL Server Express Kullanıcı örnekleri](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>TrustServerCertificate kullanma  

 `TrustServerCertificate`Anahtar sözcüğü yalnızca geçerli bir sertifikayla SQL Server örneğine bağlanılırken geçerlidir. , `TrustServerCertificate` Olarak ayarlandığında `true` , aktarım katmanı, kanalı şifrelemek ve güveni doğrulamak üzere sertifika zincirini atlamak için SSL kullanır.  
  
```csharp  
"TrustServerCertificate=true;"
```  
  
> [!NOTE]
> , `TrustServerCertificate` Olarak ayarlanmışsa `true` ve şifreleme açıksa, `Encrypt` bağlantı dizesinde olarak ayarlanmış olsa bile, sunucuda belirtilen şifreleme düzeyi kullanılır `false` . Aksi takdirde bağlantı başarısız olur.  
  
### <a name="enabling-encryption"></a>Şifrelemeyi etkinleştirme  

 Bir sertifika sunucuda sağlanmamışsa şifrelemeyi etkinleştirmek için, SQL Server Yapılandırma Yöneticisi ' de **zorlamalı protokol şifrelemesi** ve **güven sunucusu sertifikası** seçenekleri ayarlanmalıdır. Bu durumda, sunucuda herhangi bir doğrulanabilen sertifika sağlanmadıysa şifreleme, doğrulama olmadan otomatik olarak imzalanan bir sunucu sertifikası kullanacaktır.  
  
 Uygulama ayarları SQL Server ' de yapılandırılan güvenlik düzeyini azaltamaz, ancak isteğe bağlı olarak güçlendirebilirsiniz. Bir uygulama, `TrustServerCertificate` ve `Encrypt` anahtar sözcüklerini olarak ayarlayarak şifrelemeyi isteyebilir `true` , bir sunucu sertifikası sağlanmamışsa ve Istemci Için **zorlamalı protokol şifrelemesi** yapılandırılmadığı zaman bile bu şifrelemenin gerçekleşmesini garanti edebilir. Ancak, `TrustServerCertificate` istemci yapılandırmasında etkinleştirilmemişse, sağlanan bir sunucu sertifikası yine de gereklidir.  
  
 Aşağıdaki tabloda tüm durumlar açıklanmaktadır.  
  
|Protokol şifrelemesini zorla istemci ayarı|Güven sunucusu sertifika istemci ayarı|Veri bağlantısı dizesi/özniteliği için şifrelemeyi şifreleme/kullanma|Güven sunucusu sertifika bağlantı dizesi/özniteliği|Sonuç|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|No|Yok|Hayır (varsayılan)|Yoksayıldı|Şifreleme gerçekleşmez.|  
|No|Yok|Yes|Hayır (varsayılan)|Şifreleme yalnızca doğrulanabilir bir sunucu sertifikası varsa oluşur; Aksi takdirde bağlantı girişimi başarısız olur.|  
|No|Yok|Yes|Yes|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan bir sunucu sertifikası kullanabilir.|  
|Yes|Hayır|Yoksayıldı|Yoksayıldı|Şifreleme yalnızca doğrulanabilir sunucu sertifikası varsa oluşur; Aksi takdirde bağlantı girişimi başarısız olur.|  
|Yes|Yes|Hayır (varsayılan)|Yoksayıldı|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan bir sunucu sertifikası kullanabilir.|  
|Yes|Yes|Yes|Hayır (varsayılan)|Şifreleme yalnızca doğrulanabilir sunucu sertifikası varsa oluşur; Aksi takdirde bağlantı girişimi başarısız olur.|  
|Yes|Yes|Yes|Yes|Şifreleme her zaman gerçekleşir, ancak otomatik olarak imzalanan bir sunucu sertifikası kullanabilir.|  
  
 Daha fazla bilgi için bkz. [doğrulama olmadan şifrelemeyi kullanma](/sql/relational-databases/native-client/features/using-encryption-without-validation).
  
## <a name="oledb-connection-strings"></a>OleDb bağlantı dizeleri  

 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>Bir öğesinin özelliği, <xref:System.Data.OleDb.OleDbConnection> Microsoft Access gibi bir OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanak sağlar. Ayrıca `OleDb` , sınıfını kullanarak çalışma zamanında bir bağlantı dizesi oluşturabilirsiniz <xref:System.Data.OleDb.OleDbConnectionStringBuilder> .  
  
### <a name="oledb-connection-string-syntax"></a>OleDb bağlantı dizesi sözdizimi  

 Bağlantı dizesi için bir sağlayıcı adı belirtmeniz gerekir <xref:System.Data.OleDb.OleDbConnection> . Aşağıdaki bağlantı dizesi, Jet Sağlayıcısı kullanılarak bir Microsoft Access veritabanına bağlanır. `User ID` `Password` Veritabanı güvenli değilse (varsayılan) ve anahtar kelimelerin isteğe bağlı olduğunu unutmayın.  
  
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

 `DataDirectory` , için özel değildir `SqlClient` . Ayrıca, <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> .NET veri sağlayıcılarıyla birlikte kullanılabilir. Aşağıdaki örnek <xref:System.Data.OleDb.OleDbConnection> dize, uygulamanın App_Data klasöründe bulunan Northwind. mdb ' ye bağlanmak için gereken söz dizimini gösterir. Sistem veritabanı (System. mdw) de o konumda depolanır.  
  
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
  
 İçin gereken çift tırnak karakterinin `Extended Properties` Ayrıca çift tırnak işareti içine alınması gerektiğini unutmayın.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Veri şekli sağlayıcısı bağlantı dizesi sözdizimi  

 `Provider` `Data Provider` Microsoft veri şekli sağlayıcısını kullanırken hem hem de anahtar sözcüklerini kullanın. Aşağıdaki örnek, SQL Server yerel bir örneğine bağlanmak için şekil sağlayıcısını kullanır.  
  
```csharp  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"
```  
  
## <a name="odbc-connection-strings"></a>ODBC bağlantı dizeleri  

 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>Öğesinin özelliği, bir <xref:System.Data.Odbc.OdbcConnection> OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanak sağlar. ODBC bağlantı dizeleri de tarafından desteklenir <xref:System.Data.Odbc.OdbcConnectionStringBuilder> .  
  
 Aşağıdaki bağlantı dizesi Microsoft metin sürücüsünü kullanır.  
  
```csharp  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Visual FoxPro 'ya bağlanmak için DataDirectory kullanma  

 Aşağıdaki <xref:System.Data.Odbc.OdbcConnection> bağlantı dizesi örneği, `DataDirectory` bir Microsoft Visual FoxPro dosyasına bağlanmak için kullanımını gösterir.  
  
```csharp  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle bağlantı dizeleri  

 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>Öğesinin özelliği, bir <xref:System.Data.OracleClient.OracleConnection> OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanak sağlar. Oracle bağlantı dizeleri de tarafından desteklenir <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```csharp
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 ODBC bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı dizeleri](connection-strings.md)
- [Bir veri kaynağına bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
