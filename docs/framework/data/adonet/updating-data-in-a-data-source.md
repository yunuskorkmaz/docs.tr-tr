---
title: Bir Veri Kaynağındaki Verileri Güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: a12fa587d5df0ed95dd0f15ccfbe2ef886185b9e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207486"
---
# <a name="updating-data-in-a-data-source"></a><span data-ttu-id="6da82-102">Bir Veri Kaynağındaki Verileri Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="6da82-102">Updating Data in a Data Source</span></span>
<span data-ttu-id="6da82-103">(Örneğin, INSERT, UPDATE veya DELETE) verileri değiştirme SQL deyimleri, satır döndürmeyen.</span><span class="sxs-lookup"><span data-stu-id="6da82-103">SQL statements that modify data (such as INSERT, UPDATE, or DELETE) do not return rows.</span></span> <span data-ttu-id="6da82-104">Benzer şekilde, birçok saklı yordamlar, bir eylem gerçekleştirin ancak satır döndürmeyen.</span><span class="sxs-lookup"><span data-stu-id="6da82-104">Similarly, many stored procedures perform an action but do not return rows.</span></span> <span data-ttu-id="6da82-105">Satır döndürmeyen komutları yürütmek için oluşturun bir **komut** uygun SQL komut nesnesiyle ve **bağlantı**, gerekli dahil olmak üzere **parametreleri**.</span><span class="sxs-lookup"><span data-stu-id="6da82-105">To execute commands that do not return rows, create a **Command** object with the appropriate SQL command and a **Connection**, including any required **Parameters**.</span></span> <span data-ttu-id="6da82-106">Komutu ile yürütme **ExecuteNonQuery** yöntemi **komut** nesne.</span><span class="sxs-lookup"><span data-stu-id="6da82-106">Execute the command with the **ExecuteNonQuery** method of the **Command** object.</span></span>  
  
 <span data-ttu-id="6da82-107">**ExecuteNonQuery** yöntemi deyimi veya yürütülmesi saklı yordam tarafından etkilenen satır sayısını temsil eden bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="6da82-107">The **ExecuteNonQuery** method returns an integer that represents the number of rows affected by the statement or stored procedure that was executed.</span></span> <span data-ttu-id="6da82-108">Birden çok deyim yürütülür, döndürülen değer tüm yürütülen deyimleri tarafından etkilenen kayıtların toplamıdır.</span><span class="sxs-lookup"><span data-stu-id="6da82-108">If multiple statements are executed, the value returned is the sum of the records affected by all of the statements executed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6da82-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6da82-109">Example</span></span>  
 <span data-ttu-id="6da82-110">Aşağıdaki kod örneğinde bir veritabanı kullanarak bir kayıt eklemek için INSERT deyimi yürütür **ExecuteNonQuery**.</span><span class="sxs-lookup"><span data-stu-id="6da82-110">The following code example executes an INSERT statement to insert a record into a database using **ExecuteNonQuery**.</span></span>  
  
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
  
 <span data-ttu-id="6da82-111">Aşağıdaki kod örneği örnek koda oluşturan saklı yordamı yürütür [katalog işlemleri gerçekleştirme](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6da82-111">The following code example executes the stored procedure created by the sample code in [Performing Catalog Operations](../../../../docs/framework/data/adonet/performing-catalog-operations.md).</span></span> <span data-ttu-id="6da82-112">Hiçbir satır saklı yordam tarafından döndürülen şekilde **ExecuteNonQuery** yöntemi kullanılır, ancak saklı yordam giriş parametresi alır ve bir output parametresi ve dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6da82-112">No rows are returned by the stored procedure, so the **ExecuteNonQuery** method is used, but the stored procedure does receive an input parameter and returns an output parameter and a return value.</span></span>  
  
 <span data-ttu-id="6da82-113">İçin <xref:System.Data.OleDb.OleDbCommand> nesnesi **ReturnValue** parametre eklenmelidir **parametreleri** koleksiyon ilk.</span><span class="sxs-lookup"><span data-stu-id="6da82-113">For the <xref:System.Data.OleDb.OleDbCommand> object, the **ReturnValue** parameter must be added to the **Parameters** collection first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6da82-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6da82-114">See also</span></span>

- [<span data-ttu-id="6da82-115">Verileri Değiştirmek için Komutları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6da82-115">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)
- [<span data-ttu-id="6da82-116">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="6da82-116">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="6da82-117">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="6da82-117">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="6da82-118">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="6da82-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
