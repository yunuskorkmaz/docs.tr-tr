---
title: Kod örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 4f0cbc06c03c0d122fc69b8a396570919ac14970
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980294"
---
# <a name="adonet-code-examples"></a>ADO.NET kod örnekleri
Bu konudaki kod listeleri, aşağıdaki ADO.NET teknolojilerini kullanarak bir veritabanından nasıl veri alınacağını gösterir:

- ADO.NET veri sağlayıcıları:

  - [SqlClient](#sqlclient) (`System.Data.SqlClient`)

  - [OLEDB](#oledb) (`System.Data.OleDb`)

  - [Odbc](#odbc) (`System.Data.Odbc`)

  - [OracleClient](#oracleclient) (`System.Data.OracleClient`)

- ADO.NET Entity Framework:

  - [LINQ to Entities](#linq-to-entities)

  - [Tür ObjectQuery](#typed-objectquery)

  - [EntityClient](#entityclient) (`System.Data.EntityClient`)

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>ADO.NET veri sağlayıcısı örnekleri
Aşağıdaki kod listelerinde, ADO.NET veri sağlayıcıları kullanılarak bir veritabanından nasıl veri alacağınızı gösterilmektedir. Veriler bir `DataReader`döndürülür. Daha fazla bilgi için bkz. [DataReader kullanarak veri alma](retrieving-data-using-a-datareader.md).

### <a name="sqlclient"></a>SqlClient
Bu örnekteki kod, Microsoft SQL Server `Northwind` örnek veritabanına bağlanabildiğinizi varsayar. Kod, Ürünler tablosundan satırları seçmek için bir <xref:System.Data.SqlClient.SqlCommand> oluşturur, bu durumda 5, belirtilen parametre değerinden daha büyük bir UnitPrice değeri olan satırlara sonuçları kısıtlamak için bir <xref:System.Data.SqlClient.SqlParameter> ekler. <xref:System.Data.SqlClient.SqlConnection>, bir `using` bloğunun içinde açılır. Bu, kodun çıkış sırasında kaynakların kapatılmasını ve atılmasını sağlar. Kod, bir <xref:System.Data.SqlClient.SqlDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabildiğinizi varsayar. Kod, Ürünler tablosundan satırları seçmek için bir <xref:System.Data.OleDb.OleDbCommand> oluşturur, bu durumda 5, belirtilen parametre değerinden daha büyük bir UnitPrice değeri olan satırlara sonuçları kısıtlamak için bir <xref:System.Data.OleDb.OleDbParameter> ekler. <xref:System.Data.OleDb.OleDbConnection>, bir `using` bloğunun içinde açılır. Bu, kodun çıkış sırasında kaynakların kapatılmasını ve atılmasını sağlar. Kod, bir <xref:System.Data.OleDb.OleDbDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabildiğinizi varsayar. Kod, Ürünler tablosundan satırları seçmek için bir <xref:System.Data.Odbc.OdbcCommand> oluşturur, bu durumda 5, belirtilen parametre değerinden daha büyük bir UnitPrice değeri olan satırlara sonuçları kısıtlamak için bir <xref:System.Data.Odbc.OdbcParameter> ekler. <xref:System.Data.Odbc.OdbcConnection>, bir `using` bloğunun içinde açılır. Bu, kodun çıkış sırasında kaynakların kapatılmasını ve atılmasını sağlar. Kod, bir <xref:System.Data.Odbc.OdbcDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a>OracleClient
Bu örnekteki kod, TANıTıMA bir bağlantı olduğunu varsayar. Bir Oracle sunucusunda MÜŞTERI. System. Data. OracleClient. dll ' ye de bir başvuru eklemeniz gerekir. Kod, verileri bir <xref:System.Data.OracleClient.OracleDataReader>döndürür.

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Entity Framework örnekleri
Aşağıdaki kod listeleri bir Varlık Veri Modeli (EDM) içindeki varlıkları sorgulayarak bir veri kaynağından nasıl veri alınacağını göstermektedir. Bu örnekler, Northwind örnek veritabanına dayalı bir model kullanır. Entity Framework hakkında daha fazla bilgi için bkz. [Entity Framework genel bakış](./ef/overview.md).

### <a name="linq-to-entities"></a>LINQ - Varlıklar
Bu örnekteki kod, verileri kategori nesneleri olarak döndürmek için, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak tasarlanan bir LINQ sorgusu kullanır. Daha fazla bilgi için bkz. [LINQ to Entities genel bakış](./ef/language-reference/linq-to-entities.md).

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a>Tür ObjectQuery
Bu örnekteki kod, verileri kategori nesneleri olarak döndürmek için bir <xref:System.Data.Objects.ObjectQuery%601> kullanır. Daha fazla bilgi için bkz. [nesne sorguları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in 
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a>EntityClient
Bu örnekteki kod Entity SQL bir sorgu yürütmek için <xref:System.Data.EntityClient.EntityCommand> kullanır. Bu sorgu, kategori varlık türünün örneklerini temsil eden kayıtların bir listesini döndürür. Sonuç kümesindeki veri kayıtlarına erişmek için bir <xref:System.Data.EntityClient.EntityDataReader> kullanılır. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](./ef/entityclient-provider-for-the-entity-framework.md).

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName 
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr = 
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using 
    End Sub
End Class
```

## <a name="linq-to-sql"></a>LINQ - SQL
Bu örnekteki kod, verileri kategori nesneleri olarak döndürmek için, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak tasarlanan bir LINQ sorgusu kullanır. Bu örnek, Northwind veri bağlamını temel alır. Daha fazla bilgi için bkz [. Başlarken](./sql/linq/getting-started.md).

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using 
    End Sub
End Class
```

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [Veri uygulamaları oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))
- [Varlık Veri Modeli sorgulama (Entity Framework görevler)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))
- [Nasıl yapılır: anonim tür nesneleri döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))
