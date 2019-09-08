---
title: Bağlantı Dizesi Söz Dizimi
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 00b8dc4c7592daa200f1a2a6c3c7fa9a3c587087
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784921"
---
# <a name="connection-string-syntax"></a>Bağlantı Dizesi Söz Dizimi
Her .NET Framework veri sağlayıcısının, sağlayıcıya `Connection` özgü <xref:System.Data.Common.DbConnection.ConnectionString%2A> bir özelliği ve <xref:System.Data.Common.DbConnection> öğesinden devralan bir nesnesi vardır. Her sağlayıcının özel bağlantı dizesi söz dizimi, `ConnectionString` özelliğinde belgelenmiştir. Aşağıdaki tabloda .NET Framework bulunan dört veri sağlayıcısı listelenmektedir.  
  
|.NET Framework veri sağlayıcısı|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Microsoft SQL Server için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|OLE DB kullanılarak sunulan veri kaynakları için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|ODBC kullanılarak sunulan veri kaynakları için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Oracle sürüm 8.1.7 veya üzeri için veri erişimi sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
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
> `Integrated Security=true``OleDb` sağlayıcıyla birlikte kullanıldığında bir özel durum oluşturur.  
  
## <a name="sqlclient-connection-strings"></a>SqlClient bağlantı dizeleri  
Bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesinin sözdizimi, <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> özelliğinde belgelenmiştir. Özelliği, <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> bir SQL Server veritabanı için bağlantı dizesi almak veya ayarlamak için kullanabilirsiniz. SQL Server önceki bir sürümüne bağlanmanız gerekiyorsa, OleDb için .NET Framework Veri Sağlayıcısı kullanmanız gerekir (<xref:System.Data.OleDb>). Birçok bağlantı dizesi anahtar sözcüğü, <xref:System.Data.SqlClient.SqlConnectionStringBuilder>içindeki özellikleriyle da eşlenir.  

> [!IMPORTANT]
> `Persist Security Info` Anahtar sözcüğü için varsayılan ayar. `false` Bağlantı açıldıktan sonra `true` bağlantıdan `yes` alınabilmesi için, Kullanıcı kimliği ve parola dahil olmak üzere güvenliğe duyarlı bilgilerin olarak ayarlanması veya buna izin vermek için. Güvenilir olmayan bir `false` kaynağın hassas bağlantı dizesi bilgilerine erişimi olmadığından emin olmak için olarak ayarlayın.`Persist Security Info`  

### <a name="windows-authentication-with-sqlclient"></a>SqlClient ile Windows kimlik doğrulaması 
 Aşağıdaki sözdizimi biçimlerinin her biri, yerel bir sunucuda **AdventureWorks** veritabanına bağlanmak Için Windows kimlik doğrulamasını kullanır.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>SqlClient SQL Server kimlik doğrulaması   
 SQL Server bağlanmak için Windows kimlik doğrulaması tercih edilir. Ancak, SQL Server kimlik doğrulaması gerekliyse, bir Kullanıcı adı ve parola belirtmek için aşağıdaki sözdizimini kullanın. Bu örnekte, geçerli bir Kullanıcı adı ve parolasını göstermek için yıldız işaretleri kullanılır.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

Azure SQL veritabanı veya Azure SQL veri ambarı 'na bağlanıp biçimde `user@servername`bir oturum açma sağladığınızda, oturum açma alanındaki `servername` değerin için `Server=`belirtilen değerle eşleştiğinden emin olun.

> [!NOTE]
> Windows kimlik doğrulaması SQL Server oturum açma bilgilerine göre önceliklidir. Hem tümleşik güvenlik = doğru hem de bir Kullanıcı adı ve parola belirtirseniz, Kullanıcı adı ve parola yok sayılır ve Windows kimlik doğrulaması kullanılır.  

### <a name="connect-to-a-named-instance-of-sql-server"></a>Adlandırılmış bir SQL Server örneğine bağlanma
Adlandırılmış bir SQL Server örneğine bağlanmak için *sunucu adı \ örnek adı* sözdizimini kullanın.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
Ayrıca, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> `SqlConnectionStringBuilder` bir bağlantı dizesi oluştururken öğesinin özelliğini örnek adı olarak ayarlayabilirsiniz. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> Bir<xref:System.Data.SqlClient.SqlConnection> nesnenin özelliği salt okunurdur.  
  
### <a name="type-system-version-changes"></a>Sistem sürümü değişikliklerini yazın  
 İçindeki anahtar sözcüğü SQL Server türlerinin istemci tarafı gösterimini belirler.<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> `Type System Version` Anahtar`Type System Version` sözcüğü hakkında daha fazla bilgi için bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> .  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>SQL Server Express Kullanıcı örneklerine bağlanma ve Iliştirme  
 Kullanıcı örnekleri SQL Server Express bir özelliktir. Bu kişiler, en az ayrıcalıklı yerel Windows hesabında çalışan bir kullanıcının yönetici ayrıcalıklarına gerek duymadan bir SQL Server veritabanı eklemesi ve çalıştırmasına izin verir. Kullanıcı örneği, bir hizmet olarak değil kullanıcının Windows kimlik bilgileriyle yürütülür.  
  
 Kullanıcı örnekleriyle çalışma hakkında daha fazla bilgi için bkz. [SQL Server Express Kullanıcı örnekleri](./sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>TrustServerCertificate kullanma  
 `TrustServerCertificate` Anahtar sözcüğü yalnızca geçerli bir sertifikayla SQL Server örneğine bağlanılırken geçerlidir. `TrustServerCertificate` , Olarak`true`ayarlandığında, aktarım katmanı, kanalı şifrelemek ve güveni doğrulamak üzere sertifika zincirini atlamak için SSL kullanır.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
> , Olarak `true` ayarlanmışsa ve şifreleme açıksa, bağlantı dizesinde olarak `false` ayarlanmış olsa bile `Encrypt` , sunucuda belirtilen şifreleme düzeyi kullanılır. `TrustServerCertificate` Aksi takdirde bağlantı başarısız olur.  
  
### <a name="enabling-encryption"></a>Şifrelemeyi etkinleştirme  
 Bir sertifika sunucuda sağlanmamışsa şifrelemeyi etkinleştirmek için, SQL Server Yapılandırma Yöneticisi ' de **zorlamalı protokol şifrelemesi** ve **güven sunucusu sertifikası** seçenekleri ayarlanmalıdır. Bu durumda, sunucuda herhangi bir doğrulanabilen sertifika sağlanmadıysa şifreleme, doğrulama olmadan otomatik olarak imzalanan bir sunucu sertifikası kullanacaktır.  
  
 Uygulama ayarları SQL Server ' de yapılandırılan güvenlik düzeyini azaltamaz, ancak isteğe bağlı olarak güçlendirebilirsiniz. Bir uygulama `TrustServerCertificate` , ve `Encrypt` anahtar sözcüklerini olarak `true`ayarlayarak şifrelemeyi isteyebilir, bir sunucu sertifikası sağlanmadıysa ve **zorlamalı protokol şifrelemesi** olmadığında bile şifrelemeyi garanti altına alır. istemci için yapılandırıldı. Ancak, `TrustServerCertificate` istemci yapılandırmasında etkinleştirilmemişse, sağlanan bir sunucu sertifikası yine de gereklidir.  
  
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
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Bir<xref:System.Data.OleDb.OleDbConnection> öğesinin özelliği, Microsoft Access gibi bir OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanak sağlar. Ayrıca, `OleDb` <xref:System.Data.OleDb.OleDbConnectionStringBuilder> sınıfını kullanarak çalışma zamanında bir bağlantı dizesi oluşturabilirsiniz.  
  
### <a name="oledb-connection-string-syntax"></a>OleDb bağlantı dizesi sözdizimi  
 <xref:System.Data.OleDb.OleDbConnection> Bağlantı dizesi için bir sağlayıcı adı belirtmeniz gerekir. Aşağıdaki bağlantı dizesi, Jet Sağlayıcısı kullanılarak bir Microsoft Access veritabanına bağlanır. Veritabanı güvenli değilse `User ID` ( `Password` varsayılan) ve anahtar kelimelerin isteğe bağlı olduğunu unutmayın.  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Jet veritabanının güvenliği, Kullanıcı düzeyinde güvenlik kullanılarak korunuyorsa, çalışma grubu bilgi dosyasının (. mdw) konumunu sağlamanız gerekir. Çalışma grubu bilgi dosyası, bağlantı dizesinde sunulan kimlik bilgilerini doğrulamak için kullanılır.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
> Bir evrensel veri bağlantısı (UDL) dosyasında bir **OleDbConnection** için bağlantı bilgilerini sağlamak mümkündür; Ancak bunu yapmaktan kaçınmalısınız. UDL dosyaları şifrelenmez ve bağlantı dizesi bilgilerini şifresiz metin olarak kullanıma sunar. Bir UDL dosyası uygulamanıza yönelik dış dosya tabanlı bir kaynak olduğundan .NET Framework kullanılarak güvenliği alınamaz. UDL dosyaları **SqlClient**için desteklenmez.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>Access/Jet 'e bağlanmak için DataDirectory kullanma  
 `DataDirectory`, için `SqlClient`özel değildir. Ayrıca, <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> .NET veri sağlayıcılarıyla birlikte kullanılabilir. Aşağıdaki örnek <xref:System.Data.OleDb.OleDbConnection> dize, uygulamanın App_Data klasöründe bulunan Northwind. mdb ' ye bağlanmak için gereken söz dizimini gösterir. Sistem veritabanı (System. mdw) de o konumda depolanır.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
> Erişim/Jet veritabanı güvenli değilse, bağlantı dizesinde sistem veritabanının konumunu belirtmek gerekli değildir. Varsayılan ayar olarak, tüm kullanıcılar yerleşik yönetici kullanıcı olarak boş bir parolayla bağlantı kurarak. Kullanıcı düzeyi güvenlik doğru şekilde uygulansa bile, bir Jet veritabanı saldırılara karşı savunmasız kalır. Bu nedenle, bir erişim/Jet veritabanında gizli bilgilerin depolanması, dosya tabanlı güvenlik düzeninin büyük bir düzeyi nedeniyle önerilmez.  
  
### <a name="connecting-to-excel"></a>Excel 'e bağlanma  
 Microsoft Jet Sağlayıcısı, bir Excel çalışma kitabına bağlanmak için kullanılır. Aşağıdaki bağlantı dizesinde, `Extended Properties` anahtar sözcüğü Excel 'e özgü özellikleri ayarlar. "HDR = Yes;" değeri, ilk satırın sütun adlarını içerdiğini, veri ve "ıMEX = 1;" ise, sürücüye her zaman "karma" veri sütunlarını metin olarak okumasını söyler.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 İçin `Extended Properties` gereken çift tırnak karakterinin Ayrıca çift tırnak işareti içine alınması gerektiğini unutmayın.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Veri şekli sağlayıcısı bağlantı dizesi sözdizimi  
 Microsoft veri şekli `Provider` sağlayıcısını kullanırken `Data Provider` hem hem de anahtar sözcüklerini kullanın. Aşağıdaki örnek, SQL Server yerel bir örneğine bağlanmak için şekil sağlayıcısını kullanır.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>ODBC bağlantı dizeleri  
 Öğesinin özelliği, <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> bir OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanaksağlar.<xref:System.Data.Odbc.OdbcConnection> ODBC bağlantı dizeleri de tarafından <xref:System.Data.Odbc.OdbcConnectionStringBuilder>desteklenir.  
  
 Aşağıdaki bağlantı dizesi Microsoft metin sürücüsünü kullanır.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Visual FoxPro 'ya bağlanmak için DataDirectory kullanma  
 Aşağıdaki <xref:System.Data.Odbc.OdbcConnection> bağlantı dizesi örneği, bir Microsoft `DataDirectory` Visual FoxPro dosyasına bağlanmak için kullanımını gösterir.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle bağlantı dizeleri  
 Öğesinin özelliği, <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> bir OLE DB veri kaynağı için bağlantı dizesi almanıza veya ayarlamanıza olanaksağlar.<xref:System.Data.OracleClient.OracleConnection> Oracle bağlantı dizeleri de tarafından <xref:System.Data.OracleClient.OracleConnectionStringBuilder> desteklenir.  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 ODBC bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı Dizeleri](connection-strings.md)
- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
