---
title: Şema Kısıtlamaları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: b5044d39d1dc5d2fa7d2ce691cdda7075fa0e32a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151209"
---
# <a name="schema-restrictions"></a>Şema Kısıtlamaları
İsteğe bağlı ikinci parametresi **GetSchema** yöntemdir şema bilgileri miktarını sınırlamak için kullanılan kısıtlamaları döndürdü ve geçer **GetSchema** dize dizisi olarak yöntemi . Bu kısıtlama sayıya eşdeğerdir ve geçirebileceğiniz değerleri dizisinde konumunu belirler.  
  
 Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklamaktadır. SQL Server şema koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Kısıtlama değerleri belirtme  
 "Tablo" şema koleksiyonundaki kısıtlamaları birini kullanmak için yalnızca dört öğe içeren bir dizeler dizisi oluşturun, sonra bir değer kısıtlaması numarasıyla eşleşen öğe yerleştirin. Tarafından tabloları kısıtlamak için döndürülen **GetSchema** yöntemi yalnızca bu tablolara "Sales" şema öğesine iletmeden önce "Sales" için bir dizinin ikinci öğe ayarlama **GetSchema** yöntemi.  
  
> [!NOTE]
>  Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun. Kısıtlama varsayılan sütun var. yine de geriye dönük uyumluluğa yöneliktir, ancak şu anda göz ardı edilir. Kısıtlama değerleri belirtmek için bir SQL ekleme saldırısına riskini en aza indirmek için dize değiştirme yerine parametreli sorgular kullanılması gerekir.  
  
> [!NOTE]
>  Dizideki öğelerin sayısını başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır. bir <xref:System.ArgumentException> oluşturulur. Olabilir en yüksek kısıtlama sayısı daha az. Eksik kısıtlamaları (sınırsız) null olarak kabul edilir.  
  
 Desteklenen kısıtlama listesine çağırarak belirlemek için bir .NET Framework yönetilen sağlayıcı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı. Bu döndürür bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> tüm bulunan tabloların şema bilgilerini almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için döndürülen yalnızca şema "Satış" tablolar için:  
  
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
  
## <a name="sql-server-schema-restrictions"></a>SQL Server şema kısıtlamaları  
 SQL Server şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir.  
  
### <a name="users"></a>Kullanıcılar  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_name|@Name|name|1.|  
  
### <a name="databases"></a>Veritabanları  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Ad|@Name|Ad|1.|  
  
### <a name="tables"></a>Tabloları  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Sütunlar  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Görünümler  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|VIEW_CATALOG|1.|  
|Sahip|@Owner|VIEW_SCHEMA|2|  
|Tablo|@Table|VIEW_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1.|  
|Sahip|@Owner|SPECIFIC_SCHEMA|2|  
|Ad|@Name|SPECIFIC_NAME|3|  
|Parametre|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Yordamlar  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1.|  
|Sahip|@Owner|SPECIFIC_SCHEMA|2|  
|Ad|@Name|SPECIFIC_NAME|3|  
|Tür|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1.|  
|Sahip|@Owner|user_name()|2|  
|Tablo|@Table|o.Name|3|  
|ConstraintName|@ConstraintName|x.name|4|  
|Sütun|@Column|c.Name|5|  
  
### <a name="indexes"></a>Dizinleri  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1.|  
|Sahip|@Owner|user_name()|2|  
|Tablo|@Table|o.Name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|Assemblies.Name|1.|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|CONSTRAINT_CATALOG|1.|  
|Sahip|@Owner|CONSTRAINT_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Ad|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 şema kısıtlamaları  
 SQL Server 2008 şema koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmiştir. Bu kısıtlamalar, SQL Server 2008 ve .NET Framework 3.5 SP1 sürümle geçerli başlıyoruz. .NET Framework ve SQL Server'ın önceki sürümlerinde desteklenmez.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Kısıtlama adı|Parametre Adı|Varsayılan kısıtlama|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
