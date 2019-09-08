---
title: Verileri Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.openlocfilehash: 322325b765f62d04e5713557f2ef9c97e1746ae0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792051"
---
# <a name="manipulating-data"></a><span data-ttu-id="72f67-102">Verileri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="72f67-102">Manipulating Data</span></span>
<span data-ttu-id="72f67-103">Birden çok etkin sonuç kümesi (MARS) gönderilmeden önce, geliştiricilerin belirli senaryoları çözümlemek için birden çok bağlantı veya sunucu tarafı imleçler kullanması gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="72f67-103">Before the introduction of Multiple Active Result Sets (MARS), developers had to use either multiple connections or server-side cursors to solve certain scenarios.</span></span> <span data-ttu-id="72f67-104">Ayrıca, işlem durumunda birden çok bağlantı kullanıldığında, ilişkili bağlantılar ( **sp_getbindtoken** ve **sp_bindsession**ile) gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="72f67-104">In addition, when multiple connections were used in a transactional situation, bound connections (with **sp_getbindtoken** and **sp_bindsession**) were required.</span></span> <span data-ttu-id="72f67-105">Aşağıdaki senaryolarda, birden çok bağlantı yerine MARS özellikli bir bağlantının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="72f67-105">The following scenarios show how to use a MARS-enabled connection instead of multiple connections.</span></span>  
  
## <a name="using-multiple-commands-with-mars"></a><span data-ttu-id="72f67-106">MARS ile birden çok komut kullanma</span><span class="sxs-lookup"><span data-stu-id="72f67-106">Using Multiple Commands with MARS</span></span>  
 <span data-ttu-id="72f67-107">Aşağıdaki konsol uygulaması, iki nesne <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlCommand> ile iki nesne ve Mars özellikli tek <xref:System.Data.SqlClient.SqlConnection> bir nesne kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="72f67-107">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with two <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span>  
  
### <a name="example"></a><span data-ttu-id="72f67-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="72f67-108">Example</span></span>  
 <span data-ttu-id="72f67-109">Örnek, **AdventureWorks** veritabanına tek bir bağlantı açar.</span><span class="sxs-lookup"><span data-stu-id="72f67-109">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="72f67-110"><xref:System.Data.SqlClient.SqlCommand> Bir<xref:System.Data.SqlClient.SqlDataReader> nesnesi kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="72f67-110">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="72f67-111">Okuyucu kullanıldığı için, ikinci bir okuyucu için <xref:System.Data.SqlClient.SqlDataReader> WHERE yan tümcesine giriş olarak ilk <xref:System.Data.SqlClient.SqlDataReader> girdi kullanılarak ikinci bir saniye açılır.</span><span class="sxs-lookup"><span data-stu-id="72f67-111">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72f67-112">Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="72f67-112">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="72f67-113">Örnek kodda sağlanan bağlantı dizesi, veritabanının yerel bilgisayarda yüklü ve kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="72f67-113">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="72f67-114">Bağlantı dizesini ortamınız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72f67-114">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Module Module1  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim vendorID As Integer  
  
    Dim vendorCmd As SqlCommand  
    Dim productCmd As SqlCommand  
    Dim productReader As SqlDataReader  
  
    Dim vendorSQL As String = & _   
      "SELECT VendorId, Name FROM Purchasing.Vendor"  
    Dim productSQL As String = _  
        "SELECT Production.Product.Name FROM Production.Product " & _  
        "INNER JOIN Purchasing.ProductVendor " & _  
        "ON Production.Product.ProductID = " & _  
        "Purchasing.ProductVendor.ProductID " & _  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId"  
  
    Using awConnection As New SqlConnection(connectionString)  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      productCmd = New SqlCommand(productSQL, awConnection)  
      productCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      awConnection.Open()  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorId"))  
  
          productCmd.Parameters("@VendorId").Value = vendorID  
  
          ' The following line of code requires  
          ' a MARS-enabled connection.  
          productReader = productCmd.ExecuteReader()  
          Using productReader  
            While productReader.Read()  
              Console.WriteLine("  " & CStr(productReader("Name")))  
            End While  
          End Using  
        End While  
      End Using  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks; MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrieve it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a><span data-ttu-id="72f67-115">MARS ile verileri okuma ve güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="72f67-115">Reading and Updating Data with MARS</span></span>  
 <span data-ttu-id="72f67-116">MARS, bir bağlantının hem okuma işlemleri hem de veri işleme dili (DML) işlemleri için birden fazla bekleyen işlemle kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="72f67-116">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="72f67-117">Bu özellik, bir uygulamanın bağlantı meşgul hatalarıyla ilgilenmesi gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="72f67-117">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="72f67-118">Ayrıca, MARS, genellikle daha fazla kaynak kullanan sunucu tarafı imleçlerinin kullanıcısını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="72f67-118">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="72f67-119">Son olarak, birden çok işlem tek bir bağlantı üzerinde çalışabildiklerinden, **sp_getbindtoken** ve **sp_bindsession** sistem saklı yordamlarını kullanma gereksinimini ortadan kaldıran aynı işlem bağlamını paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="72f67-119">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
### <a name="example"></a><span data-ttu-id="72f67-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="72f67-120">Example</span></span>  
 <span data-ttu-id="72f67-121">Aşağıdaki konsol uygulaması, üç <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlCommand> nesne ile iki nesnenin nasıl kullanılacağını ve Mars ile tek <xref:System.Data.SqlClient.SqlConnection> bir nesneyle nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="72f67-121">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="72f67-122">İlk komut nesnesi, kredi derecelendirmesi 5 olan satıcıların bir listesini alır.</span><span class="sxs-lookup"><span data-stu-id="72f67-122">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="72f67-123">İkinci komut nesnesi, belirli bir satıcıya ait tüm ürünlerle ikincisini <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataReader> yüklemek için bir kaynağından belirtilen satıcı kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="72f67-123">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="72f67-124">Her ürün kaydı ikinciden <xref:System.Data.SqlClient.SqlDataReader>ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="72f67-124">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="72f67-125">Yeni **Onordermik** 'in ne olması gerektiğini belirlemek için bir hesaplama gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="72f67-125">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="72f67-126">Ardından, üçüncü komut nesnesi, **ProductVendor** tablosunu yeni değerle güncelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72f67-126">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="72f67-127">Bu işlemin tamamı, sonunda geri alınan tek bir işlem içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="72f67-127">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72f67-128">Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="72f67-128">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="72f67-129">Örnek kodda sağlanan bağlantı dizesi, veritabanının yerel bilgisayarda yüklü ve kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="72f67-129">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="72f67-130">Bağlantı dizesini ortamınız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="72f67-130">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim updateTx As SqlTransaction  
    Dim vendorCmd As SqlCommand  
    Dim prodVendCmd As SqlCommand  
    Dim updateCmd As SqlCommand  
  
    Dim prodVendReader As SqlDataReader  
  
    Dim vendorID As Integer  
    Dim productID As Integer  
    Dim minOrderQty As Integer  
    Dim maxOrderQty As Integer  
    Dim onOrderQty As Integer  
    Dim recordsUpdated As Integer  
    Dim totalRecordsUpdated As Integer  
  
    Dim vendorSQL As String = _  
        "SELECT VendorID, Name FROM Purchasing.Vendor " & _  
        "WHERE CreditRating = 5"  
    Dim prodVendSQL As String = _  
        "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " & _  
        "FROM Purchasing.ProductVendor " & _  
        "WHERE VendorID = @VendorID"  
    Dim updateSQL As String = _  
        "UPDATE Purchasing.ProductVendor " & _   
        "SET OnOrderQty = @OrderQty " & _  
        "WHERE ProductID = @ProductID AND VendorID = @VendorID"  
  
    Using awConnection As New SqlConnection(connectionString)  
      awConnection.Open()  
      updateTx = awConnection.BeginTransaction()  
  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      vendorCmd.Transaction = updateTx  
  
      prodVendCmd = New SqlCommand(prodVendSQL, awConnection)  
      prodVendCmd.Transaction = updateTx  
      prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      updateCmd = New SqlCommand(updateSQL, awConnection)  
      updateCmd.Transaction = updateTx  
      updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int)  
      updateCmd.Parameters.Add("@ProductID", SqlDbType.Int)  
      updateCmd.Parameters.Add("@VendorID", SqlDbType.Int)  
  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorID"))  
          prodVendCmd.Parameters("@VendorID").Value = vendorID  
          prodVendReader = prodVendCmd.ExecuteReader()  
  
          Using prodVendReader  
            While (prodVendReader.Read)  
              productID = CInt(prodVendReader("ProductID"))  
  
              If IsDBNull(prodVendReader("OnOrderQty")) Then  
                minOrderQty = CInt(prodVendReader("MinOrderQty"))  
                onOrderQty = minOrderQty  
              Else  
                maxOrderQty = CInt(prodVendReader("MaxOrderQty"))  
                onOrderQty = CInt(maxOrderQty / 2)  
              End If  
  
              updateCmd.Parameters("@OrderQty").Value = onOrderQty  
              updateCmd.Parameters("@ProductID").Value = productID  
              updateCmd.Parameters("@VendorID").Value = vendorID  
  
              recordsUpdated = updateCmd.ExecuteNonQuery()  
              totalRecordsUpdated += recordsUpdated  
            End While  
          End Using  
        End While  
      End Using  
  
      Console.WriteLine("Total Records Updated: " & _   
        CStr(totalRecordsUpdated))  
      updateTx.Rollback()  
      Console.WriteLine("Transaction Rolled Back")  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrieve it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="72f67-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72f67-131">See also</span></span>

- [<span data-ttu-id="72f67-132">Birden Çok Etkin Sonuç Kümesi (MARS)</span><span class="sxs-lookup"><span data-stu-id="72f67-132">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="72f67-133">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="72f67-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
