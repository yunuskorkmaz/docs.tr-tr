---
title: Bir Veri Kaynağındaki Verileri Güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 6b0234337c85ace0797d75b72560ccb55635daae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177273"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="0d66e-102">Bir Veri Kaynağındaki Verileri Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="0d66e-102">Updating Data in a Data Source</span></span>

<span data-ttu-id="0d66e-103">Verileri değiştiren SQL deyimleri (INSERT, UPDATE veya DELETE gibi) satır döndürmez.</span><span class="sxs-lookup"><span data-stu-id="0d66e-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="0d66e-104">Benzer şekilde, birçok saklı yordam bir eylem yapar ancak satır döndürmez.</span><span class="sxs-lookup"><span data-stu-id="0d66e-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="0d66e-105">Satırları döndürmeyen komutları yürütmek için, gerekli **Parametreler**dahil olmak üzere uygun SQL komutuyla ve bir **bağlantıyla**birlikte bir **komut** nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0d66e-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="0d66e-106">**Komut nesnesinin** **ExecuteNonQuery** yöntemiyle komutunu yürütün.</span><span class="sxs-lookup"><span data-stu-id="0d66e-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="0d66e-107">**ExecuteNonQuery** yöntemi, yürütülen deyimin veya saklı yordamın etkilediği satır sayısını temsil eden bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d66e-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="0d66e-108">Birden çok deyim yürütülürse, döndürülen değer yürütülen tüm deyimlerden etkilenen kayıtların toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="0d66e-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d66e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d66e-109">Example</span></span>  

 <span data-ttu-id="0d66e-110">Aşağıdaki kod örneği, **ExecuteNonQuery**kullanarak bir veritabanına kayıt eklemek IÇIN bir INSERT ifadesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="0d66e-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="0d66e-111">Aşağıdaki kod örneği, [Katalog Işlemlerini gerçekleştirirken](performing-catalog-operations.md)örnek kod tarafından oluşturulan saklı yordamı yürütür.</span><span class="sxs-lookup"><span data-stu-id="0d66e-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="0d66e-112">Saklı yordam tarafından hiçbir satır döndürüldüğünden, **ExecuteNonQuery** yöntemi kullanılır, ancak saklı yordam bir giriş parametresi alır ve bir çıkış parametresi ve bir dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d66e-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="0d66e-113">Nesnesi için <xref:System.Data.OleDb.OleDbCommand> , önce **parametre** koleksiyonuna **returnValue** parametresi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0d66e-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d66e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d66e-114">See also</span></span>

- [<span data-ttu-id="0d66e-115">Verileri Değiştirmek için Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0d66e-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="0d66e-116">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="0d66e-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="0d66e-117">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d66e-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="0d66e-118">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0d66e-118">ADO.NET Overview</span></span>](ado-net-overview.md)
