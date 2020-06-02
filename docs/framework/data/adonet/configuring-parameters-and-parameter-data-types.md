---
title: Parametreleri ve parametre veri türlerini yapılandırma
description: Komut nesneleri, ADO.NET içinde tür denetimi ve doğrulama sağlayarak SQL deyimlerine veya saklı yordamlara değerler geçirmek için parametreler kullanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: a426eeae785274b0484a84a2fae2dce4572fb4c4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287122"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Parametreleri ve parametre veri türlerini yapılandırma

Komut nesneleri, tür denetimi ve doğrulama sağlamak için değerleri SQL deyimlerine veya saklı yordamlara geçirmek için parametreler kullanır. Komut metninin aksine, parametre girişi, çalıştırılabilir kod olarak değil, değişmez değer olarak değerlendirilir. Bu, bir saldırganın sunucuda güvenlik altına bir SQL bildirimine güvenmesini sağlayan bir komut eklediği "SQL ekleme" saldırılarına karşı koruma sağlamaya yardımcı olur.

Parametreli Komutlar, veritabanı sunucusunun doğru bir önbelleğe alınmış sorgu planıyla gelen komutla doğru bir şekilde eşleştiğinden yardımcı olduklarından sorgu yürütme performansını da iyileştirebilir. Daha fazla bilgi için bkz. [yürütme planı önbelleğe alma ve yeniden kullanma](/sql/relational-databases/query-processing-architecture-guide#execution-plan-caching-and-reuse) ve [Parametreler ve yürütme planı yeniden kullanımı](/sql/relational-databases/query-processing-architecture-guide#PlanReuse). Güvenlik ve performans avantajlarına ek olarak, Parametreli Komutlar bir veri kaynağına geçirilen değerleri düzenlemek için kullanışlı bir yöntem sağlar.

Bir <xref:System.Data.Common.DbParameter> nesnesi, Oluşturucusu kullanılarak veya <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> koleksiyonun yöntemi çağırarak öğesine eklenerek oluşturulabilir `Add` <xref:System.Data.Common.DbParameterCollection> . `Add`Yöntemi, veri sağlayıcısına bağlı olarak, Oluşturucu bağımsız değişkenleri veya var olan bir parametre nesnesi olarak giriş olarak alır.

## <a name="supplying-the-parameterdirection-property"></a>ParameterDirection özelliği sağlama

Parametreleri eklerken, <xref:System.Data.ParameterDirection> Giriş parametrelerinden başka parametreler için bir özellik sağlamalısınız. Aşağıdaki tabloda, `ParameterDirection` numaralandırmada kullanabileceğiniz değerler gösterilmektedir <xref:System.Data.ParameterDirection> .

|Üye adı|Description|
|-----------------|-----------------|
|<xref:System.Data.ParameterDirection.Input>|Parametresi bir giriş parametresidir. Bu varsayılandır.|
|<xref:System.Data.ParameterDirection.InputOutput>|Parametresi hem giriş hem de çıkış gerçekleştirebilir.|
|<xref:System.Data.ParameterDirection.Output>|Parametresi bir çıkış parametresidir.|
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametresi, saklı yordam, yerleşik işlev veya Kullanıcı tanımlı işlev gibi bir işlemden bir dönüş değeri temsil eder.|

## <a name="working-with-parameter-placeholders"></a>Parametre yer tutucuları ile çalışma

Parametre yer tutucuları için sözdizimi veri kaynağına bağlıdır. .NET Framework veri sağlayıcıları, adlandırma ve parametreleri ve parametre yer tutucuları farklı şekilde belirtmeyi işler. Bu söz dizimi, aşağıdaki tabloda açıklandığı gibi belirli bir veri kaynağına özelleştirilir.

|Veri sağlayıcısı|Parametre adlandırma sözdizimi|
|-------------------|-----------------------------|
|<xref:System.Data.SqlClient>|Parametre adı olarak adlandırılmış parametreleri kullanır `@` *parametername*.|
|<xref:System.Data.OleDb>|Bir soru işaretiyle () belirtilen Konumsal parametre işaretçilerini kullanır `?` .|
|<xref:System.Data.Odbc>|Bir soru işaretiyle () belirtilen Konumsal parametre işaretçilerini kullanır `?` .|
|<xref:System.Data.OracleClient>|, `:` *Parmname* (veya *parmname*) biçiminde adlandırılmış parametreleri kullanır.|

## <a name="specifying-parameter-data-types"></a>Parametre veri türlerini belirtme

Bir parametrenin veri türü .NET Framework veri sağlayıcısına özeldir. Türü belirtmek, `Parameter` değerini veri kaynağına geçirmeden önce değerini .NET Framework veri sağlayıcısı türüne dönüştürür. Ayrıca, `Parameter` `DbType` nesnesinin özelliğini belirli bir şekilde ayarlayarak bir genel şekilde türünü de belirtebilirsiniz `Parameter` <xref:System.Data.DbType> .

Bir nesnenin .NET Framework veri sağlayıcısı türü, nesnenin `Parameter` .NET Framework türünden `Value` `Parameter` veya nesnesinin içinden algılanır `DbType` `Parameter` . Aşağıdaki tabloda, `Parameter` değer olarak geçirilen nesneye `Parameter` veya belirtilen değere göre gösterilen tür gösterilmektedir `DbType` .

|.NET Framework türü|DbType|SqlDbType|OleDbType|OdbcType|OracleType|
|-------------------------|------------|---------------|---------------|--------------|----------------|
|<xref:System.Boolean>|Boole|Sürümleri|Boole|Sürümleri|Bayt|
|<xref:System.Byte>|Bayt|Iç|Unsignedtınyıınt|Iç|Bayt|
|Byte []|İkili|İkili. Bayt dizisi, bir VarBinary 'ın 8000 bayt olan en büyük boyutundan daha büyükse bu örtük dönüştürme başarısız olur. 8000 bayttan daha büyük bayt dizileri için, açıkça öğesini ayarlayın <xref:System.Data.SqlDbType> .|Ikili|İkili|Ham|
|<xref:System.Char>| |Bir <xref:System.Data.SqlDbType> char 'ın bir karakter oluşturma işlemi desteklenmez.|Char|Char|Bayt|
|<xref:System.DateTime>|DateTime|DateTime|DBTimeStamp|DateTime|DateTime|
|<xref:System.DateTimeOffset>|DateTimeOffset|SQL Server 2008 ' de DateTimeOffset. <xref:System.Data.SqlDbType>SQL Server 2008 ' den önceki SQL Server sürümlerinde, DateTimeOffset 'den bir|||DateTime|
|<xref:System.Decimal>|Ondalık|Ondalık|Ondalık|Sayısal|Sayı|
|<xref:System.Double>|Çift|Float|Çift|Çift|Çift|
|<xref:System.Single>|Tek|Gerçek|Tek|Gerçek|Float|
|<xref:System.Guid>|Guid|Benzersiz tanımlayıcı|Guid|Benzersiz tanımlayıcı|Ham|
|<xref:System.Int16>|Int16|Small|Small|Small|Int16|
|<xref:System.Int32>|Int32|int|int|int|Int32|
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Sayı|
|<xref:System.Object>|Nesne|Değişken|Değişken|Nesnesinden OdbcType 'ı göstermek desteklenmez.|Blob|
|<xref:System.String>|Dize|NVarChar. Dize, 4000 karakter olan bir NVarChar 'nin en büyük boyutundan daha büyükse bu örtük dönüştürme başarısız olur. 4000 karakterden daha büyük dizeler için, açıkça öğesini ayarlayın <xref:System.Data.SqlDbType> .|VarWChar|NVarChar|NVarChar|
|<xref:System.TimeSpan>|Saat|SQL Server 2008 ' de zaman. Bir <xref:System.Data.SqlDbType> TimeSpan değeri, SQL Server 2008 ' den önceki SQL Server sürümlerinde desteklenmez.|DBTime|Saat|DateTime|
|<xref:System.UInt16>|UInt16|UInt16 'den bir veya daha fazla <xref:System.Data.SqlDbType> destek desteklenmez.|UnsignedSmallInt|int|UInt16|
|<xref:System.UInt32>|UInt32|Bir <xref:System.Data.SqlDbType> UInt32 'den bir, göstermek desteklenmez.|UnsignedInt|BigInt|UInt32|
|<xref:System.UInt64>|UInt64|Bir UInt64 'nin bir veya daha fazla <xref:System.Data.SqlDbType> olması desteklenmiyor.|UnsignedBigInt|Sayısal|Sayı|
||Ansıtring|VarChar|VarChar|VarChar|VarChar|
||AnsiStringFixedLength|Char|Char|Char|Char|
||Para Birimi|Para|Para Birimi|İçinden bir, ' den fazla bir `OdbcType` `Currency` değer erteleme desteklenmez.|Sayı|
||Tarih|SQL Server 2008 ' de tarih. <xref:System.Data.SqlDbType>SQL Server SQL Server 2008 ' den önceki sürümlerde bir from tarihi arasında bir değer olmaması desteklenmez.|DBDate|Tarih|DateTime|
||SByte|Bir SByte 'nin bir listesini göstermek <xref:System.Data.SqlDbType> desteklenmez.|Iç|Bir `OdbcType` SByte 'tan çıkarma desteklenmez.|SByte|
||StringFixedLength|NChar|WChar|NChar|NChar|
||Saat|SQL Server 2008 ' de zaman. <xref:System.Data.SqlDbType>SQL Server SQL Server 2008 ' den önceki sürümlerde bir süre içinde, desteklenmez.|DBTime|Saat|DateTime|
||VarNumeric|<xref:System.Data.SqlDbType>VarNumeric arasında bir değer göstermek desteklenmez.|VarNumeric|`OdbcType`VarNumeric bir değer göstermek desteklenmez.|Sayı|
|Kullanıcı tanımlı tür (içeren bir nesne<xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Sağlayıcıya bağlı olarak nesne veya dize (SqlClient her zaman bir nesne döndürür, ODBC her zaman bir dize döndürür ve OleDb tarafından yönetilen veri sağlayıcısı her birini görebilir|SqlDbType. udt varsa <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> , aksi takdirde varyant|OleDbType. VarWChar (değer null ise), aksi halde OleDbType. VARIANT.|OdbcType. NVarChar|desteklenmiyor|

> [!NOTE]
> Ondalığa diğer türlere dönüştürme, ondalık değeri, en yakın tamsayı değerine doğru yuvarlamak için daraltma dönüştürmelerinde. Dönüştürme sonucu hedef türünde gösterilemeyen bir tablo değilse, bir oluşturulur <xref:System.OverflowException> .

> [!NOTE]
> Sunucuya null bir parametre değeri gönderdiğinizde, <xref:System.DBNull> `null` (Visual Basic) öğesini belirtmeniz gerekir `Nothing` . Sistemdeki null değeri, değeri olmayan boş bir nesnedir. <xref:System.DBNull>null değerleri temsil etmek için kullanılır. Veritabanı boş değerleri hakkında daha fazla bilgi için bkz. [null değerlerini işleme](./sql/handling-null-values.md).

## <a name="deriving-parameter-information"></a>Parametre bilgileri türetme

Parametreler, sınıfı kullanılarak saklı bir yordamdan de türetilebilir `DbCommandBuilder` . Hem `SqlCommandBuilder` hem de `OleDbCommandBuilder` sınıfları, saklı bir `DeriveParameters` yordamdan parametre bilgilerini kullanan bir komut nesnesinin Parameters koleksiyonunu otomatik olarak dolduran statik bir yöntem sağlar. `DeriveParameters`Komutuna ait varolan parametre bilgilerinin üzerine yazar.

> [!NOTE]
> Parametre bilgilerini türeten, bilgilerin alınması için veri kaynağına ek bir gidiş dönüş gerektiğinden, bir performans cezası oluşur. Parametre bilgileri tasarım zamanında biliniyorsa, parametreleri açıkça ayarlayarak uygulamanızın performansını artırabilirsiniz.

Daha fazla bilgi için bkz. [CommandBuilder 'lar Ile komut oluşturma](generating-commands-with-commandbuilders.md).

## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Bir SqlCommand ve saklı yordamla parametreleri kullanma

Saklı yordamlar, veri odaklı uygulamalarda birçok avantaj sunar. Saklı yordamları kullanarak veritabanı işlemleri, en iyi performans için iyileştirilen ve ek güvenlikle geliştirilmiş tek bir komutta kapsüllenebilir. Saklı yordam adının ardından parametre bağımsız değişkenleri bir SQL ifadesiyle geçirilmesiyle bir saklı yordam çağrılabilir ancak, <xref:System.Data.Common.DbCommand.Parameters%2A> ADO.NET nesnesinin koleksiyonunu kullanarak, <xref:System.Data.Common.DbCommand> saklı yordam parametrelerini daha açık bir şekilde tanımlamanıza ve çıkış parametrelerine ve dönüş değerlerine erişebilmenize olanak sağlar.

> [!NOTE]
> Parametreli deyimler, `sp_executesql,` sorgu planı yeniden kullanımına izin veren kullanılarak sunucusunda yürütülür. Toplu işteki yerel imleçler veya değişkenler, `sp_executesql` çağıran toplu işe görünür değildir `sp_executesql` . Veritabanı bağlamındaki değişiklikler yalnızca deyimin sonuna kadar `sp_executesql` . Daha fazla bilgi için bkz. [sp_executesql (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql).

<xref:System.Data.SqlClient.SqlCommand>SQL Server saklı yordamı yürütmek için ile parametreleri kullanılırken, koleksiyona eklenen parametrelerin adları, <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> saklı yordamdaki parametre işaretlerinin adlarıyla eşleşmelidir. SQL Server için .NET Framework Veri Sağlayıcısı, parametreleri bir SQL ifadesine veya saklı yordama geçirmek için soru işareti (?) yer tutucusunu desteklemez. Saklı yordamdaki parametrelere adlandırılmış parametreler olarak davranır ve eşleşen parametre işaretçilerini arar. Örneğin, `CustOrderHist` saklı yordam adlı bir parametre kullanılarak tanımlanır `@CustomerID` . Kodunuz saklı yordamı yürüttüğünde, ayrıca adlı bir parametre da kullanmalıdır `@CustomerID` .

```sql
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)
```

### <a name="example"></a>Örnek

Bu örnek, örnek veritabanında SQL Server saklı yordamının nasıl çağrılacağını gösterir `Northwind` . Saklı yordamın adı `dbo.SalesByCategory` ve `@CategoryName` veri türü olan adlı bir giriş parametresi vardır `nvarchar(15)` . Bu kod, <xref:System.Data.SqlClient.SqlConnection> işlem sona erdiğinde bağlantının atılabilmesi için bir using bloğu içinde yeni bir oluşturur. <xref:System.Data.SqlClient.SqlCommand>Ve <xref:System.Data.SqlClient.SqlParameter> nesneleri oluşturulur ve özellikleri ayarlanır. <xref:System.Data.SqlClient.SqlDataReader>, Öğesini yürütür `SqlCommand` ve, çıktı, konsol penceresinde çıktıyı görüntüleyerek saklı yordamdan sonuç kümesini döndürür.

> [!NOTE]
> `SqlCommand`Ve nesneleri oluşturmak ve `SqlParameter` ardından ayrı deyimlerde özellikleri ayarlamak yerine, tek bir deyimde birden fazla özellik ayarlamak için aşırı yüklenmiş oluşturuculardan birini kullanmayı seçebilirsiniz.

[!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]

## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>OleDbCommand veya OdbcCommand ile parametreleri kullanma

Ya da ile parametreleri kullanırken <xref:System.Data.OleDb.OleDbCommand> <xref:System.Data.Odbc.OdbcCommand> , koleksiyona eklenen parametrelerin sırası, `Parameters` saklı yordamınıza tanımlanan parametrelerin sırasıyla aynı olmalıdır. ODBC için OLE DB ve .NET Framework Veri Sağlayıcısı için .NET Framework Veri Sağlayıcısı, saklı yordamdaki parametreleri yer tutucu olarak değerlendirin ve parametre değerlerini sırasıyla uygulayın. Buna ek olarak, dönüş değeri parametreleri koleksiyona eklenen ilk parametre olmalıdır `Parameters` .

ODBC için OLE DB ve .NET Framework Veri Sağlayıcısı için .NET Framework Veri Sağlayıcısı, parametreleri bir SQL ifadesine veya saklı yordama geçirmek için adlandırılmış parametreleri desteklemez. Bu durumda, aşağıdaki örnekte olduğu gibi soru işareti (?) yer tutucusunu kullanmanız gerekir.

```sql
SELECT * FROM Customers WHERE CustomerID = ?
```

Sonuç olarak, `Parameter` nesnelerin koleksiyona eklendiği sıra `Parameters` , ' nin konumuna doğrudan karşılık gelmelidir mi? parametre için yer tutucu.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar ve Parametreler](commands-and-parameters.md)
- [DataAdapter Parametreleri](dataadapter-parameters.md)
- [ADO.NET’te Veri Türü Eşlemeleri](data-type-mappings-in-ado-net.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
