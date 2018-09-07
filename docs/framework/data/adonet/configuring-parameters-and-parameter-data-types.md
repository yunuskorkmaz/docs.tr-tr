---
title: Yapılandırma parametreleri ve parametre veri türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: 7bb68a7d08d983e93119804db6c1f5a01cd047c9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081281"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Yapılandırma parametreleri ve parametre veri türleri
Komut nesneleri SQL deyimleri ya da saklı yordamlar, tür denetlemesi ve doğrulama sağlayan değerleri geçirmek için parametreleri kullanın. Komut metni parametre girişi yürütülebilir kod olarak değil, değişmez değer olarak kabul edilir. Bu, bu sunucuda ödün güvenlik SQL deyimi içinde bir saldırganın komut ekler "SQL ekleme" saldırılarına karşı önlem yardımcı olur.  
  
 Çünkü bunlar doğru gelen komutu bir uygun önbelleğe alınmış sorgu planı ile aynı veritabanı sunucusu yardımcı parametreli komutların da sorgu yürütme performansı artırır. Daha fazla bilgi için [planlama, yürütme önbelleğe alma ve yeniden](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse) ve [parametreleri ve yürütme planı yeniden](/sql/relational-databases/query-processing-architecture-guide#PlanReuse). Güvenlik ve performans avantajlarına ek olarak, parametreli komutların bir veri kaynağına iletilen değerlere düzenlemek için kullanışlı bir yöntem sağlar.  
  
 A <xref:System.Data.Common.DbParameter> nesne oluşturulabilir, oluşturucu kullanılarak ya da eklemeden <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> çağırarak `Add` yöntemi <xref:System.Data.Common.DbParameterCollection> koleksiyonu. `Add` Yöntemi olarak alacağınız oluşturucu bağımsız değişkenleri veya veri sağlayıcısına bağlı olarak var olan bir parametre nesnesi girin.  
  
## <a name="supplying-the-parameterdirection-property"></a>ParameterDirection özelliği sağlama  
 Parametreleri eklerken, sağlamalısınız bir <xref:System.Data.ParameterDirection> özelliği için giriş parametrelerini farklı parametreler. Aşağıdaki tabloda `ParameterDirection` ile kullanabileceğiniz değerler <xref:System.Data.ParameterDirection> sabit listesi.  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Data.ParameterDirection.Input>|Bir giriş parametresidir. Bu varsayılandır.|  
|<xref:System.Data.ParameterDirection.InputOutput>|Parametresi hem giriş hem de çıkış gerçekleştirebilirsiniz.|  
|<xref:System.Data.ParameterDirection.Output>|Parametre bir çıktı parametresidir.|  
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametre, dönüş değeri bir saklı yordam, yerleşik işlev veya kullanıcı tanımlı işlevi gibi bir işlemi temsil eder.|  
  
## <a name="working-with-parameter-placeholders"></a>Parametre yer tutucuları ile çalışma  
 Parametre yer tutucuları sözdizimi veri kaynağına bağlıdır. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcıları başa adlandırma ve parametreleri ve parametre yer tutucuları farklı belirtme. Bu sözdizimi, aşağıdaki tabloda açıklandığı gibi belirli veri kaynağına özelleştirilir.  
  
|Veri sağlayıcısı|Parametre adlandırma söz dizimi|  
|-------------------|-----------------------------|  
|<xref:System.Data.SqlClient>|Adlı parametreleri biçimde `@` *parametername*.|  
|<xref:System.Data.OleDb>|Bir soru işaretiyle gösterilen konumsal parametre işareti kullanır (`?`).|  
|<xref:System.Data.Odbc>|Bir soru işaretiyle gösterilen konumsal parametre işareti kullanır (`?`).|  
|<xref:System.Data.OracleClient>|Adlı parametreleri biçimde `:` *parmname* (veya *parmname*).|  
  
## <a name="specifying-parameter-data-types"></a>Parametre veri türlerini belirtme  
 Bir parametrenin veri türü için belirli [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı. Değerini dönüştürür türünü belirterek `Parameter` için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri kaynağına değer geçirmeden önce veri sağlayıcısı türü. Türünü de belirtebilirsiniz bir `Parameter` ayarlayarak genel bir şekilde `DbType` özelliği `Parameter` belirli bir nesneye <xref:System.Data.DbType>.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcı türünü bir `Parameter` gelen çıkarılan nesne [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tür `Value` , `Parameter` nesnesi veya `DbType` , `Parameter` nesne. Aşağıdaki tabloda gösterilen gösterilmektedir `Parameter` türüne dayalı olarak geçirilen nesnede `Parameter` değer veya belirtilen `DbType`.  
  
|.NET Framework türü|DbType|SqlDbType|OleDbType|OdbcType|OracleType|  
|-------------------------|------------|---------------|---------------|--------------|----------------|  
|<xref:System.Boolean>|Boole değeri|Bit|Boole değeri|Bit|Bayt|  
|<xref:System.Byte>|Bayt|Mini tamsayı|UnsignedTinyInt|Mini tamsayı|Bayt|  
|bayt]|İkili|VarBinary`.` 8000 bayt olan bayt dizisini ikili, en yüksek boyuttan büyük olması durumunda bu örtülü dönüştürme başarısız olur. 8000 bayt değerinden daha büyük bayt dizileri için açıkça ayarlanmış <xref:System.Data.SqlDbType>.|VarBinary|İkili|Ham|  
|<xref:System.Char>|``|Çıkarımını yapma bir <xref:System.Data.SqlDbType> char desteklenmiyor.|Char|Char|Bayt|  
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|  
|<xref:System.DateTimeOffset>|DateTimeOffset|SQL Server 2008'de DateTimeOffset. Çıkarımını yapma bir <xref:System.Data.SqlDbType> DateTimeOffset SQL Server'ın SQL Server 2008'den önceki sürümlerinde desteklenmez.|||DateTime|  
|<xref:System.Decimal>|Ondalık|Ondalık|Ondalık|Sayısal|Sayı|  
|<xref:System.Double>|Çift|kayan nokta|Çift|Çift|Çift|  
|<xref:System.Single>|Tek|Gerçek|Tek|Gerçek|kayan nokta|  
|<xref:System.Guid>|Guid|Benzersiz tanımlayıcı|Guid|Benzersiz tanımlayıcı|Ham|  
|<xref:System.Int16>|Int16|Tamsayı|Tamsayı|Tamsayı|Int16|  
|<xref:System.Int32>|Int32|int|int|int|Int32|  
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Sayı|  
|<xref:System.Object>|Nesne|Değişken|Değişken|Nesneden bir OdbcType çıkarımını yapma desteklenmiyor.|BLOB|  
|<xref:System.String>|Dize|NVarChar. Dize, 4000 karakter olan bir NVarChar en yüksek boyuttan büyük olması durumunda bu örtülü dönüştürme başarısız olur. 4000 karakterden uzun dizeler için açıkça ayarlanmış <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|  
|<xref:System.TimeSpan>|Zaman|SQL Server 2008'de saat. Çıkarımını yapma bir <xref:System.Data.SqlDbType> TimeSpan SQL Server'ın SQL Server 2008'den önceki sürümlerinde desteklenmez.|DBTime|Zaman|DateTime|  
|<xref:System.UInt16>|UInt16|Çıkarımını yapma bir <xref:System.Data.SqlDbType> UInt16 desteklenmiyor.|UnsignedSmallInt|int|UInt16|  
|<xref:System.UInt32>|UInt32|Çıkarımını yapma bir <xref:System.Data.SqlDbType> UInt32 desteklenmiyor.|unsignedInt|BigInt|UInt32|  
|<xref:System.UInt64>|UInt64|Çıkarımını yapma bir <xref:System.Data.SqlDbType> Uınt64 ' desteklenmiyor.|UnsignedBigInt|Sayısal|Sayı|  
||AnsiString|VarChar|VarChar|VarChar|VarChar|  
||AnsiStringFixedLength|Char|Char|Char|Char|  
|``|Para Birimi|para|Para Birimi|Çıkarımını yapma bir `OdbcType` gelen `Currency` desteklenmiyor.|Sayı|  
|``|Tarih|SQL Server 2008'de tarih. Çıkarımını yapma bir <xref:System.Data.SqlDbType> tarihinden itibaren SQL Server'ın SQL Server 2008'den önceki sürümlerinde desteklenmez.|DBDate|Tarih|DateTime|  
|``|SByte|Çıkarımını yapma bir <xref:System.Data.SqlDbType> SByte desteklenmiyor.|Mini tamsayı|Çıkarımını yapma bir `OdbcType` SByte desteklenmiyor.|SByte|  
||StringFixedLength|nChar|WChar|nChar|nChar|  
||Zaman|SQL Server 2008'de saat. Çıkarımını yapma bir <xref:System.Data.SqlDbType> zamandan SQL Server'ın SQL Server 2008'den önceki sürümlerinde desteklenmez.|DBTime|Zaman|DateTime|  
||VarNumeric|Çıkarımını yapma bir <xref:System.Data.SqlDbType> VarNumeric desteklenmiyor.|VarNumeric|Çıkarımını yapma bir `OdbcType` VarNumeric desteklenmiyor.|Sayı|  
|Kullanıcı tanımlı tür (bir nesne ile <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Nesnesi veya dize, sağlayıcıya bağlı olarak (SqlClient her zaman döndüren bir nesne, Odbc her zaman bir dize döndürür ve OleDb yönetilen veri sağlayıcısı ya da görebilirsiniz.|SqlDbType.Udt varsa <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> olan mevcut, aksi halde değişken|(Değer null ise) OleDbType.VarWChar aksi OleDbType.Variant.|OdbcType.NVarChar|Desteklenmiyor|  
  
> [!NOTE]
>  Ondalık Dönüştürmelere diğer türlere ondalık değeri sıfıra doğru en yakın tam sayı değerine YUVARLA dönüştürmeleri daraltma. Dönüştürmenin sonucu hedef türü içinde gösterilebilir değilse bir <xref:System.OverflowException> oluşturulur.  
  
> [!NOTE]
>  Null parametre değeri sunucuya gönderdiğinizde, belirtmelisiniz <xref:System.DBNull>değil `null` (`Nothing` Visual Basic'te). Null değer sisteminde herhangi bir değer olan boş bir nesnedir. <xref:System.DBNull> Null değerleri temsil etmek için kullanılır. Veritabanı null değerler hakkında daha fazla bilgi için bkz. [boş değerler işleme](../../../../docs/framework/data/adonet/sql/handling-null-values.md).  
  
## <a name="deriving-parameter-information"></a>Parametre bilgileri türetme  
 Parametreler de türetilmiş kullanarak bir saklı yordam `DbCommandBuilder` sınıfı. Hem `SqlCommandBuilder` ve `OleDbCommandBuilder` sınıfları sağlar bir statik yöntem `DeriveParameters`, hangi otomatik olarak dolduran bir saklı yordam parametre bilgilerini kullanan bir komut nesnesi parametreleri koleksiyonu. Unutmayın `DeriveParameters` komutu mevcut tüm parametre bilgilerini üzerine yazar.  
  
> [!NOTE]
>  İlave bir gidiş dönüş bilgileri almak için veri kaynağına gerektiğinden bir performans cezası parametre bilgileri türetme artmasına neden olur. Parametre bilgileri tasarım zamanında biliniyorsa, açıkça parametreleri ayarlayarak uygulamanızın performansını artırabilir.  
  
 Daha fazla bilgi için [CommandBuilders ile komut oluşturma](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>SqlCommand ve bir saklı yordam parametreleri kullanma  
 Saklı yordamlar, veri odaklı uygulamalarda birçok avantaj sunar. Saklı yordamları kullanarak, veritabanı işlemleri tek bir komutta kapsüllenmiş, en iyi performans için iyileştirilmiş ve ek güvenlik ile Gelişmiş. Bir saklı yordam parametre bağımsız değişkenler kullanarak bir SQL deyimi, ardından saklı yordam adı geçirerek de <xref:System.Data.Common.DbCommand.Parameters%2A> koleksiyonunu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.Common.DbCommand> nesne, daha açık saklı tanımlamanıza imkan tanır yordam parametreleri ve çıkış parametreleri erişmek ve dönüş değerleri için.  
  
> [!NOTE]
> Parametreleri deyimleri kullanarak sunucu üzerinde yürütülen `sp_executesql,` için sorgu planı yeniden izin verir. Yerel işaretçiler veya değişkenleri `sp_executesql` batch çağıran toplu görünür değildir `sp_executesql`. Veritabanı bağlamında son için yalnızca en son değişiklikleri `sp_executesql` deyimi. Daha fazla bilgi için [sp_executesql (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql).
  
 Parametrelerle kullanırken bir <xref:System.Data.SqlClient.SqlCommand> bir SQL Server çalıştırmak için saklı yordamı, eklenen parametrelerinin adları <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> koleksiyonu içinde saklı yordam parametre işaretlerinin adları aynı olmalıdır. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için veri sağlayıcısı desteklemiyor soru işareti (?) yer tutucu parametreleri geçirmek için bir SQL deyimi veya saklı yordam için. Bu parametreleri saklı yordamda adlandırılmış parametreler olarak değerlendirir ve parametre işaretçileri eşleştirmek için arar. Örneğin, `CustOrderHist` saklı yordam adlı bir parametre kullanarak tanımlanan `@CustomerID`. Kodunuzu saklı yordamı yürütüldüğünde, ayrıca adlı bir parametre kullanmalısınız `@CustomerID`.  
  
```  
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)  
```  
  
### <a name="example"></a>Örnek  
 Bu örnek bir SQL Server saklı yordam çağırmak nasıl gösterir `Northwind` örnek veritabanı. Saklı yordam adı `dbo.SalesByCategory` ve adlı bir giriş parametresine sahiptir `@CategoryName` veri türüne sahip `nvarchar(15)`. Yeni bir kod oluşturur <xref:System.Data.SqlClient.SqlConnection> iç kullanarak bir engelleme böylece yordamı sona erdiğinde bağlantıyı atıldı. <xref:System.Data.SqlClient.SqlCommand> Ve <xref:System.Data.SqlClient.SqlParameter> nesneleri oluşturulur ve özelliklerini ayarlayın. A <xref:System.Data.SqlClient.SqlDataReader> yürütür `SqlCommand` ve sonuç kümesi saklı yordamdan konsol penceresinde çıktıyı görüntülerken döndürür.  
  
> [!NOTE]
>  Oluşturmak yerine `SqlCommand` ve `SqlParameter` nesneleri ve sonra ayrı deyimlerinde özelliklerini ayarlayarak, bunun yerine seçebilirsiniz aşırı yüklü oluşturucular biri tek bir deyimde birden çok özelliği ayarlamak için kullanılacak.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Bir OleDbCommand ya da OdbcCommand parametrelerini kullanma  
 Parametrelerle kullanırken bir <xref:System.Data.OleDb.OleDbCommand> veya <xref:System.Data.Odbc.OdbcCommand>, eklenen parametrelerinin sırasını `Parameters` koleksiyonu, depolanmış yordamınızdaki tanımlanan parametrelerin sırasını eşleşmesi gerekir. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] OLE DB için veri sağlayıcısı ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı parametreleri saklı yordam, yer tutucu olarak kabul et ve parametre değerlerini sırayla uygulayın. Ayrıca, eklenen ilk parametre değeri parametreleri olmalıdır döndürür `Parameters` koleksiyonu.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] OLE DB için veri sağlayıcısı ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ODBC için veri sağlayıcısı desteklemez adlandırılmış parametreler için bir SQL deyimi veya saklı yordam parametreleri geçirmek için. Bu durumda, aşağıdaki örnekte olduğu gibi soru işareti (?) yer tutucu kullanmanız gerekir.  
  
```  
SELECT * FROM Customers WHERE CustomerID = ?  
```  
  
 Sonuç olarak, bir sırayı `Parameter` nesneleri eklenir `Parameters` koleksiyon konumuna doğrudan gelmelidir? parametresi için yer tutucu.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
