---
title: Kod örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 8a0a7c6166bb4cfc8064faa20056fda16b593e81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151773"
---
# <a name="adonet-code-examples"></a>ADO.NET kod örnekleri
Bu konudaki kod listeleri, aşağıdaki ADO.NET teknolojilerini kullanarak veritabanından nasıl veri alınarak alınabildiğini gösterir:

- ADO.NET veri sağlayıcıları:

  - [SqlClient](#sqlclient) `System.Data.SqlClient`( )

  - [OleDb](#oledb) `System.Data.OleDb`( )

  - [Odbc](#odbc) `System.Data.Odbc`( )

  - [OracleClient](#oracleclient) `System.Data.OracleClient`( )

- ADO.NET Varlık Çerçevesi:

  - [LINQ - Varlıklar](#linq-to-entities)

  - [Yazılan ObjectQuery](#typed-objectquery)

  - [EntityClient](#entityclient) `System.Data.EntityClient`( )

- [LINQ to SQL](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a>ADO.NET veri sağlayıcısı örnekleri
Aşağıdaki kod listeleri, veri sağlayıcıları ADO.NET kullanarak veritabanından nasıl veri alınır gösteriş gösterir. Veriler bir `DataReader`' de döndürülür. Daha fazla bilgi için [bkz.](retrieving-data-using-a-datareader.md)

### <a name="sqlclient"></a>Sqlclient
Bu örnekteki kod, Microsoft SQL Server'daki örnek veritabanına bağlanabileceğinizi `Northwind` varsayar. Kod, Ürünler <xref:System.Data.SqlClient.SqlCommand> tablosundan satırları seçmek için bir <xref:System.Data.SqlClient.SqlParameter> satır oluşturur ve bu durumda 5,, bir birim fiyatı belirtilen parametre değerinden daha büyük olan satırlarla sonuçları sınırlamak için a ekler. Kod <xref:System.Data.SqlClient.SqlConnection> çıktığında kaynakların `using` kapatılmasını ve imha edilmesini sağlayan bir blok içinde açılır. Kod, bir <xref:System.Data.SqlClient.SqlDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a>OleDb
Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabileceğinizi varsayar. Kod, Ürünler <xref:System.Data.OleDb.OleDbCommand> tablosundan satırları seçmek için bir <xref:System.Data.OleDb.OleDbParameter> satır oluşturur ve bu durumda 5,, bir birim fiyatı belirtilen parametre değerinden daha büyük olan satırlarla sonuçları sınırlamak için a ekler. Kod <xref:System.Data.OleDb.OleDbConnection> çıktığında kaynakların `using` kapatılmasını ve bertaraf edilmesini sağlayan bir bloğun içinde açılır. Kod, bir <xref:System.Data.OleDb.OleDbDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a>Odbc
Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabileceğinizi varsayar. Kod, Ürünler <xref:System.Data.Odbc.OdbcCommand> tablosundan satırları seçmek için bir <xref:System.Data.Odbc.OdbcParameter> satır oluşturur ve bu durumda 5,, bir birim fiyatı belirtilen parametre değerinden daha büyük olan satırlarla sonuçları sınırlamak için a ekler. Kod <xref:System.Data.Odbc.OdbcConnection> çıktığında kaynakların `using` kapatılmasını ve imha edilmesini sağlayan bir blok içinde açılır. Kod, bir <xref:System.Data.Odbc.OdbcDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a>OracleClient
Bu örnekteki kod DEMO'ya bir bağlantı varsayar. Oracle sunucusunda MÜŞTERİ. System.Data.OracleClient.dll adresine de bir başvuru eklemeniz gerekir. Kod, verileri bir <xref:System.Data.OracleClient.OracleDataReader>' de döndürür.

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a>Varlık Çerçevesi örnekleri
Aşağıdaki kod listeleri, Varlık Veri Modeli'ndeki (EDM) varlıkları sorgulayarak veri kaynağından nasıl veri alınarak alınabildiğini gösterir. Bu örnekler, Northwind örnek veritabanını temel alan bir model kullanır. Varlık Çerçevesi hakkında daha fazla bilgi için Entity [Framework Genel Bakış'a](./ef/overview.md)bakın.

### <a name="linq-to-entities"></a>LINQ - Varlıklar
Bu örnekteki kod, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak yansıtılan kategoriler nesneleri olarak verileri döndürmek için bir LINQ sorgusu kullanır. Daha fazla bilgi için [LINQ to Varlıklara Genel Bakış'a](./ef/language-reference/linq-to-entities.md)bakın.

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

### <a name="typed-objectquery"></a>Yazılan ObjectQuery
Bu örnekteki kod, <xref:System.Data.Objects.ObjectQuery%601> kategoriler nesneleri olarak veri döndürmek için bir kullanır. Daha fazla bilgi için [Nesne Sorguları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100))bakın.

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
Bu örnekteki kod, <xref:System.Data.EntityClient.EntityCommand> Bir Varlık SQL sorgusu yürütmek için bir kullanır. Bu sorgu, Kategoriler varlık türü örneklerini temsil eden kayıtların listesini döndürür. Sonuç <xref:System.Data.EntityClient.EntityDataReader> kümesindeki veri kayıtlarına erişmek için bir kullanılır. Daha fazla bilgi için Entity [Framework için EntityClient Sağlayıcısı'na](./ef/entityclient-provider-for-the-entity-framework.md)bakın.

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

## <a name="linq-to-sql"></a>LINQ to SQL
Bu örnekteki kod, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak yansıtılan kategoriler nesneleri olarak verileri döndürmek için bir LINQ sorgusu kullanır. Bu örnek, Northwind veri bağlamını temel adamaktadır. Daha fazla bilgi için [bkz.](./sql/linq/getting-started.md)

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
- [Veri Uygulamaları Oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))
- [Varlık Veri Modelini Sorgulama (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))
- [Nasıl yapilir: Anonim Tür Nesnelerini Döndüren Bir Sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))
