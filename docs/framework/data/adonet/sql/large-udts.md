---
title: Büyük Udt'ler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: a57bf400288c11e5ba651515feba42437b93148f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559825"
---
# <a name="large-udts"></a>Büyük Udt'ler
Kullanıcı tanımlı türler(UDT) ortak dil çalışma zamanı (CLR) nesneleri bir SQL Server veritabanında depolayarak sunucunun skalar türü sistemini genişletmek bir geliştirici izin verin. Udt'ler birden çok öğe içerebilir ve davranışlar, tek bir SQL Server sistem veri türünü oluşur geleneksel diğer veri türleri farklı olabilir.  
  
> [!NOTE]
>  .NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üzeri) büyük Udt'ler için Gelişmiş SqlClient desteği avantajlarından yararlanmak için.  
  
 Daha önce Udt'ler için en fazla 8 KB ile sınırlandırılmıştır. Bu kısıtlama, bir biçime sahip Udt'ler için SQL Server 2008'de kaldırılmıştır <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Kullanıcı tanımlı türler için kapsamlı belgeler için SQL Server Books Online'nın sürümü kullandığınız SQL Server sürümü için bkz.  
  
 **SQL Server Çevrimiçi Kitapları**  
  
1.  [Kullanıcı Tanımlı CLR Türleri](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>GetSchema kullanarak UDT şemaları alma  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Yöntemi <xref:System.Data.SqlClient.SqlConnection> döndürür veritabanı şema bilgileri bir <xref:System.Data.DataTable>. Daha fazla bilgi için [SQL Server şema koleksiyonları](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Udt'ler için GetSchemaTable sütun değerleri  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Yöntemi bir <xref:System.Data.SqlClient.SqlDataReader> döndürür bir <xref:System.Data.DataTable> sütun meta verileri, yani açıklar. Aşağıdaki tabloda, SQL Server 2005 ve SQL Server 2008 arasında büyük Udt'ler için sütun meta verileri farklılıkları açıklar.  
  
|SqlDataReader sütun|SQL Server 2005|SQL Server 2008 ve üzeri|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Değişir|Değişir|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT örneği|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT örneği|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Belirtilen adı üç bölüm *Database.SchemaName.TypeName*.|  
|`IsLong`|Değişir|Değişir|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader konuları  
 <xref:System.Data.SqlClient.SqlDataReader> Büyük UDT değerlerini alma desteklemek için SQL Server 2008'de başlayarak genişletilmiştir. Büyük UDT değerleri tarafından işlenen nasıl bir <xref:System.Data.SqlClient.SqlDataReader> kullandığınız de üzerindeki SQL Server'ın sürümüne bağlıdır `Type System Version` bağlantı dizesinde belirtilen. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Aşağıdaki yöntemlerden birini <xref:System.Data.SqlClient.SqlDataReader> döndüreceği bir <xref:System.Data.SqlTypes.SqlBinary> bir UDT yerine zaman `Type System Version` SQL Server 2005'e ayarlanır:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Aşağıdaki yöntemlerden bir dizi döndürür `Byte[]` bir UDT yerine zaman `Type System Version` SQL Server 2005'e ayarlanır:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Hiçbir dönüştürme ADO.NET geçerli sürümü için yapılan unutmayın.  
  
## <a name="specifying-sqlparameters"></a>SqlParameters belirtme  
 Aşağıdaki <xref:System.Data.SqlClient.SqlParameter> genişletilmiş özellikler büyük Udt'ler ile çalışmak için.  
  
|SqlParameter özelliği|Açıklama|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Alır veya ayarlar parametresinin değerini temsil eden bir nesne. Varsayılan olarak null'dur. Özellik güncelleştirilebiliyorsa `SqlBinary`, `Byte[]`, veya yönetilen bir nesne.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Alır veya ayarlar parametresinin değerini temsil eden bir nesne. Varsayılan olarak null'dur. Özellik güncelleştirilebiliyorsa `SqlBinary`, `Byte[]`, veya yönetilen bir nesne.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Alır veya gidermek için herhangi bir parametre boyutunu ayarlar. Varsayılan değer 0’dır. Özelliği, parametre değerinin boyutu temsil eden bir tamsayı olabilir. Büyük Udt'ler için UDT veya bilinmeyen için -1 gerçek boyutu olabilir.|  
  
## <a name="retrieving-data-example"></a>Örnek veri alma  
 Aşağıdaki kod parçası büyük UDT veri veriye nasıl erişeceğinizi gösterir. `connectionString` Değişkeni geçerli bir SQL Server veritabanı bağlantısının varsayar ve `commandString` değişkeni listede ilk sıradaysa birincil anahtar sütunu geçerli bir SELECT deyimi varsayar.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
