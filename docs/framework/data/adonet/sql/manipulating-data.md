---
title: Verileri Düzenleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.openlocfilehash: 70ee6041b14feb298d93ab452e16ee23607b3fcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174296"
---
# <a name="manipulating-data"></a><span data-ttu-id="b871b-102">Verileri Düzenleme</span><span class="sxs-lookup"><span data-stu-id="b871b-102">Manipulating Data</span></span>
<span data-ttu-id="b871b-103">Birden Çok Etkin Sonuç Kümesi (MARS) kullanılmaya başlanmadan önce, geliştiriciler belirli senaryoları çözmek için birden çok bağlantı veya sunucu tarafı imleci kullanmak zorunda kaldı.</span><span class="sxs-lookup"><span data-stu-id="b871b-103">Before the introduction of Multiple Active Result Sets (MARS), developers had to use either multiple connections or server-side cursors to solve certain scenarios.</span></span> <span data-ttu-id="b871b-104">Buna ek olarak, bir işlem durumunda birden çok bağlantı kullanıldığında, bağlı bağlantılar **(sp_getbindtoken** ve **sp_bindsession)** gerekliydi.</span><span class="sxs-lookup"><span data-stu-id="b871b-104">In addition, when multiple connections were used in a transactional situation, bound connections (with **sp_getbindtoken** and **sp_bindsession**) were required.</span></span> <span data-ttu-id="b871b-105">Aşağıdaki senaryolar, birden çok bağlantı yerine MARS özellikli bir bağlantının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b871b-105">The following scenarios show how to use a MARS-enabled connection instead of multiple connections.</span></span>  
  
## <a name="using-multiple-commands-with-mars"></a><span data-ttu-id="b871b-106">MARS ile Birden Çok Komut Kullanma</span><span class="sxs-lookup"><span data-stu-id="b871b-106">Using Multiple Commands with MARS</span></span>  
 <span data-ttu-id="b871b-107">Aşağıdaki Konsol uygulaması, iki <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlCommand> nesne ve MARS etkin tek <xref:System.Data.SqlClient.SqlConnection> bir nesne ile iki nesne nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b871b-107">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with two <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b871b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b871b-108">Example</span></span>  
 <span data-ttu-id="b871b-109">Örnek, **AdventureWorks** veritabanına tek bir bağlantı açar.</span><span class="sxs-lookup"><span data-stu-id="b871b-109">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="b871b-110">Bir <xref:System.Data.SqlClient.SqlCommand> nesne kullanılarak, a <xref:System.Data.SqlClient.SqlDataReader> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b871b-110">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="b871b-111">Okuyucu kullanıldığında, ikinci okuyucu <xref:System.Data.SqlClient.SqlDataReader> için WHERE yan tümcesine giriş olarak ilk <xref:System.Data.SqlClient.SqlDataReader> inden gelen verileri kullanarak ikinci bir açılır.</span><span class="sxs-lookup"><span data-stu-id="b871b-111">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b871b-112">Aşağıdaki örnek, SQL Server ile birlikte verilen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b871b-112">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="b871b-113">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklenmiş ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="b871b-113">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="b871b-114">Bağlantı dizesini ortamınız için gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b871b-114">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
## <a name="reading-and-updating-data-with-mars"></a><span data-ttu-id="b871b-115">MARS ile Verileri Okuma ve Güncelleme</span><span class="sxs-lookup"><span data-stu-id="b871b-115">Reading and Updating Data with MARS</span></span>  
 <span data-ttu-id="b871b-116">MARS, birden fazla bekleyen işlemle hem okuma işlemleri hem de veri işleme dili (DML) işlemleri için bir bağlantı kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b871b-116">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="b871b-117">Bu özellik, bağlantı meşgul hataları ile başa çıkmak için bir uygulama ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b871b-117">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="b871b-118">Buna ek olarak, MARS genellikle daha fazla kaynak tüketen sunucu tarafı imleçlerinin kullanımını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b871b-118">In addition, MARS can replace the use of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="b871b-119">Son olarak, birden çok işlem tek bir bağlantı da çalışabildiği için, aynı işlem bağlamını paylaşarak **sp_getbindtoken** kullanma gereksinimini ortadan kaldırabilir ve sistem depolanan yordamları **sp_bindsession.**</span><span class="sxs-lookup"><span data-stu-id="b871b-119">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b871b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b871b-120">Example</span></span>  
 <span data-ttu-id="b871b-121">Aşağıdaki Konsol uygulaması, üç <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlCommand> nesne ve MARS etkin tek <xref:System.Data.SqlClient.SqlConnection> bir nesne ile iki nesne nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b871b-121">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="b871b-122">İlk komut nesnesi, kredi derecelendirmesi 5 olan satıcıların listesini alır.</span><span class="sxs-lookup"><span data-stu-id="b871b-122">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="b871b-123">İkinci komut nesnesi, belirli <xref:System.Data.SqlClient.SqlDataReader> satıcının tüm <xref:System.Data.SqlClient.SqlDataReader> ürünleriyle ikinciyi yüklemek için a'dan sağlanan satıcı kimliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b871b-123">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="b871b-124">Her ürün kaydı ikinci <xref:System.Data.SqlClient.SqlDataReader>tarafından ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="b871b-124">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="b871b-125">Yeni **OnOrderQty'nin** ne olması gerektiğini belirlemek için bir hesaplama yapılır.</span><span class="sxs-lookup"><span data-stu-id="b871b-125">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="b871b-126">Üçüncü komut nesnesi daha sonra **ProductVendor** tablosunu yeni değerle güncelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b871b-126">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="b871b-127">Tüm bu işlem, sonunda geri alınır tek bir işlem içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="b871b-127">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b871b-128">Aşağıdaki örnek, SQL Server ile birlikte verilen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b871b-128">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="b871b-129">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklenmiş ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="b871b-129">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="b871b-130">Bağlantı dizesini ortamınız için gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b871b-130">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b871b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b871b-131">See also</span></span>

- [<span data-ttu-id="b871b-132">Birden Çok Etkin Sonuç Kümesi (MARS)</span><span class="sxs-lookup"><span data-stu-id="b871b-132">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="b871b-133">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b871b-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
