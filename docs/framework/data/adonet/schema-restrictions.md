---
title: Şema Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149017"
---
# <a name="schema-restrictions"></a>Şema Kısıtlamaları
**GetSchema** yönteminin ikinci isteğe bağlı parametresi, döndürülen şema bilgi miktarını sınırlamak için kullanılan kısıtlamalardır ve bir dizi dize olarak **GetSchema** yöntemine geçirilir. Dizideki konum geçebileceğiniz değerleri belirler ve bu kısıtlama numarasına eşdeğerdir.  
  
 Örneğin, aşağıdaki tabloda SQL Server için .NET Framework Data Provider kullanarak "Tablolar" şema koleksiyonu tarafından desteklenen kısıtlamalar açıklanmaktadır. Bu konunun sonunda SQL Server şema koleksiyonları için ek kısıtlamalar listelenmiştir.  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Name|TABLE_NAME|3|  
|Tablo Tipi|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Kısıtlama Değerlerini Belirtme  
 "Tablolar" şema koleksiyonunun kısıtlamalarından birini kullanmak için, dört öğeli bir dizi dize oluşturmanız ve ardından kısıtlama numarasıyla eşleşen öğeye bir değer yerleştirmeniz yeterlidir. Örneğin, **GetSchema** yöntemi tarafından döndürülen tabloları yalnızca "Satış" şemasındaki tablolarla sınırlamak için, dizinin ikinci öğesini **GetSchema** yöntemine geçirmeden önce "Satışlar" olarak ayarlayın.  
  
> [!NOTE]
> Kısıtlamalar için `SqlClient` koleksiyonlar `OracleClient` ve `ParameterName` ek bir sütun var. Kısıtlama varsayılan sütunu geriye dönük uyumluluk için hala oradadır, ancak şu anda yoksayılır. Kısıtlama değerleri belirtilirken bir SQL enjeksiyon atağı riskini en aza indirmek için dize değiştirme yerine parametreli sorgular kullanılmalıdır.  
  
> [!NOTE]
> Dizideki öğe sayısı, belirtilen şema koleksiyonu <xref:System.ArgumentException> için desteklenen kısıtlama sayısından daha az veya eşit olmalıdır. Maksimum kısıtlama sayısından daha az olabilir. Eksik kısıtlamaların geçersiz (sınırsız) olduğu varsayılır.  
  
 **GetSchema** yöntemini "Kısıtlamalar" olan schema koleksiyonunun adı ile arayarak desteklenen kısıtlamaların listesini belirlemek için bir .NET Framework yönetilen sağlayıcıyı sorgulayabilirsiniz. Bu, koleksiyon <xref:System.Data.DataTable> adlarının, kısıtlama adlarının, varsayılan kısıtlama değerlerinin ve kısıtlama numaralarının bir listesini döndürür.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekler, **AdventureWorks** <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> örnek veritabanında yer alan tüm tablolar <xref:System.Data.SqlClient.SqlConnection> hakkında şema bilgilerini almak ve yalnızca "Satış" şemasındaki tablolara döndürülen bilgileri kısıtlamak için SQL Server sınıfı için .NET Framework Data Provider yönteminin nasıl kullanılacağını göstermektedir:  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
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
    string connectionString =
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
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
  
## <a name="sql-server-schema-restrictions"></a>SQL Server Şema Kısıtlamaları  
 Aşağıdaki tablolarda SQL Server şema koleksiyonlarının kısıtlamaları listeleneb.r  
  
### <a name="users"></a>Kullanıcılar  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Kullanıcı_adı|@Name|ad|1|  
  
### <a name="databases"></a>Veritabanları  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Adı|@Name|Adı|1|  
  
### <a name="tables"></a>Tablolar  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Name|TABLE_NAME|3|  
|Tablo Tipi|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Sütunlar  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Görünümler  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>Sütunları Görüntüle  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|VIEW_CATALOG|1|  
|Sahip|@Owner|VIEW_SCHEMA|2|  
|Tablo|@Table|VIEW_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>Prosedür Parametreleri  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1|  
|Sahip|@Owner|SPECIFIC_SCHEMA|2|  
|Adı|@Name|SPECIFIC_NAME|3|  
|Parametre|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Yordamlar  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1|  
|Sahip|@Owner|SPECIFIC_SCHEMA|2|  
|Adı|@Name|SPECIFIC_NAME|3|  
|Tür|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Sahip|@Owner|user_name()|2|  
|Tablo|@Table|o.name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|Sütun|@Column|c.name|5|  
  
### <a name="indexes"></a>Dizinler  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Sahip|@Owner|user_name()|2|  
|Tablo|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|türleri.assembly_class|2|  
  
### <a name="foreignkeys"></a>Yabancı Anahtarlar  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|CONSTRAINT_CATALOG|1|  
|Sahip|@Owner|CONSTRAINT_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Adı|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 Şema Kısıtlamaları  
 Aşağıdaki tablolarda SQL Server 2008 şema koleksiyonlarının kısıtlamaları listeleneb.)'de. Bu kısıtlamalar ,NET Framework ve SQL Server 2008 sürümü 3.5 SP1 ile başlayan geçerlidir. .NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.  
  
### <a name="columnsetcolumns"></a>SütunSeti Sütunlar  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>Tüm Sütunlar  
  
|Kısıtlama Adı|Parametre Adı|Kısıtlama Varsayılan|Kısıtlama Numarası|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
