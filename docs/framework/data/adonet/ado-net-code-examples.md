---
title: ADO.NET kod örnekleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
ms.openlocfilehash: 8719ffc458297191514cfe65714d5b6dd862dd60
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143629"
---
# <a name="adonet-code-examples"></a><span data-ttu-id="82bfe-102">ADO.NET kod örnekleri</span><span class="sxs-lookup"><span data-stu-id="82bfe-102">ADO.NET code examples</span></span>
<span data-ttu-id="82bfe-103">Bu konudaki kod listeleri aşağıdaki ADO.NET teknolojileri kullanarak bir veritabanından veri almak nasıl ekleyebileceğiniz gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="82bfe-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="82bfe-104">ADO.NET veri sağlayıcıları:</span><span class="sxs-lookup"><span data-stu-id="82bfe-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="82bfe-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="82bfe-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="82bfe-106">[OleDb](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="82bfe-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="82bfe-107">[Odbc](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="82bfe-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="82bfe-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="82bfe-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="82bfe-109">ADO.NET varlık çerçevesi:</span><span class="sxs-lookup"><span data-stu-id="82bfe-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="82bfe-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="82bfe-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="82bfe-111">Türü belirlenmiş ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="82bfe-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="82bfe-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="82bfe-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="82bfe-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="82bfe-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="82bfe-114">ADO.NET veri sağlayıcı örneği</span><span class="sxs-lookup"><span data-stu-id="82bfe-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="82bfe-115">Aşağıdaki kod listeleri ADO.NET veri sağlayıcıları kullanarak bir veritabanından veri almak nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82bfe-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="82bfe-116">Veriler içerisinde geri dönmemiş ise bir `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="82bfe-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="82bfe-117">Daha fazla bilgi için [alma verileri kullanarak bir DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="82bfe-117">For more information, see [Retrieving Data Using a DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="82bfe-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="82bfe-118">SqlClient</span></span>
<span data-ttu-id="82bfe-119">Bu örnekteki kod için bağlanabildiğinizi varsayar `Northwind` örnek veritabanını Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="82bfe-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft SQL Server.</span></span> <span data-ttu-id="82bfe-120">Kod oluşturur bir <xref:System.Data.SqlClient.SqlCommand> Ürünler tablosundan satırları seçmek için ekleme bir <xref:System.Data.SqlClient.SqlParameter> sonuçları belirtilen parametre, bu durumda 5 değerinden bir UnitPrice satırları sınırlamak için.</span><span class="sxs-lookup"><span data-stu-id="82bfe-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="82bfe-121"><xref:System.Data.SqlClient.SqlConnection> İçinde açılan bir `using` bloğu, kaynakları kapalı ve kod çıktığında elden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bfe-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="82bfe-122">Kod kullanarak komutu yürütür. bir <xref:System.Data.SqlClient.SqlDataReader>ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82bfe-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="82bfe-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="82bfe-123">OleDb</span></span>
<span data-ttu-id="82bfe-124">Bu örnekteki kod Microsoft Access Northwind örnek veritabanına bağlanabildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="82bfe-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="82bfe-125">Kod oluşturur bir <xref:System.Data.OleDb.OleDbCommand> Ürünler tablosundan satırları seçmek için ekleme bir <xref:System.Data.OleDb.OleDbParameter> sonuçları belirtilen parametre, bu durumda 5 değerinden bir UnitPrice satırları sınırlamak için.</span><span class="sxs-lookup"><span data-stu-id="82bfe-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="82bfe-126"><xref:System.Data.OleDb.OleDbConnection> İçine açıldığında bir `using` bloğu, kaynakları kapalı ve kod çıktığında elden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bfe-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="82bfe-127">Kod kullanarak komutu yürütür. bir <xref:System.Data.OleDb.OleDbDataReader>ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82bfe-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="82bfe-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="82bfe-128">Odbc</span></span>
<span data-ttu-id="82bfe-129">Bu örnekteki kod Microsoft Access Northwind örnek veritabanına bağlanabildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="82bfe-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="82bfe-130">Kod oluşturur bir <xref:System.Data.Odbc.OdbcCommand> Ürünler tablosundan satırları seçmek için ekleme bir <xref:System.Data.Odbc.OdbcParameter> sonuçları belirtilen parametre, bu durumda 5 değerinden bir UnitPrice satırları sınırlamak için.</span><span class="sxs-lookup"><span data-stu-id="82bfe-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="82bfe-131"><xref:System.Data.Odbc.OdbcConnection> İçinde açılan bir `using` bloğu, kaynakları kapalı ve kod çıktığında elden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="82bfe-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="82bfe-132">Kod kullanarak komutu yürütür. bir <xref:System.Data.Odbc.OdbcDataReader>ve sonuçları konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="82bfe-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="82bfe-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="82bfe-133">OracleClient</span></span>
<span data-ttu-id="82bfe-134">Bu örnekteki kod tanıtım bağlantı varsayar. Bir Oracle sunucusunda müşteri.</span><span class="sxs-lookup"><span data-stu-id="82bfe-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="82bfe-135">Ayrıca, System.Data.OracleClient.dll bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82bfe-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="82bfe-136">Kod verileri döndürür bir <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="82bfe-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="82bfe-137">Entity Framework örnekleri</span><span class="sxs-lookup"><span data-stu-id="82bfe-137">Entity Framework examples</span></span>
<span data-ttu-id="82bfe-138">Aşağıdaki kod listeleri varlıkları bir varlık veri modeli (EDM) sorgulayarak bir veri kaynağından veri almak nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="82bfe-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="82bfe-139">Bu örnekler, Northwind örnek veritabanını temel alan bir model kullanır.</span><span class="sxs-lookup"><span data-stu-id="82bfe-139">These examples use a model based on the Northwind sample database.</span></span> <span data-ttu-id="82bfe-140">Entity Framework hakkında daha fazla bilgi için bkz: [Entity Framework'e Genel Bakış](../../../../docs/framework/data/adonet/ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="82bfe-140">For more information about Entity Framework, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="82bfe-141">LINQ - Varlıklar</span><span class="sxs-lookup"><span data-stu-id="82bfe-141">LINQ to Entities</span></span>
<span data-ttu-id="82bfe-142">Bu örnekteki kod, yalnızca kullanıcı, Categoryıd'si ve CategoryName özellikleri içeren bir anonim tür öngörülen kategorileri nesneleri olarak verileri döndürmek için LINQ sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="82bfe-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="82bfe-143">Daha fazla bilgi için [LINQ to Entities genel bakış](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="82bfe-143">For more information, see [LINQ to Entities Overview](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).</span></span>

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

### <a name="typed-objectquery"></a><span data-ttu-id="82bfe-144">Türü belirlenmiş ObjectQuery</span><span class="sxs-lookup"><span data-stu-id="82bfe-144">Typed ObjectQuery</span></span>
<span data-ttu-id="82bfe-145">Bu örnekteki kod bir <xref:System.Data.Objects.ObjectQuery%601> veri kategorileri nesneler olarak döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="82bfe-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="82bfe-146">Daha fazla bilgi için [nesne sorgularını](https://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span><span class="sxs-lookup"><span data-stu-id="82bfe-146">For more information, see [Object Queries](https://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span></span>

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

### <a name="entityclient"></a><span data-ttu-id="82bfe-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="82bfe-147">EntityClient</span></span>
<span data-ttu-id="82bfe-148">Bu örnekteki kod bir <xref:System.Data.EntityClient.EntityCommand> varlık SQL sorgusu yürütülemedi.</span><span class="sxs-lookup"><span data-stu-id="82bfe-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="82bfe-149">Bu sorgu kategorileri varlık türünün örneğini temsil eden kayıtlarını içeren bir liste döndürür.</span><span class="sxs-lookup"><span data-stu-id="82bfe-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="82bfe-150">Bir <xref:System.Data.EntityClient.EntityDataReader> sonuç kümesinde veri kayıtlarını erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82bfe-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="82bfe-151">Daha fazla bilgi için [Entity Framework için EntityClient sağlayıcısı](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="82bfe-151">For more information, see [EntityClient Provider for the Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>

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

## <a name="linq-to-sql"></a><span data-ttu-id="82bfe-152">LINQ - SQL</span><span class="sxs-lookup"><span data-stu-id="82bfe-152">LINQ to SQL</span></span>
<span data-ttu-id="82bfe-153">Bu örnekteki kod, yalnızca kullanıcı, Categoryıd'si ve CategoryName özellikleri içeren bir anonim tür öngörülen kategorileri nesneleri olarak verileri döndürmek için LINQ sorgusu kullanır.</span><span class="sxs-lookup"><span data-stu-id="82bfe-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="82bfe-154">Bu örnekte, Northwind veri bağlama temel alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="82bfe-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="82bfe-155">Daha fazla bilgi için [Başlarken](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="82bfe-155">For more information, see [Getting Started](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="82bfe-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82bfe-156">See also</span></span>
 [<span data-ttu-id="82bfe-157">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="82bfe-157">ADO.NET Overview</span></span>](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [<span data-ttu-id="82bfe-158">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="82bfe-158">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="82bfe-159">Veri uygulamaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="82bfe-159">Creating Data Applications</span></span>](https://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [<span data-ttu-id="82bfe-160">Bir varlık veri modeli (varlık çerçevesi görevler) sorgulama</span><span class="sxs-lookup"><span data-stu-id="82bfe-160">Querying an Entity Data Model (Entity Framework Tasks)</span></span>](https://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [<span data-ttu-id="82bfe-161">Nasıl Yapılır: Anonim türdeki nesneleri döndüren bir sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="82bfe-161">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 [<span data-ttu-id="82bfe-162">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="82bfe-162">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)  
