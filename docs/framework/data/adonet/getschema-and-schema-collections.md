---
title: GetSchema ve şeması koleksiyonları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 1694a6de515e5326264f345f50d0730fe2a62e4f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763949"
---
# <a name="getschema-and-schema-collections"></a>GetSchema ve şeması koleksiyonları
**Bağlantı** her .NET Framework yönetilen sağlayıcıları uygulayan sınıflar bir **GetSchema** şu anda bağlı olduğu, veritabanında ilgili şema bilgileri almak için kullanılan yöntem ve döndürülen şema bilgileri **GetSchema** yöntemi gelen biçiminde bir <xref:System.Data.DataTable>. **GetSchema** dönmek için şema koleksiyonu belirtme ve döndürülen bilgi tutarını sınırlamak için isteğe bağlı parametreler sağlayan bir aşırı yüklenmiş yöntemin bir yöntemdir.  
  
## <a name="specifying-the-schema-collections"></a>Şema koleksiyonları belirtme  
 İlk isteğe bağlı parametresi **GetSchema** bir dize olarak belirtilen bir koleksiyon adını bir yöntemdir. Şema koleksiyonların iki tür vardır: tüm sağlayıcılar için ortak olan ortak şeması koleksiyonları ve her sağlayıcıya özgü belirli şeması koleksiyonları.  
  
 Çağıran desteklenen şema koleksiyonları listesini belirlemek için bir .NET Framework yönetilen sağlayıcısı sorgulayabilirsiniz **GetSchema** yöntemi bağımsız değişken içermeyen veya şema koleksiyonu adı "MetaDataCollections". Bu döndürülecek bir <xref:System.Data.DataTable> desteklenen şeması koleksiyonları, her destekledikleri kısıtlama sayısı ve kullandıkları tanımlayıcı bölümlerinin sayısını listesini içeren.  
  
### <a name="retrieving-schema-collections-example"></a>Şema koleksiyonları örnek alma  
 Aşağıdaki örnekler nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> şema tüm içinde yer alan tabloları hakkında bilgi almak için sınıf **AdventureWorks**örnek veritabanı:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
