---
title: Bir veri kaynağındaki verileri güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 11c3faa85d6d0b77c4e606815aa8252188b6f67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357799"
---
# <a name="updating-data-in-a-data-source"></a>Bir veri kaynağındaki verileri güncelleştirme
Verileri (örneğin, INSERT, UPDATE veya DELETE) değiştirme SQL deyimlerini satırları döndürmeyin. Benzer şekilde, birçok saklı yordamlar bir eylem gerçekleştirmek ancak satırları döndürmüyor. Satır döndürmeyen komutları yürütmek için Oluştur bir **komutu** uygun SQL komutu nesnesiyle ve **bağlantı**, gerekli dahil olmak üzere **parametreleri**. Komutu yürütmek **ExecuteNonQuery** yöntemi **komutu** nesnesi.  
  
 **ExecuteNonQuery** yöntemi deyimi veya yürütüldü saklı yordam tarafından etkilenen satırların sayısını temsil eden bir tamsayı döndürür. Birden çok deyime yürütülürse, döndürülen değer tüm yürütülen deyimleri tarafından etkilenen kayıtların toplamıdır.  
  
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
  
 Aşağıdaki kod örneği örnek kodda tarafından oluşturulan saklı yordam yürütür [katalog işlemleri gerçekleştirme](../../../../docs/framework/data/adonet/performing-catalog-operations.md). Hiçbir satır saklı yordamı tarafından döndürülen böylece **ExecuteNonQuery** yöntemi kullanılır, ancak saklı yordamı bir giriş parametresi alır ve bir output parametresi ve dönüş değeri döndürür.  
  
 İçin <xref:System.Data.OleDb.OleDbCommand> nesnesi **ReturnValue** parametre eklenmelidir **parametreleri** koleksiyonu ilk.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri Değiştirmek için Komutları Kullanma](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
