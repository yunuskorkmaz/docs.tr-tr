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
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="c8a76-102">Bir Veri Kaynağındaki Verileri Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="c8a76-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="c8a76-103">Verileri değiştiren SQL deyimleri (INSERT, UPDATE veya DELETE gibi) satır döndürmez.</span><span class="sxs-lookup"><span data-stu-id="c8a76-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="c8a76-104">Benzer şekilde, depolanan birçok yordam bir eylem gerçekleştirir, ancak satırları döndürmez.</span><span class="sxs-lookup"><span data-stu-id="c8a76-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="c8a76-105">Satırları döndürmeyan komutları yürütmek için, gerekli **parametreleri**içeren uygun SQL komutu ve **bağlantıile**bir **Komut** nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8a76-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="c8a76-106">**Komut** nesnesinin **ExecuteNonQuery** yöntemi ile komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c8a76-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="c8a76-107">**ExecuteNonQuery** yöntemi, yürütülen deyim veya depolanan yordamdan etkilenen satır sayısını temsil eden bir karşıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8a76-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="c8a76-108">Birden çok deyim yürütülürse, döndürülen değer, yürütülen tüm deyimlerden etkilenen kayıtların toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="c8a76-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8a76-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8a76-109">Example</span></span>  
 <span data-ttu-id="c8a76-110">Aşağıdaki kod **örneği, ExecuteNonQuery**kullanarak bir veritabanına bir kayıt eklemek için bir INSERT deyimi yürütür.</span><span class="sxs-lookup"><span data-stu-id="c8a76-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="c8a76-111">Aşağıdaki kod örneği, [Performans Kataloğu İşlemleri'nde](performing-catalog-operations.md)örnek kodu tarafından oluşturulan depolanan yordamı yürütür.</span><span class="sxs-lookup"><span data-stu-id="c8a76-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](performing-catalog-operations.md).</span></span> <span data-ttu-id="c8a76-112">Depolanan yordam tarafından satır döndürülür, bu nedenle **ExecuteNonQuery** yöntemi kullanılır, ancak depolanan yordam bir giriş parametresi alır ve bir çıktı parametresi ve bir dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8a76-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="c8a76-113">Nesne <xref:System.Data.OleDb.OleDbCommand> **için, Önce** **Parametreler** koleksiyonuna ReturnValue parametresi eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c8a76-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8a76-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8a76-114">See also</span></span>

- [<span data-ttu-id="c8a76-115">Verileri Değiştirmek için Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c8a76-115">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)
- [<span data-ttu-id="c8a76-116">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="c8a76-116">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="c8a76-117">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8a76-117">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="c8a76-118">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c8a76-118">ADO.NET Overview</span></span>](ado-net-overview.md)
