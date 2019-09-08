---
title: ADO.NET kod örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 86d5fc63168330502f81dfa464fcd2c04f014760
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785067"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="2cd53-102">ADO.NET kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="2cd53-102">ADO.NET code examples</span></span>
<span data-ttu-id="2cd53-103">Bu konudaki kod listeleri, aşağıdaki ADO.NET teknolojilerini kullanarak bir veritabanından nasıl veri alınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2cd53-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="2cd53-104">ADO.NET veri sağlayıcıları:</span><span class="sxs-lookup"><span data-stu-id="2cd53-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="2cd53-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="2cd53-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="2cd53-106">[OLEDB](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="2cd53-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="2cd53-107">[Odbc](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="2cd53-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="2cd53-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="2cd53-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="2cd53-109">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="2cd53-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="2cd53-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="2cd53-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="2cd53-111">Tür ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="2cd53-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="2cd53-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="2cd53-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="2cd53-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2cd53-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="2cd53-114">ADO.NET veri sağlayıcısı örnekleri</span><span class="sxs-lookup"><span data-stu-id="2cd53-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="2cd53-115">Aşağıdaki kod listelerinde, ADO.NET veri sağlayıcıları kullanılarak bir veritabanından nasıl veri alacağınızı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2cd53-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="2cd53-116">Veriler bir `DataReader`içinde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2cd53-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="2cd53-117">Daha fazla bilgi için bkz. [DataReader kullanarak veri alma](retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="2cd53-117">For more information, see [Retrieving Data Using a DataReader](retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="2cd53-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="2cd53-118">SqlClient</span></span>
<span data-ttu-id="2cd53-119">Bu örnekteki kod, Microsoft SQL Server `Northwind` örnek veritabanına bağlanabildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="2cd53-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="2cd53-120">Kod, Ürünler tablosundan <xref:System.Data.SqlClient.SqlCommand> satırları seçmek için bir oluşturur ve bu durumda 5, <xref:System.Data.SqlClient.SqlParameter> belirtilen parametre değerinden daha büyük bir UnitPrice değeri olan satırları satırlara kısıtlamak için bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="2cd53-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="2cd53-121">, <xref:System.Data.SqlClient.SqlConnection> Bir`using` blok içinde açılır ve bu, kodun çıkış sırasında kaynakların kapatılmasını ve aktiften çıkarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd53-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="2cd53-122">Kod, komutunu kullanarak <xref:System.Data.SqlClient.SqlDataReader>komutu yürütür ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2cd53-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="2cd53-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="2cd53-123">OleDb</span></span>
<span data-ttu-id="2cd53-124">Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="2cd53-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="2cd53-125">Kod, Ürünler tablosundan <xref:System.Data.OleDb.OleDbCommand> satırları seçmek için bir oluşturur ve bu durumda 5, <xref:System.Data.OleDb.OleDbParameter> belirtilen parametre değerinden daha büyük bir UnitPrice değeri olan satırları satırlara kısıtlamak için bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="2cd53-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="2cd53-126">, <xref:System.Data.OleDb.OleDbConnection> Bir`using` bloğun içinde açılır ve bu, kodun çıkış sırasında kaynakların kapatılmasını ve aktiften çıkarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd53-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="2cd53-127">Kod, komutunu kullanarak <xref:System.Data.OleDb.OleDbDataReader>komutu yürütür ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2cd53-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="2cd53-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="2cd53-128">Odbc</span></span>
<span data-ttu-id="2cd53-129">Bu örnekteki kod, Microsoft Access Northwind örnek veritabanına bağlanabildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="2cd53-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="2cd53-130">Kod, Ürünler tablosundan <xref:System.Data.Odbc.OdbcCommand> satırları seçmek için bir oluşturur ve bu durumda 5, <xref:System.Data.Odbc.OdbcParameter> belirtilen parametre değerinden daha büyük bir UnitPrice değeri olan satırları satırlara kısıtlamak için bir değer ekler.</span><span class="sxs-lookup"><span data-stu-id="2cd53-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="2cd53-131">, <xref:System.Data.Odbc.OdbcConnection> Bir`using` blok içinde açılır ve bu, kodun çıkış sırasında kaynakların kapatılmasını ve aktiften çıkarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd53-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="2cd53-132">Kod, komutunu kullanarak <xref:System.Data.Odbc.OdbcDataReader>komutu yürütür ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2cd53-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="2cd53-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="2cd53-133">OracleClient</span></span>
<span data-ttu-id="2cd53-134">Bu örnekteki kod, TANıTıMA bir bağlantı olduğunu varsayar. Bir Oracle sunucusunda MÜŞTERI.</span><span class="sxs-lookup"><span data-stu-id="2cd53-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="2cd53-135">System. Data. OracleClient. dll ' ye de bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cd53-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="2cd53-136">Kod, içindeki <xref:System.Data.OracleClient.OracleDataReader>verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cd53-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="2cd53-137">Entity Framework örnekleri</span><span class="sxs-lookup"><span data-stu-id="2cd53-137">Entity Framework examples</span></span>
<span data-ttu-id="2cd53-138">Aşağıdaki kod listeleri bir Varlık Veri Modeli (EDM) içindeki varlıkları sorgulayarak bir veri kaynağından nasıl veri alınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2cd53-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="2cd53-139">Bu örnekler, Northwind örnek veritabanına dayalı bir model kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cd53-139">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="2cd53-140">Entity Framework hakkında daha fazla bilgi için bkz. [Entity Framework genel bakış](./ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="2cd53-140">For more information about Entity Framework, see [Entity Framework Overview](./ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="2cd53-141">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="2cd53-141">LINQ to Entities</span></span>
<span data-ttu-id="2cd53-142">Bu örnekteki kod, verileri kategori nesneleri olarak döndürmek için, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak tasarlanan bir LINQ sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cd53-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="2cd53-143">Daha fazla bilgi için bkz. [LINQ to Entities genel bakış](./ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="2cd53-143">For more information, see [LINQ to Entities Overview](./ef/language-reference/linq-to-entities.md).</span></span>

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

Imports System
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

### <a name="typed-objectquery"></a><span data-ttu-id="2cd53-144">Tür ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="2cd53-144">Typed ObjectQuery</span></span>
<span data-ttu-id="2cd53-145">Bu örnekteki kod, verileri kategori nesneleri <xref:System.Data.Objects.ObjectQuery%601> olarak döndürmek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cd53-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="2cd53-146">Daha fazla bilgi için bkz. [nesne sorguları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2cd53-146">For more information, see [Object Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896241(v=vs.100)).</span></span>

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

Imports System
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

### <a name="entityclient"></a><span data-ttu-id="2cd53-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="2cd53-147">EntityClient</span></span>
<span data-ttu-id="2cd53-148">Bu örnekteki kod, Entity SQL bir sorgu <xref:System.Data.EntityClient.EntityCommand> yürütmek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cd53-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="2cd53-149">Bu sorgu, kategori varlık türünün örneklerini temsil eden kayıtların bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cd53-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="2cd53-150"><xref:System.Data.EntityClient.EntityDataReader> Sonuç kümesindeki veri kayıtlarına erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2cd53-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="2cd53-151">Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](./ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="2cd53-151">For more information, see [EntityClient Provider for the Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

Imports System
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

## <a name="linq-to-sql"></a><span data-ttu-id="2cd53-152">LINQ - SQL</span><span class="sxs-lookup"><span data-stu-id="2cd53-152">LINQ to SQL</span></span>
<span data-ttu-id="2cd53-153">Bu örnekteki kod, verileri kategori nesneleri olarak döndürmek için, yalnızca CategoryID ve CategoryName özelliklerini içeren anonim bir tür olarak tasarlanan bir LINQ sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cd53-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="2cd53-154">Bu örnek, Northwind veri bağlamını temel alır.</span><span class="sxs-lookup"><span data-stu-id="2cd53-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="2cd53-155">Daha fazla bilgi için bkz [. Başlarken](./sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="2cd53-155">For more information, see [Getting Started](./sql/linq/getting-started.md).</span></span>

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

Imports System
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

## <a name="see-also"></a><span data-ttu-id="2cd53-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd53-156">See also</span></span>

- [<span data-ttu-id="2cd53-157">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2cd53-157">ADO.NET Overview</span></span>](ado-net-overview.md)
- [<span data-ttu-id="2cd53-158">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2cd53-158">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="2cd53-159">[Veri uygulamaları oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="2cd53-159">[Creating Data Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/h0y4a0f6(v=vs.120))</span></span>
- <span data-ttu-id="2cd53-160">[Varlık Veri Modeli sorgulama (Entity Framework görevler)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2cd53-160">[Querying an Entity Data Model (Entity Framework Tasks)](https://docs.microsoft.com/previous-versions/bb738455(v=vs.90))</span></span>
- <span data-ttu-id="2cd53-161">[Nasıl yapılır: Anonim tür nesneleri döndüren bir sorgu yürütme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2cd53-161">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>
