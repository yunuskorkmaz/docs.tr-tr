---
title: "Bağlantı dizesi sözdizimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9c7edc59ecb71c4b201b77c993fc839f5700abe3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="connection-string-syntax"></a>Bağlantı dizesi sözdizimi
Her .NET Framework veri sağlayıcısı sahip bir `Connection` devraldığı nesne <xref:System.Data.Common.DbConnection> sağlayıcıya özgü yanı sıra <xref:System.Data.Common.DbConnection.ConnectionString%2A> özelliği. Her bir sağlayıcı için belirli bağlantı dizesi sözdizimi belgelenen kendi `ConnectionString` özelliği. .NET Framework dahil dört veri sağlayıcıları aşağıdaki tabloda listelenmektedir.  
  
|.NET framework veri sağlayıcısı|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|Veri erişimi için Microsoft SQL Server sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.|  
|<xref:System.Data.OleDb>|OLE DB kullanılarak kullanıma sunulan veri kaynakları için veri erişim sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz: <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.|  
|<xref:System.Data.Odbc>|ODBC kullanılarak kullanıma sunulan veri kaynakları için veri erişim sağlar. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz: <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.|  
|<xref:System.Data.OracleClient>|Sürüm 8.1.7 Oracle için veri erişim sağlar ya da daha sonra. Bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz: <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.|  
  
## <a name="connection-string-builders"></a>Bağlantı dizesi oluşturucular  
 ADO.NET 2.0, .NET Framework veri sağlayıcısı için aşağıdaki bağlantı dizesi oluşturucular kullanıma sunuldu.  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 Bağlantı dizesi oluşturucular kodunuzdaki bağlantı dizesi değerlerini el ile birleştirme gerekmez şekilde sözdizimsel olarak geçerli bağlantı dizeleri çalışma zamanında oluşturmanıza olanak sağlar. Daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="windows-authentication"></a>Windows Kimlik Doğrulaması  
 Windows kimlik doğrulaması kullanmanızı öneririz (bazen denir *tümleşik güvenlik*) destekleyen veri kaynaklarına bağlanmak için. Bağlantı dizesinde değişiklik sözdizimi sağlayıcıya göre değişir. Aşağıdaki tabloda, .NET Framework veri sağlayıcıları ile kullanılan Windows kimlik doğrulaması sözdizimi gösterilmektedir.  
  
|Sağlayıcı|Sözdizimi|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  `Integrated Security=true`ile kullanıldığında bir özel durum oluşturur `OleDb` sağlayıcısı.  
  
## <a name="sqlclient-connection-strings"></a>SqlClient bağlantı dizeleri  
 Sözdizimi bir <xref:System.Data.SqlClient.SqlConnection> bağlantı dizesi içinde belgelenmiştir <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> özelliği. Kullanabileceğiniz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> almak veya bir SQL Server veritabanı için bağlantı dizesini ayarlamak için özellik. SQL Server'ın önceki bir sürüme bağlanmak gerekiyorsa, .NET Framework veri sağlayıcısı için OleDb kullanmanız gerekir (<xref:System.Data.OleDb>). Çoğu bağlantı dizesi anahtar sözcükleri özelliklerinde de Eşle <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Windows kimlik doğrulaması her sözdizimi aşağıdaki biçimlerden birini bağlanmak için kullanacağı **AdventureWorks** yerel bir sunucuda veritabanı.  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-logins"></a>SQL Server Logins  
 Windows kimlik doğrulaması SQL Server'a bağlanmak için tercih edilir. Ancak, SQL Server kimlik doğrulaması gerekiyorsa, bir kullanıcı adı ve parola belirtmek için aşağıdaki sözdizimini kullanın. Bu örnekte, yıldız işareti, geçerli bir kullanıcı adı ve parola göstermek için kullanılır.  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  
  
> [!IMPORTANT]
>  İçin varsayılan ayar `Persist Security Info` anahtar sözcüğü `false`. Ayar `true` veya `yes` kullanıcı kimliği ve parolası, bağlantı açıldıktan sonra bağlantısından elde gibi güvenlik bakımından hassas bilgiler sağlar. Tutmak `Persist Security Info` kümesine `false` güvenilmeyen bir kaynağa hassas bağlantı dizesi bilgilere erişimi olmadığından emin olmak için.  
  
 SQL Server'ın adlandırılmış bir örneğine bağlanmak için *sunucu adı\örnek adı* sözdizimi.  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
  
 Ayrıca ayarlayabilirsiniz <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> özelliği `SqlConnectionStringBuilder` bir bağlantı dizesi oluştururken örnek adı. <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> Özelliği bir <xref:System.Data.SqlClient.SqlConnection> nesne salt okunur.  
  
> [!NOTE]
>  Windows kimlik doğrulaması SQL Server oturumları önceliklidir. Her iki tümleşik güvenliği belirtmek iyi bir kullanıcı adı ve parola, kullanıcı adı ve parola yoksayılacak ve Windows kimlik doğrulaması kullanılacak şekilde = true.  
  
### <a name="type-system-version-changes"></a>Tür sistemi sürüm değişiklikleri  
 `Type System Version` İn anahtar sözcüğü bir <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> istemci-tarafı gösterimini belirtir [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] türleri. Bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> hakkında daha fazla bilgi için `Type System Version` anahtar sözcüğü.  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>Kullanıcı örnekleri Express bağlanma ve SQL Server ekleme  
 Kullanıcı örnekleri, SQL Server Express için kullanılan bir özelliğidir. Ekleme ve bir SQL Server veritabanı yönetici ayrıcalıklarına gerek duymadan çalıştırmak bir en az ayrıcalıklı yerel Windows hesabı üzerinde çalışan bir kullanıcı sağlarlar. Bir kullanıcı örneği bir hizmet olarak değil kullanıcının Windows kimlik bilgileriyle yürütür.  
  
 Kullanıcı örnekleri ile çalışma hakkında daha fazla bilgi için bkz: [SQL Server Express kullanıcı örnekleri](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).  
  
## <a name="using-trustservercertificate"></a>TrustServerCertificate kullanma  
 `TrustServerCertificate` Anahtar sözcüğü, yalnızca bağlanırken geçerli bir [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] örneği geçerli bir sertifika ile. Zaman `TrustServerCertificate` ayarlanır `true`, Aktarım katmanı kanalını şifrelemek ve güven doğrulamak için sertifika zinciri taramasını atlamak için SSL kullanır.  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  Varsa `TrustServerCertificate` ayarlanır `true` ve şifreleme açıktır, sunucuda belirtilen şifreleme düzeyini kullanılacak olsa bile `Encrypt` ayarlanır `false` bağlantı dizesinde. Aksi takdirde bağlantı başarısız olur.  
  
### <a name="enabling-encryption"></a>Şifrelemeyi etkinleştirme  
 Sunucuda bir sertifika sağlanmamıştır şifrelemeyi etkinleştirmek için **zorla protokol şifrelemesi** ve **sunucu sertifika güven** seçenekleri, SQL Server Yapılandırma Yöneticisi'nde ayarlanmış olması gerekir. Doğrulanabilen sertifika sunucuda sağlanan bu durumda, şifreleme doğrulama olmadan otomatik olarak imzalanan sunucu sertifikasını kullanır.  
  
 Uygulama ayarları, SQL Server'da yapılandırılmış güvenlik düzeyini indiremezsiniz ancak isteğe bağlı olarak artırabilir. Bir uygulama ayarlayarak şifreleme isteyebilir `TrustServerCertificate` ve `Encrypt` anahtar sözcükler `true`, hatta bir sunucu sertifikası sağlanmayan olduğunda şifreleme gerçekleşir olduğunu güvence altına alır ve **zorla protokol şifrelemesi**  istemci için yapılandırılmamış. Ancak, varsa `TrustServerCertificate` etkin istemci yapılandırmasında sağlanan sunucu sertifikası hala gereklidir.  
  
 Aşağıdaki tabloda tüm durumlarda açıklanmaktadır.  
  
|Protokol şifrelemesi istemci ayarı zorla|Sunucu sertifikası istemci ayarı güven|Veri bağlantı dizesi/özniteliği için şifreleme kullan şifreleme|Sunucu sertifikası bağlantı dizesi/özniteliği güven|Sonuç|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|Hayır|Yok|Hayır (varsayılan)|Yoksayıldı|Şifreleme oluşur.|  
|Hayır|Yok|Evet|Hayır (varsayılan)|Yalnızca bağlantı denemesi başarısız doğrulanabilen sunucu sertifikası, aksi takdirde ise şifreleme oluşur.|  
|Hayır|Yok|Evet|Evet|Yalnızca bağlantı denemesi başarısız doğrulanabilen sunucu sertifikası, aksi takdirde ise şifreleme oluşur.|  
|Evet|Hayır|Yoksayıldı|Yoksayıldı|Yalnızca bağlantı denemesi başarısız doğrulanabilen sunucu sertifikası, aksi takdirde ise şifreleme oluşur.|  
|Evet|Evet|Hayır (varsayılan)|Yoksayıldı|Yalnızca bağlantı denemesi başarısız doğrulanabilen sunucu sertifikası, aksi takdirde ise şifreleme oluşur.|  
|Evet|Evet|Evet|Hayır (varsayılan)|Yalnızca bağlantı denemesi başarısız doğrulanabilen sunucu sertifikası, aksi takdirde ise şifreleme oluşur.|  
|Evet|Evet|Evet|Evet|Yalnızca bağlantı denemesi başarısız doğrulanabilen sunucu sertifikası, aksi takdirde ise şifreleme oluşur.|  
  
 Daha fazla bilgi için bkz: [kullanarak şifreleme olmadan doğrulama](http://go.microsoft.com/fwlink/?LinkId=120500) SQL Server Books Online.  
  
## <a name="oledb-connection-strings"></a>OleDb bağlantı dizeleri  
 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> Özelliği bir <xref:System.Data.OleDb.OleDbConnection> almak veya Microsoft Access gibi bir OLE DB veri kaynağı için bir bağlantı dizesini ayarlamak sağlar. Ayrıca bir `OleDb` bağlantı dizesi kullanarak çalışma zamanında <xref:System.Data.OleDb.OleDbConnectionStringBuilder> sınıfı.  
  
### <a name="oledb-connection-string-syntax"></a>OleDb bağlantı dizesi sözdizimi  
 İçin bir sağlayıcı adı belirtmeniz gerekir bir <xref:System.Data.OleDb.OleDbConnection> bağlantı dizesi. Aşağıdaki bağlantı dizesi Jet sağlayıcısını kullanarak bir Microsoft Access veritabanına bağlar. Unutmayın `UserID` ve `Password` anahtar sözcükler (varsayılan) veritabanı güvenli, isteğe bağlı.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 Kullanıcı düzeyinde güvenlik kullanarak Jet veritabanı güvenliği, çalışma grubu bilgi dosyasının (.mdw) konumunu sağlamanız gerekir. Çalışma grubu bilgi dosyası bağlantı dizesinde sunulan kimlik bilgilerini doğrulamak için kullanılır.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  Bağlantı bilgilerini sağlamak olası bir **OleDbConnection** evrensel veri bağlantısı (UDL) dosyasında; Bununla birlikte, kaçının Bunun yapılması. UDL dosyaları şifrelenmez ve düz metin bağlantı dizesi bilgilerini kullanıma sunar. Dış dosya tabanlı kaynak uygulamanıza UDL dosyası olduğu için .NET Framework kullanılarak korunamıyor. UDL dosyaları için desteklenmiyor **SqlClient**.  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>DataDirectory erişim/Jet bağlanmak için kullanma  
 `DataDirectory`Özel değil `SqlClient`. İle de kullanılabilir <xref:System.Data.OleDb> ve <xref:System.Data.Odbc> .NET veri sağlayıcısı. Aşağıdaki örnek <xref:System.Data.OleDb.OleDbConnection> dize uygulamanın app_data klasöründe Northwind.mdb bağlanmak için gereken sözdizimi gösterilmektedir. Sistem veritabanı (System.mdw) de söz konusu konumda depolanır.  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  Bağlantı dizesinde sistem veritabanı konumunu belirten, erişim/Jet veritabanı güvenli değilse gerekli değildir. Güvenlik varsayılan olarak, boş bir parolaya sahip yerleşik yönetici kullanıcı olarak bağlanma tüm kullanıcılarla kapalıdır. Hatta kullanıcı düzeyinde güvenlik düzgün şekilde uygulandığında, Jet veritabanı saldırıya açık kalır. Bu nedenle, bir erişim/Jet veritabanı hassas bilgileri depolamak, dosya tabanlı güvenlik şeması devralınmış zayıflık nedeniyle önerilmez.  
  
### <a name="connecting-to-excel"></a>Excel'e bağlanma  
 Microsoft Jet Sağlayıcısı, bir Excel çalışma kitabı bağlanmak için kullanılır. Aşağıdaki bağlantı dizesinde `Extended Properties` anahtar sözcüğü Excel'e özgü özelliklerini ayarlar. "HDR = Yes;" ilk satırı sütun adları, verileri değil, içerdiğini belirtir ve "IMEX = 1;" her zaman "intermixed" veri sütunlarını metin olarak okumak için sürücü söyler.  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 Çift tırnak karakteri gerekli Not `Extended Properties` da çift tırnak içine alınmalıdır.  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Veri Şekli Sağlayıcısı bağlantı dizesi sözdizimi  
 Her ikisini de kullanmanız `Provider` ve `Data Provider` Microsoft Veri Şekli Sağlayıcısı kullanırken anahtar sözcükler. Aşağıdaki örnek, yerel bir SQL Server örneğine bağlanmak için Şekil sağlayıcısı kullanır.  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>ODBC bağlantı dizeleri  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> Özelliği bir <xref:System.Data.Odbc.OdbcConnection> almak veya ayarlamak için bir OLE DB veri kaynağı bir bağlantı dizesi olanak tanır. ODBC bağlantı dizeleri tarafından da desteklenir <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.  
  
 Aşağıdaki bağlantı dizesini Microsoft Metin sürücüsü kullanır.  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>Visual FoxPro bağlanmak için DataDirectory kullanma  
 Aşağıdaki <xref:System.Data.Odbc.OdbcConnection> bağlantı dizesi örneği gösterir kullanarak `DataDirectory` bir Microsoft Visual FoxPro dosyasına bağlanmak için.  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle bağlantı dizeleri  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> Özelliği bir <xref:System.Data.OracleClient.OracleConnection> almak veya ayarlamak için bir OLE DB veri kaynağı bir bağlantı dizesi olanak tanır. Oracle bağlantı dizeleri tarafından da desteklenir <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 ODBC bağlantı dizesi sözdizimi hakkında daha fazla bilgi için bkz: <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
