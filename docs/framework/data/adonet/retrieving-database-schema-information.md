---
title: Veritabanı Şema Bilgilerini Alma
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782731"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="377a6-102">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="377a6-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="377a6-103">Şema bulma işlemi ile bir veritabanından şema bilgileri alma işlemi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="377a6-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="377a6-104">Şema bulma, uygulamaların belirli bir veritabanının *meta verileri*olarak da bilinen veritabanı şeması hakkındaki bilgileri bulmasını ve döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="377a6-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="377a6-105">Tablolar, sütunlar ve saklı yordamlar gibi farklı veritabanı şeması öğeleri, şema koleksiyonları aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="377a6-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="377a6-106">Her şema koleksiyonu, kullanılmakta olan sağlayıcıya özgü çeşitli şema bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="377a6-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="377a6-107">.NET Framework yönetilen sağlayıcıların her biri, **bağlantı** sınıfında **GetSchema** yöntemini uygular ve **GetSchema** yönteminden döndürülen şema bilgileri bir <xref:System.Data.DataTable>biçiminde gelir.</span><span class="sxs-lookup"><span data-stu-id="377a6-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="377a6-108">**GetSchema** yöntemi, döndürülecek şema koleksiyonunu belirtmek ve döndürülen bilgi miktarını kısıtlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="377a6-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="377a6-109">OLE DB, ODBC, Oracle ve SqlClient .NET Framework veri sağlayıcıları, **DataReader**'ın sütun meta verilerini açıklayan bir DataTable döndüren **GetSchemaTable** yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="377a6-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="377a6-110">OLE DB için .NET Framework veri sağlayıcısı, <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> <xref:System.Data.OleDb.OleDbConnection> nesne yöntemini kullanarak şema bilgilerini de kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="377a6-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="377a6-111">Bağımsız değişkenler olarak, **GetOleDbSchemaTable** , <xref:System.Data.OleDb.OleDbSchemaGuid> Döndürülecek şema bilgilerini ve döndürülen sütunlara yönelik bir dizi kısıtlamayı belirleyen bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="377a6-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="377a6-112">**GetOleDbSchemaTable** , istenen <xref:System.Data.DataTable> şema bilgileriyle doldurulmuş bir değer döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="377a6-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="377a6-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="377a6-113">In This Section</span></span>  
 [<span data-ttu-id="377a6-114">GetSchema ve Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="377a6-114">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="377a6-115">**GetSchema** yöntemini ve bir veritabanından şema bilgilerini almak ve kısıtlamak için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="377a6-116">Şema Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="377a6-116">Schema Restrictions</span></span>  
 <span data-ttu-id="377a6-117">**GetSchema**ile kullanılabilen şema kısıtlamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="377a6-118">Ortak Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="377a6-118">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="377a6-119">Tüm .NET Framework yönetilen sağlayıcılar tarafından desteklenen tüm ortak şema koleksiyonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="377a6-120">SQL Server Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="377a6-120">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="377a6-121">SQL Server için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="377a6-122">Oracle Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="377a6-122">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="377a6-123">Oracle için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="377a6-124">ODBC Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="377a6-124">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="377a6-125">ODBC sürücüleri için şema koleksiyonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="377a6-126">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="377a6-126">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="377a6-127">OLE DB sağlayıcıları için şema koleksiyonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="377a6-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="377a6-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="377a6-129"><xref:System.Data.Common.DbConnection> Sınıfının **GetSchema** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="377a6-130"><xref:System.Data.Odbc.OdbcConnection> Sınıfının **GetSchema** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="377a6-131"><xref:System.Data.OleDb.OleDbConnection> Sınıfının **GetSchema** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="377a6-132"><xref:System.Data.OracleClient.OracleConnection> Sınıfının **GetSchema** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="377a6-133"><xref:System.Data.SqlClient.SqlConnection> Sınıfının **GetSchema** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="377a6-134"><xref:System.Data.Common.DbDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="377a6-135"><xref:System.Data.Odbc.OdbcDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="377a6-136"><xref:System.Data.OleDb.OleDbDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="377a6-137"><xref:System.Data.OracleClient.OracleDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="377a6-138"><xref:System.Data.SqlClient.SqlDataReader> Sınıfının **GetSchemaTable** metodunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="377a6-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377a6-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="377a6-139">See also</span></span>

- [<span data-ttu-id="377a6-140">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="377a6-140">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="377a6-141">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="377a6-141">ADO.NET Overview</span></span>](ado-net-overview.md)
