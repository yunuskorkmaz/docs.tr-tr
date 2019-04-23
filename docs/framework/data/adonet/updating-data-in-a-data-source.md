---
title: Bir Veri Kaynağındaki Verileri Güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: a12fa587d5df0ed95dd0f15ccfbe2ef886185b9e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207486"
---
# <a name="updating-data-in-a-data-source"></a>Bir Veri Kaynağındaki Verileri Güncelleştirme
(Örneğin, INSERT, UPDATE veya DELETE) verileri değiştirme SQL deyimleri, satır döndürmeyen. Benzer şekilde, birçok saklı yordamlar, bir eylem gerçekleştirin ancak satır döndürmeyen. Satır döndürmeyen komutları yürütmek için oluşturun bir **komut** uygun SQL komut nesnesiyle ve **bağlantı**, gerekli dahil olmak üzere **parametreleri**. Komutu ile yürütme **ExecuteNonQuery** yöntemi **komut** nesne.  
  
 **ExecuteNonQuery** yöntemi deyimi veya yürütülmesi saklı yordam tarafından etkilenen satır sayısını temsil eden bir tamsayı döndürür. Birden çok deyim yürütülür, döndürülen değer tüm yürütülen deyimleri tarafından etkilenen kayıtların toplamıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir veritabanı kullanarak bir kayıt eklemek için INSERT deyimi yürütür **ExecuteNonQuery**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 Aşağıdaki kod örneği örnek koda oluşturan saklı yordamı yürütür [katalog işlemleri gerçekleştirme](../../../../docs/framework/data/adonet/performing-catalog-operations.md). Hiçbir satır saklı yordam tarafından döndürülen şekilde **ExecuteNonQuery** yöntemi kullanılır, ancak saklı yordam giriş parametresi alır ve bir output parametresi ve dönüş değeri döndürür.  
  
 İçin <xref:System.Data.OleDb.OleDbCommand> nesnesi **ReturnValue** parametre eklenmelidir **parametreleri** koleksiyon ilk.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Verileri Değiştirmek için Komutları Kullanma](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
