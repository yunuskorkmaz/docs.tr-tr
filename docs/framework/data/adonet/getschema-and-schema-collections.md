---
title: GetSchema ve Şema Koleksiyonları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 4ac0216ce2965d555f7283ba66a085ea9d7cac3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783842"
---
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="5968e-102">GetSchema ve Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="5968e-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="5968e-103">.NET Framework yönetilen sağlayıcıların her birinde bulunan **bağlantı** sınıfları, şu anda bağlı olan veritabanı ile ilgili şema bilgilerini ve ' den döndürülen şema bilgilerini almak için kullanılan bir **GetSchema** yöntemi uygular.  **GetSchema** yöntemi bir <xref:System.Data.DataTable>biçiminde gelir.</span><span class="sxs-lookup"><span data-stu-id="5968e-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="5968e-104">**GetSchema** yöntemi, döndürülecek şema koleksiyonunu belirtmek ve döndürülen bilgi miktarını kısıtlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="5968e-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="5968e-105">Şema koleksiyonlarını belirtme</span><span class="sxs-lookup"><span data-stu-id="5968e-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="5968e-106">**GetSchema** yönteminin ilk isteğe bağlı parametresi, bir dize olarak belirtilen koleksiyon adıdır.</span><span class="sxs-lookup"><span data-stu-id="5968e-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="5968e-107">İki tür şema koleksiyonu vardır: tüm sağlayıcılar için ortak olan ortak şema koleksiyonları ve her sağlayıcıya özgü belirli şema koleksiyonları.</span><span class="sxs-lookup"><span data-stu-id="5968e-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="5968e-108">.NET Framework yönetilen bir sağlayıcıyı, **GetSchema** yöntemini bağımsız değişken olmadan veya "MetaDataCollections" şema koleksiyonu adıyla çağırarak, desteklenen şema koleksiyonlarının listesini belirleyecek şekilde sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5968e-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="5968e-109">Bu, desteklenen şema <xref:System.Data.DataTable> koleksiyonlarının listesi, her birinin desteklediği kısıtlamaların sayısı ve kullandıkları tanımlayıcı bölümlerinin sayısı ile birlikte döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5968e-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="5968e-110">Şema koleksiyonları örneği alınıyor</span><span class="sxs-lookup"><span data-stu-id="5968e-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="5968e-111">Aşağıdaki örneklerde, **AdventureWorks** örnek veritabanında bulunan tüm <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> tablolar hakkında şema bilgilerini almak için SQL Server <xref:System.Data.SqlClient.SqlConnection> sınıfının .NET Framework veri sağlayıcısı yönteminin nasıl kullanılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5968e-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,    
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
   End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
   Console.WriteLine("Press any key to continue.");  
   Console.ReadKey();  
   }  
 }  
  
  private static string GetConnectionString()  
  {  
   // To avoid storing the connection string in your code,  
   // you can retrieve it from a configuration file.  
   return "Data Source=(local);Database=AdventureWorks;" +  
      "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5968e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5968e-112">See also</span></span>

- [<span data-ttu-id="5968e-113">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="5968e-113">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="5968e-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5968e-114">ADO.NET Overview</span></span>](ado-net-overview.md)
