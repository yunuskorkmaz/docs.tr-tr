---
title: GetSchema ve Şema Koleksiyonları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: e18c23e9bbec97a64110aba6eb7241761ecece06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149563"
---
# <a name="getschema-and-schema-collections"></a>GetSchema ve Şema Koleksiyonları
.NET Framework yönetilen sağlayıcıların her birinde **Bağlantı** sınıfları, şu anda bağlı olan veritabanı hakkında şema bilgilerini almak için kullanılan bir **GetSchema** yöntemi uygular ve <xref:System.Data.DataTable> **GetSchema** yönteminden döndürülen şema bilgileri bir . **GetSchema** yöntemi, şema koleksiyonunun geri dönmesini belirtmek ve döndürülen bilgi miktarını kısıtlamak için isteğe bağlı parametreler sağlayan aşırı yüklü bir yöntemdir.  
  
## <a name="specifying-the-schema-collections"></a>Şema Koleksiyonlarının Belirtilmesi  
 **GetSchema** yönteminin ilk isteğe bağlı parametresi, dize olarak belirtilen toplama adıdır. İki tür şema koleksiyonu vardır: tüm sağlayıcılar için ortak olan ortak şema koleksiyonları ve her sağlayıcıya özgü belirli şema koleksiyonları.  
  
 **GetSchema** yöntemini bağımsız değişken olmadan veya şema toplama adı "MetaDataCollections" ile çağırarak desteklenen şema koleksiyonlarının listesini belirlemek için bir .NET Framework yönetilen sağlayıcısını sorgulayabilirsiniz. Bu, desteklenen <xref:System.Data.DataTable> şema koleksiyonlarının bir listesini, her destekledikleri kısıtlamaların sayısını ve kullandıkları tanımlayıcı parçalarının sayısını döndürecektir.  
  
### <a name="retrieving-schema-collections-example"></a>Şema Koleksiyonları Nın Alınması Örneği  
 Aşağıdaki örnekler, **AdventureWorks** <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> örnek veritabanında yer alan tüm tablolar <xref:System.Data.SqlClient.SqlConnection> hakkında şema bilgilerini almak için SQL Server sınıfı için .NET Framework Data Provider yönteminin nasıl kullanılacağını göstermektedir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
