---
title: Bir Veri Kaynağındaki Verileri Güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780619"
---
# <a name="updating-data-in-a-data-source"></a>Bir Veri Kaynağındaki Verileri Güncelleştirme
Verileri değiştiren SQL deyimleri (INSERT, UPDATE veya DELETE gibi) satır döndürmez. Benzer şekilde, birçok saklı yordam bir eylem yapar ancak satır döndürmez. Satırları döndürmeyen komutları yürütmek için, gerekli **Parametreler**dahil olmak üzere uygun SQL komutuyla ve bir **bağlantıyla**birlikte bir **komut** nesnesi oluşturun. **Komut nesnesinin** **ExecuteNonQuery** yöntemiyle komutunu yürütün.  
  
 **ExecuteNonQuery** yöntemi, yürütülen deyimin veya saklı yordamın etkilediği satır sayısını temsil eden bir tamsayı döndürür. Birden çok deyim yürütülürse, döndürülen değer yürütülen tüm deyimlerden etkilenen kayıtların toplamıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, **ExecuteNonQuery**kullanarak bir veritabanına kayıt eklemek IÇIN bir INSERT ifadesini yürütür.  
  
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
  
 Aşağıdaki kod örneği, [Katalog Işlemlerini gerçekleştirirken](performing-catalog-operations.md)örnek kod tarafından oluşturulan saklı yordamı yürütür. Saklı yordam tarafından hiçbir satır döndürüldüğünden, **ExecuteNonQuery** yöntemi kullanılır, ancak saklı yordam bir giriş parametresi alır ve bir çıkış parametresi ve bir dönüş değeri döndürür.  
  
 Nesnesi için, önce **parametre koleksiyonuna** ReturnValue parametresi eklenmelidir. <xref:System.Data.OleDb.OleDbCommand>  
  
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
