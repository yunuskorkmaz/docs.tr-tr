---
description: 'Hakkında daha fazla bilgi edinin: veritabanı şeması bilgileri alma'
title: Veritabanı Şema Bilgilerini Alma
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 84ac94a72b23d0b1d6924600f2fd33b2a285eab8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663410"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="3e6d3-103">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="3e6d3-103">Retrieving Database Schema Information</span></span>

<span data-ttu-id="3e6d3-104">Şema bulma işlemi ile bir veritabanından şema bilgileri alma işlemi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-104">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="3e6d3-105">Şema bulma, uygulamaların belirli bir veritabanının *meta verileri* olarak da bilinen veritabanı şeması hakkındaki bilgileri bulmasını ve döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-105">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="3e6d3-106">Tablolar, sütunlar ve saklı yordamlar gibi farklı veritabanı şeması öğeleri, şema koleksiyonları aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-106">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="3e6d3-107">Her şema koleksiyonu, kullanılmakta olan sağlayıcıya özgü çeşitli şema bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-107">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="3e6d3-108">.NET Framework yönetilen sağlayıcıların her biri, **bağlantı** sınıfında **GetSchema** yöntemini uygular ve **GetSchema** yönteminden döndürülen şema bilgileri bir biçiminde gelir <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-108">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="3e6d3-109">**GetSchema** yöntemi, döndürülecek şema koleksiyonunu belirtmek ve döndürülen bilgi miktarını kısıtlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-109">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="3e6d3-110">OLE DB, ODBC, Oracle ve SqlClient .NET Framework veri sağlayıcıları, **DataReader**'ın sütun meta verilerini açıklayan bir DataTable döndüren **GetSchemaTable** yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-110">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="3e6d3-111">OLE DB için .NET Framework Veri Sağlayıcısı, nesne yöntemini kullanarak şema bilgilerini de kullanıma sunar <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> <xref:System.Data.OleDb.OleDbConnection> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-111">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="3e6d3-112">Bağımsız değişkenler olarak, **GetOleDbSchemaTable** , <xref:System.Data.OleDb.OleDbSchemaGuid> Döndürülecek şema bilgilerini ve döndürülen sütunlara yönelik bir dizi kısıtlamayı belirleyen bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-112">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="3e6d3-113">**GetOleDbSchemaTable** <xref:System.Data.DataTable> , istenen şema bilgileriyle doldurulmuş bir değer döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-113">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e6d3-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3e6d3-114">In This Section</span></span>  

 [<span data-ttu-id="3e6d3-115">GetSchema ve Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3e6d3-115">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="3e6d3-116">**GetSchema** yöntemini ve bir veritabanından şema bilgilerini almak ve kısıtlamak için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-116">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="3e6d3-117">Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="3e6d3-117">Schema Restrictions</span></span>  
 <span data-ttu-id="3e6d3-118">**GetSchema** ile kullanılabilen şema kısıtlamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-118">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="3e6d3-119">Ortak Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3e6d3-119">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="3e6d3-120">Tüm .NET Framework yönetilen sağlayıcılar tarafından desteklenen tüm ortak şema koleksiyonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-120">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="3e6d3-121">SQL Server Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3e6d3-121">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="3e6d3-122">SQL Server için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-122">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="3e6d3-123">Oracle Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3e6d3-123">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="3e6d3-124">Oracle için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-124">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="3e6d3-125">ODBC Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3e6d3-125">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="3e6d3-126">ODBC sürücüleri için şema koleksiyonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-126">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="3e6d3-127">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="3e6d3-127">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="3e6d3-128">OLE DB sağlayıcıları için şema koleksiyonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-128">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3e6d3-129">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3e6d3-129">Reference</span></span>  

 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="3e6d3-130">Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.Common.DbConnection> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-130">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="3e6d3-131">Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.Odbc.OdbcConnection> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-131">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="3e6d3-132">Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.OleDb.OleDbConnection> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-132">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="3e6d3-133">Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.OracleClient.OracleConnection> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-133">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="3e6d3-134">Sınıfının **GetSchema** metodunu açıklar <xref:System.Data.SqlClient.SqlConnection> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-134">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="3e6d3-135">Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.Common.DbDataReader> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="3e6d3-136">Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.Odbc.OdbcDataReader> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-136">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="3e6d3-137">Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.OleDb.OleDbDataReader> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="3e6d3-138">Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-138">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="3e6d3-139">Sınıfının **GetSchemaTable** metodunu açıklar <xref:System.Data.SqlClient.SqlDataReader> .</span><span class="sxs-lookup"><span data-stu-id="3e6d3-139">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6d3-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e6d3-140">See also</span></span>

- [<span data-ttu-id="3e6d3-141">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3e6d3-141">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="3e6d3-142">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3e6d3-142">ADO.NET Overview</span></span>](ado-net-overview.md)
