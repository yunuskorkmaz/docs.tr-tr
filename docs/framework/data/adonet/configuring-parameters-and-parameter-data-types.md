---
title: Yapılandırma parametreleri ve parametre veri türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: 320a45af1c2f3b460c23d8320c456120643902f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759549"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Yapılandırma parametreleri ve parametre veri türleri
Komut nesneleri parametreleri SQL deyimlerini ya da tür denetleme ve doğrulama sağlayan saklı yordamlar için değerleri geçirmek için kullanın. Komut metni parametre girişini yürütülebilir kod olarak değil, sabit değer olarak kabul edilir. Bu, bu sunucuda güvenlik ihlalleri güvenlik SQL deyimi içine bir saldırganın komut ekler "SQL ekleme" saldırılarına karşı koruma yardımcı olur.  
  
 Çünkü doğru gelen komutu uygun önbelleğe alınmış sorgu planı ile eşleşecek veritabanı sunucusu yardımcı parametreli komutlar da sorgu yürütme performansını iyileştirebilir. Daha fazla bilgi için bkz: [planlama yürütme önbelleğe alma ve yeniden](http://go.microsoft.com/fwlink/?LinkId=120424) ve [parametreleri ve yürütme planı yeniden](http://go.microsoft.com/fwlink/?LinkId=120423) SQL Server Books Online. Güvenlik ve performans yararlar yanı sıra, parametreli komutlar bir veri kaynağına geçirilen değerlerini düzenlemek için kullanışlı bir yöntem sağlar.  
  
 A <xref:System.Data.Common.DbParameter> nesne, kendi oluşturucusunu kullanarak veya eklemeyi oluşturulabilir <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> çağırarak `Add` yöntemi <xref:System.Data.Common.DbParameterCollection> koleksiyonu. `Add` Yöntemi olarak sürer oluşturucu bağımsız değişkenleri veya veri sağlayıcısı bağlı olarak var olan bir parametre nesnesi girin.  
  
## <a name="supplying-the-parameterdirection-property"></a>ParameterDirection özelliği sağlama  
 Parametreleri eklerken sağlamalısınız bir <xref:System.Data.ParameterDirection> giriş parametreleri dışında parametreleri için özelliği. Aşağıdaki tabloda `ParameterDirection` ile birlikte kullanabileceğiniz değerleri <xref:System.Data.ParameterDirection> numaralandırması.  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Data.ParameterDirection.Input>|Bir giriş parametresidir. Bu varsayılandır.|  
|<xref:System.Data.ParameterDirection.InputOutput>|Parametresi giriş ve çıkış gerçekleştirebilirsiniz.|  
|<xref:System.Data.ParameterDirection.Output>|Bir çıkış parametresidir.|  
|<xref:System.Data.ParameterDirection.ReturnValue>|Saklı yordam, yerleşik işlevi veya kullanıcı tanımlı işlev gibi bir işlem parametresi dönüş değeri temsil eder.|  
  
## <a name="working-with-parameter-placeholders"></a>Parametre yer tutucuları ile çalışma  
 Parametre yer tutucuları sözdizimi veri kaynağına bağlıdır. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcıları işlemek adlandırma ve parametreleri ve parametre yer tutucuları farklı belirtme. Bu sözdizimi, aşağıdaki tabloda açıklandığı gibi belirli veri kaynağına özelleştirilir.  
  
|Veri sağlayıcısı|Parametre adlandırma söz dizimi|  
|-------------------|-----------------------------|  
|<xref:System.Data.SqlClient>|Adlı parametre biçimde kullanır `@` *parametername*.|  
|<xref:System.Data.OleDb>|Bir soru işaretiyle gösterilen konumsal parametre işaretçileri kullanır (`?`).|  
|<xref:System.Data.Odbc>|Bir soru işaretiyle gösterilen konumsal parametre işaretçileri kullanır (`?`).|  
|<xref:System.Data.OracleClient>|Adlı parametre biçimde kullanır `:` *parmname* (veya *parmname*).|  
  
## <a name="specifying-parameter-data-types"></a>Parametre veri türlerini belirtme  
 Parametre veri türü için belirli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı. Türünü belirtme değerine dönüştürür `Parameter` için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri kaynağına değer geçirmeden önce veri sağlayıcısı türü. Türünü de belirtebilir bir `Parameter` ayarlayarak genel bir şekilde `DbType` özelliği `Parameter` belirli bir nesneye <xref:System.Data.DbType>.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcı türü bir `Parameter` nesne olayla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü `Value` , `Parameter` nesnesi veya `DbType` , `Parameter` nesnesi. Aşağıdaki tabloda oluşturulursa gösterilmektedir `Parameter` türüne dayalı olarak geçirilen nesnesi üzerinde `Parameter` değer veya belirtilen `DbType`.  
  
|.NET Framework türü|DbType|SqlDbType|OleDbType|OdbcType|OracleType|  
|-------------------------|------------|---------------|---------------|--------------|----------------|  
|<xref:System.Boolean>|Boole değeri|bit|Boole değeri|bit|Bayt|  
|<xref:System.Byte>|Bayt|Mini tamsayı|UnsignedTinyInt|Mini tamsayı|Bayt|  
|Byte]|İkili|VarBinary`.` bayt dizisi 8000 bayt olduğu bir VarBinary en büyük boyuttan daha büyükse bu örtük dönüştürme başarısız olur. 8000 bayttan büyük bayt dizileri için açık olarak ayarlanıp <xref:System.Data.SqlDbType>.|VarBinary|İkili|Ham|  
|<xref:System.Char>|``|Çıkarımını yapma bir <xref:System.Data.SqlDbType> char desteklenmiyor.|Char|Char|Bayt|  
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|  
|<xref:System.DateTimeOffset>|DateTimeOffset|SQL Server 2008'de DateTimeOffset. Çıkarımını yapma bir <xref:System.Data.SqlDbType> DateTimeOffset SQL Server 2008'den önceki SQL Server sürümlerinde desteklenmez.|||DateTime|  
|<xref:System.Decimal>|Ondalık|Ondalık|Ondalık|sayısal|Sayı|  
|<xref:System.Double>|Çift|Kayan nokta|Çift|Çift|Çift|  
|<xref:System.Single>|Tek|Gerçek|Tek|Gerçek|Kayan nokta|  
|<xref:System.Guid>|Guid|Benzersiz tanımlayıcı|Guid|Benzersiz tanımlayıcı|Ham|  
|<xref:System.Int16 >|Int16|Tamsayı|Tamsayı|Tamsayı|Int16|  
|<xref:System.Int32>|Int32|int|int|int|Int32|  
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Sayı|  
|<xref:System.Object>|Nesne|Değişken|Değişken|Nesneden bir OdbcType çıkarımını yapma desteklenmiyor.|BLOB|  
|<xref:System.String>|Dize|NVarChar. Dize 4000 karakterdir bir NVarChar en büyük boyuttan daha büyükse bu örtük dönüştürme başarısız olur. 4000 karakterden daha büyük olan dizeleri için açık olarak ayarlanıp <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|  
|<xref:System.TimeSpan>|Zaman|SQL Server 2008 süre. Çıkarımını yapma bir <xref:System.Data.SqlDbType> TimeSpan SQL Server 2008'den önceki SQL Server sürümlerinde desteklenmez.|DBTime|Zaman|DateTime|  
|<xref:System.UInt16>|UInt16|Çıkarımını yapma bir <xref:System.Data.SqlDbType> UInt16 desteklenmiyor.|UnsignedSmallInt|int|UInt16|  
|<xref:System.UInt32>|UInt32|Çıkarımını yapma bir <xref:System.Data.SqlDbType> UInt32 desteklenmiyor.|unsignedInt|BigInt|UInt32|  
|<xref:System.UInt64>|UInt64|Çıkarımını yapma bir <xref:System.Data.SqlDbType> UInt64 desteklenmiyor.|UnsignedBigInt|sayısal|Sayı|  
||AnsiString|VarChar|VarChar|VarChar|VarChar|  
||AnsiStringFixedLength|Char|Char|Char|Char|  
|``|Para Birimi|para|Para Birimi|Çıkarımını yapma bir `OdbcType` gelen `Currency` desteklenmiyor.|Sayı|  
|``|Tarih|SQL Server 2008'de tarih. Çıkarımını yapma bir <xref:System.Data.SqlDbType> tarihinden SQL Server 2008'den önceki SQL Server sürümlerinde desteklenmez.|DBDate|Tarih|DateTime|  
|``|SByte|Çıkarımını yapma bir <xref:System.Data.SqlDbType> SByte desteklenmiyor.|Mini tamsayı|Çıkarımını yapma bir `OdbcType` SByte desteklenmiyor.|SByte|  
||StringFixedLength|NChar|WChar|NChar|NChar|  
||Zaman|SQL Server 2008 süre. Çıkarımını yapma bir <xref:System.Data.SqlDbType> zamandan SQL Server 2008'den önceki SQL Server sürümlerinde desteklenmez.|DBTime|Zaman|DateTime|  
||VarNumeric|Çıkarımını yapma bir <xref:System.Data.SqlDbType> VarNumeric desteklenmiyor.|VarNumeric|Çıkarımını yapma bir `OdbcType` VarNumeric desteklenmiyor.|Sayı|  
|Kullanıcı tanımlı tür (sahip bir nesne <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Nesne veya dize, sağlayıcı bağlı olarak (SqlClient her zaman döndüren bir nesne, Odbc her zaman bir dize döndürür ve OleDb yönetilen veri sağlayıcısı ya da görebilirsiniz|SqlDbType.Udt varsa <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> olan mevcut, aksi takdirde değişken|(Değer null ise) OleDbType.VarWChar aksi OleDbType.Variant.|OdbcType.NVarChar|Desteklenmiyor|  
  
> [!NOTE]
>  Ondalık değeri sıfıra doğru en yakın tam sayı değerine YUVARLA dönüşümleri daraltma ondalık gelen bir dönüşümleri diğer türleri için. Dönüştürme işleminin sonucu hedef türü gösterilebilir değilse, bir <xref:System.OverflowException> oluşturulur.  
  
> [!NOTE]
>  Sunucuya bir null parametre değeri gönderdiğinizde belirtmelisiniz <xref:System.DBNull>değil `null` (`Nothing` Visual Basic'te). Null değer sisteminde değeri yok boş bir nesnedir. <xref:System.DBNull> Null değerleri temsil etmek için kullanılır. Veritabanı null değerler hakkında daha fazla bilgi için bkz: [boş değerler işleme](../../../../docs/framework/data/adonet/sql/handling-null-values.md).  
  
## <a name="deriving-parameter-information"></a>Parametre bilgileri türetme  
 Parametreler de türetilmiş kullanarak bir saklı yordam `DbCommandBuilder` sınıfı. Hem `SqlCommandBuilder` ve `OleDbCommandBuilder` sınıfları statik bir yöntem sunar `DeriveParameters`, hangi otomatik olarak dolduran bir saklı yordamdan parametre bilgilerini kullanan bir komut nesnesi parametreleri topluluğu. Unutmayın `DeriveParameters` komutu mevcut tüm parametre bilgilerini üzerine yazar.  
  
> [!NOTE]
>  Bir ek gidiş dönüş bilgileri almak için veri kaynağına gerektirdiğinden parametre bilgilerini türetme performans cezası doğurur. Parametre bilgileri tasarım zamanında biliniyorsa parametreleri açıkça ayarlayarak, uygulamanızın performansını artırabilir.  
  
 Daha fazla bilgi için bkz: [CommandBuilders oluşturma komutlarıyla](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Parametreleri bir SqlCommand ve saklı yordam ile kullanma  
 Saklı yordamlar veri tabanlı uygulamalarda birçok avantaj sunar. Saklı yordamları kullanarak, veritabanı işlemleri içinde tek bir komut kapsüllenmiş, en iyi performans için en iyi duruma getirilmiş ve Gelişmiş ile ek güvenlik. Saklı yordam kullanarak bir SQL deyimi, parametre bağımsız değişkenlerini tarafından izlenen saklı yordam adı geçirerek çağrılabilir rağmen <xref:System.Data.Common.DbCommand.Parameters%2A> koleksiyonu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.Common.DbCommand> nesne daha açıkça saklı tanımlamanızı sağlar yordam parametreleri, çıktı parametreleri erişmek ve dönüş değerleri.  
  
> [!NOTE]
>  Parametreleri deyimleri kullanarak sunucu üzerinde yürütülen `sp_executesql,` için sorgu planı yeniden kullanılmasını sağlar. Yerel imleçleri veya değişkenleri `sp_executesql` toplu çağıran toplu görünür olmayan `sp_executesql`. Veritabanı bağlamında yalnızca sonuna kadar en son değişiklikleri `sp_executesql` deyimi. Daha fazla bilgi için SQL Server Books Online'a bakın.  
  
 Parametreler ile kullanıldığında bir <xref:System.Data.SqlClient.SqlCommand> saklı yordamı, eklenen parametrelerinin adları bir SQL Server yürütme <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> toplama saklı yordamı parametre işaretlerinde adları aynı olmalıdır. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server desteği yok soru işareti (?) yer tutucu bir SQL deyimi veya saklı yordam parametreleri geçirme. Parametreleri saklı yordam, adlandırılmış parametreleri olarak değerlendirir ve parametre işaretçileri eşleştirmek için arar. Örneğin, `CustOrderHist` saklı yordam adlı bir parametre kullanarak tanımlanmış `@CustomerID`. Kodunuzu saklı yordamı yürütüldüğünde, ayrıca adlı bir parametre kullanmalısınız `@CustomerID`.  
  
```  
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)  
```  
  
### <a name="example"></a>Örnek  
 Bu örnek bir SQL Server saklı yordam nasıl çağırılacağını `Northwind` örnek veritabanı. Saklı yordam adı `dbo.SalesByCategory` ve adlı bir giriş parametresi sahip `@CategoryName` veri türüne sahip `nvarchar(15)`. Yeni bir kod oluşturur <xref:System.Data.SqlClient.SqlConnection> iç kullanarak bir engelleme böylece yordamı sona erdiğinde bağlantıyı atıldı. <xref:System.Data.SqlClient.SqlCommand> Ve <xref:System.Data.SqlClient.SqlParameter> nesneler oluşturulur ve bunların özelliklerini ayarlayın. A <xref:System.Data.SqlClient.SqlDataReader> yürütür `SqlCommand` ve sonuç çıkış konsol penceresinde görüntüleme saklı yordamdan kümesini döndürür.  
  
> [!NOTE]
>  Oluşturmak yerine `SqlCommand` ve `SqlParameter` nesneleri ve ardından Özellikler ayrı deyimlerinde ayarını etkinleştirirseniz, bunun yerine seçmediğiniz aşırı yüklenmiş oluşturuculardan birine tek bir deyimde birden çok özelliği ayarlamak için kullanılacak.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Parametreleri OleDbCommand ya da OdbcCommand ile kullanma  
 Parametreler ile kullanıldığında bir <xref:System.Data.OleDb.OleDbCommand> veya <xref:System.Data.Odbc.OdbcCommand>, eklenen parametreleri sırasını `Parameters` toplama saklı yordamda tanımlanan parametrelerin sırasını eşleşmesi gerekir. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin OLE DB veri sağlayıcısı ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı yer tutucu olarak bir saklı yordam parametreleri kabul ve parametre değerlerini sırayla uygulayın. Ayrıca, değer parametreleri eklenen ilk parametre olmalıdır dönmek `Parameters` koleksiyonu.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İçin OLE DB veri sağlayıcısı ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı desteklemez adlandırılmış parametreleri bir SQL deyimi veya saklı yordam parametreleri geçirme. Bu durumda, aşağıdaki örnekte olduğu gibi soru işareti (?) yer tutucu kullanmanız gerekir.  
  
```  
SELECT * FROM Customers WHERE CustomerID = ?  
```  
  
 Sonuç olarak, hangi sırayla `Parameter` nesneleri eklenir `Parameters` koleksiyonu konumuna doğrudan karşılık gerekir? parametre için yer tutucu.  
  
### <a name="oledb-example"></a>OleDb örneği  
  
```vb  
Dim command As OleDbCommand = New OleDbCommand( _  
  "SampleProc", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OleDbParameter = command.Parameters.Add( _  
  "RETURN_VALUE", OleDbType.Integer)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OleDbType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OleDbType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OleDbCommand command = new OleDbCommand("SampleProc", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OleDbParameter parameter = command.Parameters.Add(  
  "RETURN_VALUE", OleDbType.Integer);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@InputParm", OleDbType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add(  
  "@OutputParm", OleDbType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="odbc-example"></a>ODBC örneği  
  
```vb  
Dim command As OdbcCommand = New OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OdbcParameter = command.Parameters.Add("RETURN_VALUE", OdbcType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OdbcCommand command = new OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OdbcParameter parameter = command.Parameters.Add( _  
  "RETURN_VALUE", OdbcType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapter Parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
