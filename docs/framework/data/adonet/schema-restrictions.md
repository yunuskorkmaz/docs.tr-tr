---
title: "Şema kısıtlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c254865800694af8eb754c3e8d4072688fd7e89a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="schema-restrictions"></a>Şema kısıtlamaları
İkinci isteğe bağlı parametresi, **GetSchema** yöntemdir şema bilgi tutarını sınırlamak için kullanılan kısıtlamaları döndürülür ve için geçirilen **GetSchema** bir dize dizisi olarak yöntemi . Dizideki konumu geçirebilirsiniz değerleri belirler ve bu kısıtlama sayıya eşdeğerdir.  
  
 Örneğin, aşağıdaki tabloda, SQL Server için .NET Framework veri sağlayıcısı kullanarak "Tablo" şema koleksiyonu tarafından desteklenen kısıtlamaları açıklar. SQL Server şeması koleksiyonları için ek kısıtlamalar, bu konunun sonunda listelenmiştir.  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Kısıtlama değerleri belirtme  
 "Tablo" şema koleksiyonu kısıtlamalarını birini kullanmak için yalnızca bir dizeler dizisi ile dört öğeleri oluşturun, sonra bir değer kısıtlama numarasıyla eşleşen öğe yerleştirin. Örneğin, tablolar kısıtlamak için tarafından geri döndürülen **GetSchema** geçirmeden önce "Satış" diziye ikinci öğesini set yöntemi yalnızca "Satış" şemasında tablolara **GetSchema** yöntemi.  
  
> [!NOTE]
>  Kısıtlamaları koleksiyonlar için `SqlClient` ve `OracleClient` ek bir sahip `ParameterName` sütun. Kısıtlama varsayılan sütunu yine için geriye dönük uyumluluk yoktur, ancak şu anda göz ardı edilir. Dize değiştirme yerine parametreli sorgular kısıtlama değerleri belirtirken SQL ekleme saldırı riskini en aza indirmek için kullanılmalıdır.  
  
> [!NOTE]
>  Dizideki öğelerin sayısı başka belirtilen şema koleksiyonu için desteklenen kısıtlama sayısı küçük veya buna eşit olmalıdır bir <xref:System.ArgumentException> oluşturulur. Olabilir kısıtlamaları maksimum sayısından az. Eksik kısıtlamaları (sınırsız) null olduğu varsayılır.  
  
 Çağıran desteklenen kısıtlamaların listesini belirlemek için bir .NET Framework yönetilen sağlayıcısı sorgulayabilirsiniz **GetSchema** yöntemi "kısıtlamaları" kısıtlamaları şema koleksiyonu adı. Bu döndürülecek bir <xref:System.Data.DataTable> koleksiyon adları, kısıtlama adları, varsayılan kısıtlama değerleri ve kısıtlama numaraları listesi ile.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekler nasıl kullanılacağını gösteren <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server için .NET Framework veri sağlayıcısı yöntemi <xref:System.Data.SqlClient.SqlConnection> şema tüm içinde yer alan tabloları hakkında bilgi almak için sınıf **AdventureWorks**örnek veritabanı ve bilgileri kısıtlamak için yalnızca "Satış" şemasında tablolar için:  
  
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
 SQL Server şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir.  
  
### <a name="users"></a>Kullanıcılar  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_name|@Name|name|1.|  
  
### <a name="databases"></a>Veritabanları  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Ad|@Name|Ad|1.|  
  
### <a name="tables"></a>tabloları  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Sütunlar  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Görünümler  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|VIEW_CATALOG|1.|  
|Sahip|@Owner|VIEW_SCHEMA|2|  
|Tablo|@Table|VIEW_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1.|  
|Sahip|@Owner|SPECIFIC_SCHEMA|2|  
|Ad|@Name|SPECIFIC_NAME|3|  
|Parametre|@Parameter|PARAMETRE_ADÝ|4|  
  
### <a name="procedures"></a>Yordamlar  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1.|  
|Sahip|@Owner|SPECIFIC_SCHEMA|2|  
|Ad|@Name|SPECIFIC_NAME|3|  
|Tür|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1.|  
|Sahip|@Owner|USER_NAME()|2|  
|Tablo|@Table|o.Name|3|  
|ConstraintName|@ConstraintName|x.Name|4|  
|Sütun|@Column|c.Name|5|  
  
### <a name="indexes"></a>Dizinler  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1.|  
|Sahip|@Owner|USER_NAME()|2|  
|Tablo|@Table|o.Name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|Assemblies.Name|1.|  
|udt_name|@UDTName|Types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|CONSTRAINT_CATALOG|1.|  
|Sahip|@Owner|CONSTRAINT_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Ad|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 şema kısıtlamaları  
 SQL Server 2008 şeması koleksiyonları için kısıtlamaları aşağıdaki tablolarda listelenmektedir. Bu kısıtlamalar sürüm SQL Server 2008 ve .NET Framework 3.5 SP1 ile başlayan geçerli ' dir. Önceki .NET Framework ve SQL Server sürümlerinde desteklenmez.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Kısıtlama adı|Parametre Adı|Kısıtlama varsayılan|Kısıtlama sayısı|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1.|  
|Sahip|@Owner|TABLE_SCHEMA|2|  
|Tablo|@Table|TABLE_NAME|3|  
|Sütun|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
