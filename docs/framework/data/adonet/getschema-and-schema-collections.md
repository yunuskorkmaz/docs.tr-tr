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
# <a name="getschema-and-schema-collections"></a>GetSchema ve Şema Koleksiyonları
.NET Framework yönetilen sağlayıcıların her birinde bulunan **bağlantı** sınıfları, şu anda bağlı olan veritabanı ile ilgili şema bilgilerini ve ' den döndürülen şema bilgilerini almak için kullanılan bir **GetSchema** yöntemi uygular.  **GetSchema** yöntemi bir <xref:System.Data.DataTable>biçiminde gelir. **GetSchema** yöntemi, döndürülecek şema koleksiyonunu belirtmek ve döndürülen bilgi miktarını kısıtlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş bir yöntemdir.  
  
## <a name="specifying-the-schema-collections"></a>Şema koleksiyonlarını belirtme  
 **GetSchema** yönteminin ilk isteğe bağlı parametresi, bir dize olarak belirtilen koleksiyon adıdır. İki tür şema koleksiyonu vardır: tüm sağlayıcılar için ortak olan ortak şema koleksiyonları ve her sağlayıcıya özgü belirli şema koleksiyonları.  
  
 .NET Framework yönetilen bir sağlayıcıyı, **GetSchema** yöntemini bağımsız değişken olmadan veya "MetaDataCollections" şema koleksiyonu adıyla çağırarak, desteklenen şema koleksiyonlarının listesini belirleyecek şekilde sorgulayabilirsiniz. Bu, desteklenen şema <xref:System.Data.DataTable> koleksiyonlarının listesi, her birinin desteklediği kısıtlamaların sayısı ve kullandıkları tanımlayıcı bölümlerinin sayısı ile birlikte döndürülür.  
  
### <a name="retrieving-schema-collections-example"></a>Şema koleksiyonları örneği alınıyor  
 Aşağıdaki örneklerde, **AdventureWorks** örnek veritabanında bulunan tüm <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> tablolar hakkında şema bilgilerini almak için SQL Server <xref:System.Data.SqlClient.SqlConnection> sınıfının .NET Framework veri sağlayıcısı yönteminin nasıl kullanılacağı gösterilmektedir:  
  
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
