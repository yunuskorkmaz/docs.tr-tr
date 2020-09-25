---
title: Büyük UDT’ler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 032093244f51893cd3b0cf50ad81c79413aaa32e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194550"
---
# <a name="large-udts"></a>Büyük UDT’ler

Kullanıcı tanımlı türler (UDTs), bir geliştiricinin ortak dil çalışma zamanı (CLR) nesnelerini bir SQL Server veritabanında depolayarak sunucunun skalar tür sistemini genişletmesine izin verir. UDTs birden çok öğe içerebilir ve tek bir SQL Server sistem veri türünden oluşan geleneksel diğer ad veri türlerinden farklı olarak davranışları olabilir.  
  
> [!NOTE]
> Büyük UDTs için gelişmiş SqlClient desteğinin avantajlarından yararlanabilmek için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.  
  
 Daha önce, UDTs, 8 kilobayt olan en büyük boyutla sınırlandırılmıştır. SQL Server 2008 ' de, bu kısıtlama biçiminde olan UDTs 'ler için kaldırılmıştır <xref:Microsoft.SqlServer.Server.Format.UserDefined> .  
  
 Kullanıcı tanımlı türlerin tam belgeleri için, kullandığınız SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **SQL Server belgeleri**  
  
1. [Kullanıcı Tanımlı CLR Türleri](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>GetSchema kullanarak UDT şemaları alma  

 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>Yöntemi, <xref:System.Data.SqlClient.SqlConnection> içindeki veritabanı şeması bilgilerini döndürür <xref:System.Data.DataTable> . Daha fazla bilgi için bkz. [SQL Server şema koleksiyonları](../sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>UDTs için GetSchemaTable sütun değerleri  

 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>Bir öğesinin yöntemi, <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.DataTable> sütun meta verilerini açıklayan bir döndürür. Aşağıdaki tabloda, SQL Server 2005 ve SQL Server 2008 arasındaki büyük UDTs için sütun meta verilerindeki farklar açıklanmaktadır.  
  
|SqlDataReader sütunu|SQL Server 2005|SQL Server 2008 ve üzeri|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Değişir|Değişir|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT örneği|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT örneği|  
|`ProviderType`|21 ( `SqlDbType.VarBinary` )|29 ( `SqlDbType.Udt` )|  
|`NonVersionedProviderType`|29 ( `SqlDbType.Udt` )|29 ( `SqlDbType.Udt` )|  
|`DataTypeName`|`SqlDbType.VarBinary`|*Database. SchemaName. TypeName*olarak belirtilen üç bölüm adı.|  
|`IsLong`|Değişir|Değişir|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader konuları  

 , <xref:System.Data.SqlClient.SqlDataReader> Büyük udt değerlerini almayı desteklemek için SQL Server 2008 ' den başlayarak genişletildi. Büyük UDT değerlerinin bir tarafından nasıl işlendiği <xref:System.Data.SqlClient.SqlDataReader> , kullandığınız SQL Server sürümüne ve ayrıca `Type System Version` bağlantı dizesinde belirtilen sürüme bağlıdır. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Aşağıdaki yöntemleri <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlTypes.SqlBinary> , `Type System Version` SQL Server 2005 olarak ayarlandığında UDT yerine bir udt döndürür:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Aşağıdaki yöntemler `Byte[]` , `Type System Version` SQL Server 2005 olarak AYARLANDıĞıNDA bir udt yerine bir dizisi döndürür:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Geçerli ADO.NET sürümü için hiçbir dönüştürme yapılmadığını unutmayın.  
  
## <a name="specifying-sqlparameters"></a>SqlParameters belirtme  

 Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> Özellikler, büyük UDTs ile çalışacak şekilde genişletildi.  
  
|SqlParameter özelliği|Açıklama|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Parametresinin değerini temsil eden bir nesne alır veya ayarlar. Varsayılan olarak null'dur. Özelliği `SqlBinary` , `Byte[]` veya yönetilen bir nesne olabilir.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Parametresinin değerini temsil eden bir nesne alır veya ayarlar. Varsayılan olarak null'dur. Özelliği `SqlBinary` , `Byte[]` veya yönetilen bir nesne olabilir.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Çözülecek parametre değerinin boyutunu alır veya ayarlar. Varsayılan değer 0’dır. Özelliği parametre değerinin boyutunu temsil eden bir tamsayı olabilir. Büyük UDTs 'ler için, UDT 'nin gerçek boyutu veya bilinmeyen için-1 olabilir.|  
  
## <a name="retrieving-data-example"></a>Veri alma örneği  

 Aşağıdaki kod parçası, büyük UDT verilerinin nasıl alınacağını gösterir. `connectionString`Değişken, SQL Server veritabanına geçerli bir bağlantı olduğunu varsayar ve `commandString` değişken önce listelenen birincil anahtar sütunu ile GEÇERLI bir SELECT ifadesini varsayar.  
  
```csharp  
using (SqlConnection connection = new SqlConnection(
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../configuring-parameters-and-parameter-data-types.md)
- [Veritabanı Şema Bilgilerini Alma](../retrieving-database-schema-information.md)
- [SQL Server Veri Türü Eşlemeleri](../sql-server-data-type-mappings.md)
- [SQL Server İkili ve Büyük Değerli Veriler](sql-server-binary-and-large-value-data.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
