---
title: "ADO.NET kod örnekleri"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-ado
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 61de1bf5f3e5eb16718f2af7fa29325dc94770d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-code-examples"></a><span data-ttu-id="d1951-102">ADO.NET kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="d1951-102">ADO.NET code examples</span></span>
<span data-ttu-id="d1951-103">Bu konudaki kod listeleri aşağıdaki ADO.NET teknolojilerini kullanarak bir veritabanından veri almak nasıl ekleyebileceğiniz gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d1951-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="d1951-104">ADO.NET veri sağlayıcıları:</span><span class="sxs-lookup"><span data-stu-id="d1951-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="d1951-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="d1951-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="d1951-106">[OleDb](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="d1951-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="d1951-107">[ODBC](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="d1951-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="d1951-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="d1951-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="d1951-109">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="d1951-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="d1951-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d1951-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="d1951-111">Yazılı ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="d1951-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="d1951-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="d1951-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="d1951-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d1951-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="d1951-114">ADO.NET veri sağlayıcısı örnekleri</span><span class="sxs-lookup"><span data-stu-id="d1951-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="d1951-115">Aşağıdaki kod listeleri ADO.NET data Provider kullanarak bir veritabanından veri almak nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1951-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="d1951-116">İçinde döndürülen veriler bir `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="d1951-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="d1951-117">Daha fazla bilgi için bkz: [alma verileri kullanarak bir DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="d1951-117">For more information, see [Retrieving Data Using a DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="d1951-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="d1951-118">SqlClient</span></span>
<span data-ttu-id="d1951-119">Bu örnekteki kod için bağlanabildiğinizi varsayar `Northwind` Microsoft örnek veritabanı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1951-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d1951-120">Kod oluşturur bir <xref:System.Data.SqlClient.SqlCommand> Ürünler tablosundan satırları seçmek için ekleme bir <xref:System.Data.SqlClient.SqlParameter> belirtilen parametre, bu durumda 5 değerinden bir UnitPrice satırlarla sonuçları sınırlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="d1951-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="d1951-121"><xref:System.Data.SqlClient.SqlConnection> İçinde açılmış bir `using` kaynakları kapalı ve kod çıktığında atıldı sağlar bloğu.</span><span class="sxs-lookup"><span data-stu-id="d1951-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="d1951-122">Kod kullanarak komutu yürütür bir <xref:System.Data.SqlClient.SqlDataReader>ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d1951-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="d1951-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="d1951-123">OleDb</span></span>
<span data-ttu-id="d1951-124">Bu örnekteki kod için Microsoft Access Northwind örnek veritabanı bağlanabildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="d1951-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="d1951-125">Kod oluşturur bir <xref:System.Data.OleDb.OleDbCommand> Ürünler tablosundan satırları seçmek için ekleme bir <xref:System.Data.OleDb.OleDbParameter> belirtilen parametre, bu durumda 5 değerinden bir UnitPrice satırlarla sonuçları sınırlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="d1951-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="d1951-126"><xref:System.Data.OleDb.OleDbConnection> İçinde açılmış bir `using` kaynakları kapalı ve kod çıktığında atıldı sağlar bloğu.</span><span class="sxs-lookup"><span data-stu-id="d1951-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="d1951-127">Kod kullanarak komutu yürütür bir <xref:System.Data.OleDb.OleDbDataReader>ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d1951-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="d1951-128">ODBC</span><span class="sxs-lookup"><span data-stu-id="d1951-128">Odbc</span></span>
<span data-ttu-id="d1951-129">Bu örnekteki kod için Microsoft Access Northwind örnek veritabanı bağlanabildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="d1951-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="d1951-130">Kod oluşturur bir <xref:System.Data.Odbc.OdbcCommand> Ürünler tablosundan satırları seçmek için ekleme bir <xref:System.Data.Odbc.OdbcParameter> belirtilen parametre, bu durumda 5 değerinden bir UnitPrice satırlarla sonuçları sınırlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="d1951-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="d1951-131"><xref:System.Data.Odbc.OdbcConnection> İçinde açılmış bir `using` kaynakları kapalı ve kod çıktığında atıldı sağlar bloğu.</span><span class="sxs-lookup"><span data-stu-id="d1951-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="d1951-132">Kod kullanarak komutu yürütür bir <xref:System.Data.Odbc.OdbcDataReader>ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d1951-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="d1951-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="d1951-133">OracleClient</span></span>
<span data-ttu-id="d1951-134">Bu örnekteki kod DEMO bağlantı varsayar. Bir Oracle Sunucusu müşteri.</span><span class="sxs-lookup"><span data-stu-id="d1951-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="d1951-135">Ayrıca System.Data.OracleClient.dll bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1951-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="d1951-136">Veri kodu döndürür bir <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d1951-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="d1951-137">Entity Framework örnekleri</span><span class="sxs-lookup"><span data-stu-id="d1951-137">Entity Framework examples</span></span>
<span data-ttu-id="d1951-138">Aşağıdaki kod listeleri varlıklar bir varlık veri modeli (EDM) sorgulayarak bir veri kaynağından veri almak nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1951-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="d1951-139">Bu örneklerde [Northwind modeli](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span><span class="sxs-lookup"><span data-stu-id="d1951-139">These examples use the [Northwind model](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span></span> <span data-ttu-id="d1951-140">Daha fazla bilgi için bkz: [Entity Framework genel bakış](../../../../docs/framework/data/adonet/ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="d1951-140">For more information, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="d1951-141">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="d1951-141">LINQ to Entities</span></span>
<span data-ttu-id="d1951-142">Bu örnekteki kod LINQ sorgusu yalnızca adlı kullanıcı, Categoryıd'si ve CategoryName özellikleri içeren bir anonim tür olarak öngörülen kategorileri nesneler olarak verileri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1951-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="d1951-143">Daha fazla bilgi için bkz: [LINQ to Entities genel bakış](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span><span class="sxs-lookup"><span data-stu-id="d1951-143">For more information, see [LINQ to Entities Overview](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span></span>

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

### <a name="typed-objectquery"></a><span data-ttu-id="d1951-144">Yazılı ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="d1951-144">Typed ObjectQuery</span></span>
<span data-ttu-id="d1951-145">Bu örnekteki kod kullanan bir <xref:System.Data.Objects.ObjectQuery%601> kategorileri nesneler olarak verileri döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="d1951-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="d1951-146">Daha fazla bilgi için bkz: [nesne sorguları](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span><span class="sxs-lookup"><span data-stu-id="d1951-146">For more information, see [Object Queries](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span></span>

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

### <a name="entityclient"></a><span data-ttu-id="d1951-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="d1951-147">EntityClient</span></span>
<span data-ttu-id="d1951-148">Bu örnekteki kod kullanan bir <xref:System.Data.EntityClient.EntityCommand> bir varlık SQL sorgusu yürütülemedi.</span><span class="sxs-lookup"><span data-stu-id="d1951-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="d1951-149">Bu sorgu, kategoriler varlık türünün örneklerini temsil eden kayıt listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1951-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="d1951-150">Bir <xref:System.Data.EntityClient.EntityDataReader> veri kayıtlarını sonuç kümesinde erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1951-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="d1951-151">Daha fazla bilgi için bkz: [EntityClient sağlayıcısı için Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="d1951-151">For more information, see [EntityClient Provider for the Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

## <a name="linq-to-sql"></a><span data-ttu-id="d1951-152">LINQ - SQL</span><span class="sxs-lookup"><span data-stu-id="d1951-152">LINQ to SQL</span></span>
<span data-ttu-id="d1951-153">Bu örnekteki kod LINQ sorgusu yalnızca adlı kullanıcı, Categoryıd'si ve CategoryName özellikleri içeren bir anonim tür olarak öngörülen kategorileri nesneler olarak verileri döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1951-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="d1951-154">Bu örnek, Northwind veri bağlamda temel alır.</span><span class="sxs-lookup"><span data-stu-id="d1951-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="d1951-155">Daha fazla bilgi için bkz: [Başlarken](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="d1951-155">For more information, see [Getting Started](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d1951-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1951-156">See also</span></span>
 [<span data-ttu-id="d1951-157">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d1951-157">ADO.NET Overview</span></span>](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [<span data-ttu-id="d1951-158">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d1951-158">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="d1951-159">Veri uygulamaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1951-159">Creating Data Applications</span></span>](http://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [<span data-ttu-id="d1951-160">Bir varlık veri modeli (Entity Framework görevler) sorgulama</span><span class="sxs-lookup"><span data-stu-id="d1951-160">Querying an Entity Data Model (Entity Framework Tasks)</span></span>](http://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [<span data-ttu-id="d1951-161">Nasıl yapılır: Anonim türde nesne döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="d1951-161">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [<span data-ttu-id="d1951-162">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="d1951-162">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)  
