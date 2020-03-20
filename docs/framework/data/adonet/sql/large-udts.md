---
title: Büyük UDT’ler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: f55f6eccf3566a2391204e1ca4349ae5dff01954
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148562"
---
# <a name="large-udts"></a>Büyük UDT’ler
Kullanıcı tanımlı türleri (UDT'ler), bir geliştiricinin ortak dil çalışma zamanı (CLR) nesnelerini bir SQL Server veritabanında depolayarak sunucunun skaler tür sistemini genişletmesine olanak sağlar. UDT'ler birden çok öğe içerebilir ve tek bir SQL Server sistem veri türünden oluşan geleneksel diğer ad veri türlerinin aksine davranışlar içerebilir.  
  
> [!NOTE]
> Büyük UDT'ler için geliştirilmiş SqlClient desteğinden yararlanmak için .NET Framework 3.5 SP1 (veya sonraki) yüklemeniz gerekir.  
  
 Daha önce, UDTs 8 kilobayt maksimum boyutu ile sınırlı idi. SQL Server 2008'de, bu kısıtlama , <xref:Microsoft.SqlServer.Server.Format.UserDefined>biçimi ne olan UDT'ler için kaldırıldı  
  
 Kullanıcı tanımlı türler için tam belgeler için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.  
  
 **SQL Server belgeleri**  
  
1. [Kullanıcı Tanımlı CLR Türleri](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>GetSchema kullanarak UDT Şema alma  
 Veritabanı şema bilgilerini bir <xref:System.Data.DataTable>. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:System.Data.SqlClient.SqlConnection> Daha fazla bilgi için [SQL Server Schema Collections'a](../sql-server-schema-collections.md)bakın.  
  
### <a name="getschematable-column-values-for-udts"></a>UD'ler için GetSchemaTable Sütun Değerleri  
 Sütun <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> meta <xref:System.Data.SqlClient.SqlDataReader> verilerini <xref:System.Data.DataTable> açıklayan bir yöntem. Aşağıdaki tabloda, SQL Server 2005 ile SQL Server 2008 arasındaki büyük UDT'ler için sütun meta verilerindeki farklar açıklanmaktadır.  
  
|SqlDataReader sütunu|SQL Server 2005|SQL Server 2008 ve sonrası|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Değişir|Değişir|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT örneği|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT örneği|  
|`ProviderType`|21`SqlDbType.VarBinary`( ) ( )|29`SqlDbType.Udt`( ) ( )|  
|`NonVersionedProviderType`|29`SqlDbType.Udt`( ) ( )|29`SqlDbType.Udt`( ) ( )|  
|`DataTypeName`|`SqlDbType.VarBinary`|*Database.SchemaName.TypeName*olarak belirtilen üç bölümadı.|  
|`IsLong`|Değişir|Değişir|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader Hususlar  
 Büyük <xref:System.Data.SqlClient.SqlDataReader> UDT değerlerinin alınmasını desteklemek için SQL Server 2008'den itibaren genişletildi. UdT değerlerinin ne kadar <xref:System.Data.SqlClient.SqlDataReader> büyük bir değer tarafından işlendiği, kullandığınız SQL Server `Type System Version` sürümüne ve bağlantı dizesinde belirtilene bağlıdır. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 SQL Server <xref:System.Data.SqlClient.SqlDataReader> 2005 olarak <xref:System.Data.SqlTypes.SqlBinary> ayarlandığında, `Type System Version` aşağıdaki yöntemler udt yerine bir döndürme yöntemi:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Aşağıdaki yöntemler, SQL Server `Byte[]` 2005 olarak `Type System Version` ayarlandığında UDT yerine bir dizi döndürecektir:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 ADO.NET geçerli sürümü için dönüşüm yapılmadığını unutmayın.  
  
## <a name="specifying-sqlparameters"></a>SqlParametrelerinin Belirtilmesi  
 Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> özellikler büyük UDT'lerle çalışmak üzere genişletilmiştir.  
  
|SqlParameter Özelliği|Açıklama|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Parametrenin değerini temsil eden bir nesne alır veya ayarlar. Varsayılan olarak null'dur. Özellik , `Byte[]` `SqlBinary`veya yönetilen bir nesne olabilir.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Parametrenin değerini temsil eden bir nesne alır veya ayarlar. Varsayılan olarak null'dur. Özellik , `Byte[]` `SqlBinary`veya yönetilen bir nesne olabilir.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Çözülecek parametre değerinin boyutunu alır veya ayarlar. Varsayılan değer 0’dır. Özellik, parametre değerinin boyutunu temsil eden bir karşıcı olabilir. Büyük UDT'ler için UDT'nin gerçek boyutu veya bilinmeyen için -1 olabilir.|  
  
## <a name="retrieving-data-example"></a>Veri Alma Örneği  
 Aşağıdaki kod parçası, büyük UDT verilerinin nasıl alındığını gösterir. Değişken, `connectionString` bir SQL Server veritabanına geçerli `commandString` bir bağlantı varsayar ve değişken ilk listelenen birincil anahtar sütunu ile geçerli bir SELECT deyimi varsayar.  
  
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
