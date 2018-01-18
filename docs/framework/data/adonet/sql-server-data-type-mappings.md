---
title: "SQL Server veri türü eşlemeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fafdc31a-f435-4cd3-883f-1dfadd971277
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 76343b75f09a3aa007a955b0ee869d1dcf1146aa
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-data-type-mappings"></a>SQL Server veri türü eşlemeleri
SQL Server ve .NET Framework farklı tür sistemlerde temel alır. Örneğin, .NET Framework <xref:System.Decimal> yapısının 28, en fazla ölçeğini kullanırken SQL Server ondalık ve sayısal veri türleri 38 maksimum ölçeğini vardır. Veri, okuma ve yazma, veri bütünlüğünü sağlamak için <xref:System.Data.SqlClient.SqlDataReader> çıkarır SQL Server'a özel yazılan nesnelerin dönüş erişimci yöntemleri <xref:System.Data.SqlTypes> .NET Framework dönüş erişimci yöntemleri yanı sıra türleri. SQL Server türleri ve .NET Framework türleri de temsil ettiği numaralandırmalara <xref:System.Data.DbType> ve <xref:System.Data.SqlDbType> belirtirken kullanabileceğiniz sınıfları <xref:System.Data.SqlClient.SqlParameter> veri türleri.  
  
 Aşağıdaki tabloda oluşturulursa gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü, <xref:System.Data.DbType> ve <xref:System.Data.SqlDbType> numaralandırmalar ve erişimci yöntemleri <xref:System.Data.SqlClient.SqlDataReader>.  
  
|SQL Server veritabanı altyapısı türü|.NET Framework türü|SqlDbType numaralandırması|Erişimci SqlDataReader SqlTypes yazılan|DbType numaralandırması|Erişimci SqlDataReader DbType yazılan|  
|-------------------------------------|-------------------------|---------------------------|-------------------------------------------|------------------------|-----------------------------------------|  
|bigint|Int64|<xref:System.Data.SqlDbType.BigInt>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt64%2A>|<xref:System.Data.DbType.Int64>|<xref:System.Data.SqlClient.SqlDataReader.GetInt64%2A>|  
|ikili|Byte]|<xref:System.Data.SqlDbType.VarBinary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|bit|Boole değeri|<xref:System.Data.SqlDbType.Bit>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBoolean%2A>|<xref:System.Data.DbType.Boolean>|<xref:System.Data.SqlClient.SqlDataReader.GetBoolean%2A>|  
|char|Dize<br /><br /> Char]|<xref:System.Data.SqlDbType.Char>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.AnsiStringFixedLength>,<br /><br /> <xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|Tarih<br /><br /> (SQL Server 2008 ve üzeri)|DateTime|<xref:System.Data.SqlDbType.Date>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType.Date>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime|DateTime|<xref:System.Data.SqlDbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|datetime2<br /><br /> (SQL Server 2008 ve üzeri)|DateTime|<xref:System.Data.SqlDbType.DateTime2>|Yok.|<xref:System.Data.DbType.DateTime2>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|Datetimeoffset<br /><br /> (SQL Server 2008 ve üzeri)|DateTimeOffset|<xref:System.Data.SqlDbType.DateTimeOffset>|yok|<xref:System.Data.DbType.DateTimeOffset>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|  
|decimal|Ondalık|<xref:System.Data.SqlDbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|FILESTREAM özniteliği (varbinary(max))|Byte]|<xref:System.Data.SqlDbType.VarBinary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|float|Çift|<xref:System.Data.SqlDbType.Float>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDouble%2A>|<xref:System.Data.DbType.Double>|<xref:System.Data.SqlClient.SqlDataReader.GetDouble%2A>|  
|görüntü|Byte]|<xref:System.Data.SqlDbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|int|Int32|<xref:System.Data.SqlDbType.Int>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt32%2A>|<xref:System.Data.DbType.Int32>|<xref:System.Data.SqlClient.SqlDataReader.GetInt32%2A>|  
|para|Ondalık|<xref:System.Data.SqlDbType.Money>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nchar|Dize<br /><br /> Char]|<xref:System.Data.SqlDbType.NChar>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.StringFixedLength>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|ntext|Dize<br /><br /> Char]|<xref:System.Data.SqlDbType.NText>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|sayısal|Ondalık|<xref:System.Data.SqlDbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|nvarchar|Dize<br /><br /> Char]|<xref:System.Data.SqlDbType.NVarChar>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|gerçek|Tek|<xref:System.Data.SqlDbType.Real>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlSingle%2A>|<xref:System.Data.DbType.Single>|<xref:System.Data.SqlClient.SqlDataReader.GetFloat%2A>|  
|rowVersion|Byte]|<xref:System.Data.SqlDbType.Timestamp>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|smalldatetime|DateTime|<xref:System.Data.SqlDbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlDateTime%2A>|<xref:System.Data.DbType.DateTime>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|smallint|Int16|<xref:System.Data.SqlDbType.SmallInt>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlInt16%2A>|<xref:System.Data.DbType.Int16>|<xref:System.Data.SqlClient.SqlDataReader.GetInt16%2A>|  
|küçük para|Ondalık|<xref:System.Data.SqlDbType.SmallMoney>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlMoney%2A>|<xref:System.Data.DbType.Decimal>|<xref:System.Data.SqlClient.SqlDataReader.GetDecimal%2A>|  
|sql_variant|Nesne *|<xref:System.Data.SqlDbType.Variant>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A> *|<xref:System.Data.DbType.Object>|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A> *|  
|metin|Dize<br /><br /> Char]|<xref:System.Data.SqlDbType.Text>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|zaman<br /><br /> (SQL Server 2008 ve üzeri)|TimeSpan|<xref:System.Data.SqlDbType.Time>|yok|<xref:System.Data.DbType.Time>|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|  
|zaman damgası|Byte]|<xref:System.Data.SqlDbType.Timestamp>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|Mini tamsayı|Bayt|<xref:System.Data.SqlDbType.TinyInt>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlByte%2A>|<xref:System.Data.DbType.Byte>|<xref:System.Data.SqlClient.SqlDataReader.GetByte%2A>|  
|uniqueidentifier|Guid|<xref:System.Data.SqlDbType.UniqueIdentifier>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlGuid%2A>|<xref:System.Data.DbType.Guid>|<xref:System.Data.SqlClient.SqlDataReader.GetGuid%2A>|  
|varbinary|Byte]|<xref:System.Data.SqlDbType.VarBinary>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlBinary%2A>|<xref:System.Data.DbType.Binary>|<xref:System.Data.SqlClient.SqlDataReader.GetBytes%2A>|  
|varchar|Dize<br /><br /> Char]|<xref:System.Data.SqlDbType.VarChar>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<xref:System.Data.DbType.AnsiString>, <xref:System.Data.DbType.String>|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A><br /><br /> <xref:System.Data.SqlClient.SqlDataReader.GetChars%2A>|  
|xml|Xml|<xref:System.Data.SqlDbType.Xml>|<xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A>|<xref:System.Data.DbType.Xml>|yok|  
  
 \*Temel alınan türü biliyorsanız, belirli bir yazılı erişimci kullanmak `sql_variant`.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-books-online-reference"></a>[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]Books Online başvurusu  
 Hakkında daha fazla bilgi için [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] veri türlerini görmek [veri türleri (veritabanı altyapısı)](http://go.microsoft.com/fwlink/?LinkID=107468).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Veri Türleri ve ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [SQL Server İkili ve Büyük Değerli Veriler](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
