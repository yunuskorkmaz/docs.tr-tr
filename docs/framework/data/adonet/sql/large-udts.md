---
title: Büyük atama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 3c74bed67069740354b36891db73ed80b952f0c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="large-udts"></a>Büyük atama
Kullanıcı tanımlı türler (atama) ortak dil çalışma zamanı (CLR) nesneleri bir SQL Server veritabanında depolayarak sunucunun skaler tür sistemini genişletmek Geliştirici izin verin. Atama birden çok öğe içerebilir ve tek bir SQL Server sistem veri türü oluşur geleneksel diğer veri türleri farklı davranışlar olabilir.  
  
> [!NOTE]
>  .NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üstü) büyük atama için Gelişmiş SqlClient destek yararlanmak için.  
  
 Daha önce atama en büyük boyutunu 8 kilobayt için kısıtlanmış. Bu kısıtlama bir biçimine sahip atama için SQL Server 2008'de kaldırılmıştır <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Kullanıcı tanımlı türler için kapsamlı belgeler için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1.  [Kullanıcı Tanımlı CLR Türleri](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>GetSchema kullanarak UDT şemaları alma  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Yöntemi <xref:System.Data.SqlClient.SqlConnection> döndürür veritabanı şema bilgileri bir <xref:System.Data.DataTable>. Daha fazla bilgi için bkz: [SQL Server şeması koleksiyonları](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>GetSchemaTable sütun değerlerini atama  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> döndüren bir <xref:System.Data.DataTable> sütun meta verileri açıklar. Aşağıdaki tabloda, SQL Server 2005 ve SQL Server 2008 arasında büyük atama için sütun meta verileri farklılıkları açıklar.  
  
|SqlDataReader sütun|SQL Server 2005|SQL Server 2008 ve sonraki sürümleri|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Değişir|Değişir|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT örneği|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT örneği|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Üç parçası olarak belirtilen adı *Database.SchemaName.TypeName*.|  
|`IsLong`|Değişir|Değişir|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader konuları  
 <xref:System.Data.SqlClient.SqlDataReader> Büyük UDT değerlerini alma desteklemek için SQL Server 2008'den itibaren genişletilmiştir. Büyük UDT değer tarafından işlenen nasıl bir <xref:System.Data.SqlClient.SqlDataReader> kullanıyorsanız, üzerinde de olarak SQL Server sürümüne bağlıdır `Type System Version` bağlantı dizesinde belirtilen. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Aşağıdaki yöntemlerden birini <xref:System.Data.SqlClient.SqlDataReader> döndürülecek bir <xref:System.Data.SqlTypes.SqlBinary> UDT yerine zaman `Type System Version` SQL Server 2005'e ayarlayın:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Aşağıdaki yöntemlerden bir dizi döndürür `Byte[]` UDT yerine zaman `Type System Version` SQL Server 2005'e ayarlayın:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Hiçbir dönüştürme ADO.NET geçerli sürümü için yapılan unutmayın.  
  
## <a name="specifying-sqlparameters"></a>SqlParameters belirtme  
 Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> genişletilmiş özellikler büyük atama ile çalışmak için.  
  
|SqlParameter özelliği|Açıklama|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Alır veya ayarlar parametresinin değerini temsil eden nesne. Varsayılan olarak null'dur. Özellik güncelleştirilebiliyorsa `SqlBinary`, `Byte[]`, veya yönetilen bir nesne.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Alır veya ayarlar parametresinin değerini temsil eden nesne. Varsayılan olarak null'dur. Özellik güncelleştirilebiliyorsa `SqlBinary`, `Byte[]`, veya yönetilen bir nesne.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Alır veya gidermek için parametre değeri ayarlar. Varsayılan değer 0’dır. Parametre değeri boyutunu temsil eden bir tamsayı özelliği olabilir. Büyük atama için UDT veya -1 bilinmeyen için gerçek boyutu olabilir.|  
  
## <a name="retrieving-data-example"></a>Veri örneği alınıyor  
 Aşağıdaki kod parçası, büyük UDT veri almayı gösterir. `connectionString` Değişkeni geçerli bir SQL Server veritabanı bağlantısının varsayar ve `commandString` değişkeni, ilk listelenen birincil anahtar sütunu geçerli bir SELECT deyimi varsayar.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Parametreleri ve Parametre Veri Türlerini Yapılandırma](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Veritabanı Şema Bilgilerini Alma](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [SQL Server Veri Türü Eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [SQL Server İkili ve Büyük Değerli Veriler](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
