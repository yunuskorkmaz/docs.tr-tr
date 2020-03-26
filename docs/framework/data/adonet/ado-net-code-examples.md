---
title: Kod örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 6e0c34e1db50030c78db295f26fcc25b431d3dde
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111809"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="10d3f-102">ADO.NET kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="10d3f-102">ADO.NET code examples</span></span>

<span data-ttu-id="10d3f-103">Bu sayfadaki kod listeleri, aşağıdaki ADO.NET teknolojilerini kullanarak veritabanından nasıl veri alınarak alınabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="10d3f-103">The code listings on this page demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="10d3f-104">ADO.NET veri sağlayıcıları:</span><span class="sxs-lookup"><span data-stu-id="10d3f-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="10d3f-105">[SqlClient](#sqlclient) `System.Data.SqlClient`( )</span><span class="sxs-lookup"><span data-stu-id="10d3f-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="10d3f-106">[OleDb](#oledb) `System.Data.OleDb`( )</span><span class="sxs-lookup"><span data-stu-id="10d3f-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="10d3f-107">[Odbc](#odbc) `System.Data.Odbc`( )</span><span class="sxs-lookup"><span data-stu-id="10d3f-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="10d3f-108">[OracleClient](#oracleclient) `System.Data.OracleClient`( )</span><span class="sxs-lookup"><span data-stu-id="10d3f-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="10d3f-109">ADO.NET Varlık Çerçevesi:</span><span class="sxs-lookup"><span data-stu-id="10d3f-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="10d3f-110">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="10d3f-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="10d3f-111">Yazılan ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="10d3f-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="10d3f-112">[EntityClient](#entityclient) `System.Data.EntityClient`( )</span><span class="sxs-lookup"><span data-stu-id="10d3f-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="10d3f-113">LINQ - SQL</span><span class="sxs-lookup"><span data-stu-id="10d3f-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="10d3f-114">ADO.NET veri sağlayıcısı örnekleri</span><span class="sxs-lookup"><span data-stu-id="10d3f-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="10d3f-115">Aşağıdaki kod listeleri, veri sağlayıcıları ADO.NET kullanarak veritabanından nasıl veri alınır gösteriş gösterir.</span><span class="sxs-lookup"><span data-stu-id="10d3f-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="10d3f-116">Veriler bir `DataReader`' de döndürülür.</span><span class="sxs-lookup"><span data-stu-id="10d3f-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="10d3f-117">Daha fazla bilgi için [bkz.](retrieving-data-using-a-datareader.md)</span><span class="sxs-lookup"><span data-stu-id="10d3f-117">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="10d3f-118">Sqlclient</span><span class="sxs-lookup"><span data-stu-id="10d3f-118">SqlClient</span></span>
<span data-ttu-id="10d3f-119">Bu örnekteki kod, Microsoft SQL Server'daki örnek veritabanına bağlanabileceğinizi `Northwind` varsayar.</span><span class="sxs-lookup"><span data-stu-id="10d3f-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="10d3f-120">Kod, Ürünler <xref:System.Data.SqlClient.SqlCommand> tablosundan satırları seçmek için bir <xref:System.Data.SqlClient.SqlParameter> satır oluşturur ve bu durumda 5,, bir birim fiyatı belirtilen parametre değerinden daha büyük olan satırlarla sonuçları sınırlamak için a ekler.</span><span class="sxs-lookup"><span data-stu-id="10d3f-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="10d3f-121">Kod <xref:System.Data.SqlClient.SqlConnection> çıktığında kaynakların `using` kapatılmasını ve imha edilmesini sağlayan bir blok içinde açılır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="10d3f-122">Kod, bir <xref:System.Data.SqlClient.SqlDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="10d3f-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="10d3f-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="10d3f-123">OleDb</span></span>
<span data-ttu-id="10d3f-124">Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabileceğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="10d3f-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="10d3f-125">Kod, Ürünler <xref:System.Data.OleDb.OleDbCommand> tablosundan satırları seçmek için bir <xref:System.Data.OleDb.OleDbParameter> satır oluşturur ve bu durumda 5,, bir birim fiyatı belirtilen parametre değerinden daha büyük olan satırlarla sonuçları sınırlamak için a ekler.</span><span class="sxs-lookup"><span data-stu-id="10d3f-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="10d3f-126">Kod <xref:System.Data.OleDb.OleDbConnection> çıktığında kaynakların `using` kapatılmasını ve bertaraf edilmesini sağlayan bir bloğun içinde açılır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="10d3f-127">Kod, bir <xref:System.Data.OleDb.OleDbDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="10d3f-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="10d3f-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="10d3f-128">Odbc</span></span>
<span data-ttu-id="10d3f-129">Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabileceğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="10d3f-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="10d3f-130">Kod, Ürünler <xref:System.Data.Odbc.OdbcCommand> tablosundan satırları seçmek için bir <xref:System.Data.Odbc.OdbcParameter> satır oluşturur ve bu durumda 5,, bir birim fiyatı belirtilen parametre değerinden daha büyük olan satırlarla sonuçları sınırlamak için a ekler.</span><span class="sxs-lookup"><span data-stu-id="10d3f-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="10d3f-131">Kod <xref:System.Data.Odbc.OdbcConnection> çıktığında kaynakların `using` kapatılmasını ve imha edilmesini sağlayan bir blok içinde açılır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="10d3f-132">Kod, bir <xref:System.Data.Odbc.OdbcDataReader>kullanarak komutu yürütür ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="10d3f-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)]
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)]

### <a name="oracleclient"></a><span data-ttu-id="10d3f-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="10d3f-133">OracleClient</span></span>
<span data-ttu-id="10d3f-134">Bu örnekteki kod DEMO'ya bir bağlantı varsayar. Oracle sunucusunda MÜŞTERİ.</span><span class="sxs-lookup"><span data-stu-id="10d3f-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="10d3f-135">System.Data.OracleClient.dll adresine de bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="10d3f-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="10d3f-136">Kod, verileri bir <xref:System.Data.OracleClient.OracleDataReader>' de döndürür.</span><span class="sxs-lookup"><span data-stu-id="10d3f-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="10d3f-137">Varlık Çerçevesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="10d3f-137">Entity Framework examples</span></span>
<span data-ttu-id="10d3f-138">Aşağıdaki kod listeleri, Varlık Veri Modeli'ndeki (EDM) varlıkları sorgulayarak veri kaynağından nasıl veri alınarak alınabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="10d3f-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="10d3f-139">Bu örnekler, Northwind örnek veritabanını temel alan bir model kullanır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-139">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="10d3f-140">Varlık Çerçevesi hakkında daha fazla bilgi için Entity [Framework Genel Bakış'a](./ef/overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="10d3f-140">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="10d3f-141">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="10d3f-141">LINQ to Entities</span></span>
<span data-ttu-id="10d3f-142">Bu örnekteki kod, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak yansıtılan kategoriler nesneleri olarak verileri döndürmek için bir LINQ sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="10d3f-143">Daha fazla bilgi için [LINQ to Varlıklara Genel Bakış'a](./ef/language-reference/linq-to-entities.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="10d3f-143">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

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

### <a name="typed-objectquery"></a><span data-ttu-id="10d3f-144">Yazılan ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="10d3f-144">Typed ObjectQuery</span></span>
<span data-ttu-id="10d3f-145">Bu örnekteki kod, <xref:System.Data.Objects.ObjectQuery%601> kategoriler nesneleri olarak veri döndürmek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="10d3f-146">Daha fazla bilgi için [Nesne Sorguları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100))bakın.</span><span class="sxs-lookup"><span data-stu-id="10d3f-146">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

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

### <a name="entityclient"></a><span data-ttu-id="10d3f-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="10d3f-147">EntityClient</span></span>
<span data-ttu-id="10d3f-148">Bu örnekteki kod, <xref:System.Data.EntityClient.EntityCommand> Bir Varlık SQL sorgusu yürütmek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="10d3f-149">Bu sorgu, Kategoriler varlık türü örneklerini temsil eden kayıtların listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="10d3f-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="10d3f-150">Sonuç <xref:System.Data.EntityClient.EntityDataReader> kümesindeki veri kayıtlarına erişmek için bir kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="10d3f-151">Daha fazla bilgi için Entity [Framework için EntityClient Sağlayıcısı'na](./ef/entityclient-provider-for-the-entity-framework.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="10d3f-151">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

## <a name="linq-to-sql"></a><span data-ttu-id="10d3f-152">LINQ - SQL</span><span class="sxs-lookup"><span data-stu-id="10d3f-152">LINQ to SQL</span></span>
<span data-ttu-id="10d3f-153">Bu örnekteki kod, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak yansıtılan kategoriler nesneleri olarak verileri döndürmek için bir LINQ sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="10d3f-154">Bu örnek, Northwind veri bağlamını temel adamaktadır.</span><span class="sxs-lookup"><span data-stu-id="10d3f-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="10d3f-155">Daha fazla bilgi için [bkz.](./sql/linq/getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="10d3f-155">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="10d3f-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10d3f-156">See also</span></span>

- [<span data-ttu-id="10d3f-157">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="10d3f-157">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="10d3f-158">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="10d3f-158">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="10d3f-159">[Veri Uygulamaları Oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="10d3f-159">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="10d3f-160">[Varlık Veri Modelini Sorgulama (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="10d3f-160">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="10d3f-161">[Nasıl yapilir: Anonim Tür Nesnelerini Döndüren Bir Sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10d3f-161">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
