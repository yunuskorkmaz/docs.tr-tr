---
title: Bir Veri Kaynağındaki Verileri Güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 18bb03e17b19243ee1bc6e3f7ebd70afb4d4c60b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174452"
---
# <a name="updating-data-in-a-data-source"></a>Bir Veri Kaynağındaki Verileri Güncelleştirme
Verileri değiştiren SQL deyimleri (INSERT, UPDATE veya DELETE gibi) satır döndürmez. Benzer şekilde, depolanan birçok yordam bir eylem gerçekleştirir, ancak satırları döndürmez. Satırları döndürmeyan komutları yürütmek için, gerekli **parametreleri**içeren uygun SQL komutu ve **bağlantıile**bir **Komut** nesnesi oluşturun. **Komut** nesnesinin **ExecuteNonQuery** yöntemi ile komutu çalıştırın.  
  
 **ExecuteNonQuery** yöntemi, yürütülen deyim veya depolanan yordamdan etkilenen satır sayısını temsil eden bir karşıcı döndürür. Birden çok deyim yürütülürse, döndürülen değer, yürütülen tüm deyimlerden etkilenen kayıtların toplamıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod **örneği, ExecuteNonQuery**kullanarak bir veritabanına bir kayıt eklemek için bir INSERT deyimi yürütür.  
  
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
  
 Aşağıdaki kod örneği, [Performans Kataloğu İşlemleri'nde](performing-catalog-operations.md)örnek kodu tarafından oluşturulan depolanan yordamı yürütür. Depolanan yordam tarafından satır döndürülür, bu nedenle **ExecuteNonQuery** yöntemi kullanılır, ancak depolanan yordam bir giriş parametresi alır ve bir çıktı parametresi ve bir dönüş değeri döndürür.  
  
 Nesne <xref:System.Data.OleDb.OleDbCommand> **için, Önce** **Parametreler** koleksiyonuna ReturnValue parametresi eklenmelidir.  
  
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

- [Verileri Değiştirmek için Komutları Kullanma](using-commands-to-modify-data.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
