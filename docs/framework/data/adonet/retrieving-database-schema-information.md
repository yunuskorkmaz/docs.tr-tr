---
title: Veritabanı şema bilgilerini alma
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 8a076ca792ee1b4b2194b778c51fefbd0bb19bd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494034"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="7307a-102">Veritabanı şema bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="7307a-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="7307a-103">Veritabanı şema bilgilerini alma şema bulma işlemi ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7307a-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="7307a-104">Şema bulma sağlayan yönetilen sağlayıcıları bulun ve veritabanı şeması hakkında bilgi döndürür olarak da bilinen istemek uygulamaları *meta verileri*, belirli bir veritabanı.</span><span class="sxs-lookup"><span data-stu-id="7307a-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="7307a-105">Tablolar, sütunlar ve saklı yordamlar gibi farklı veritabanı şeması öğeleri şema koleksiyonları sunulur.</span><span class="sxs-lookup"><span data-stu-id="7307a-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="7307a-106">Şema bilgileri kullanılan sağlayıcıya özgü çeşitli her şema koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="7307a-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="7307a-107">Her .NET Framework yönetilen sağlayıcıları uygulama **GetSchema** yönteminde **bağlantı** sınıfı ve öğesinden döndürülen şema bilgileri **GetSchema**yöntemi gelen biçiminde bir <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="7307a-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="7307a-108">**GetSchema** döndürmek için şema koleksiyonu belirtme ve döndürülen bilgi tutarını sınırlamak için isteğe bağlı parametreler sağlayan aşırı yüklenmiş yöntem yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="7307a-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="7307a-109">.NET Framework veri sağlayıcıları için OLE DB, ODBC, Oracle ve SqlClient sağlayan bir **GetSchemaTable** sütun meta verileri tanımlayan bir DataTable döndüren yöntem **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="7307a-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="7307a-110">Ayrıca OLE DB için .NET Framework veri sağlayıcısı kullanarak şema bilgileri sunan <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> yöntemi <xref:System.Data.OleDb.OleDbConnection> nesne.</span><span class="sxs-lookup"><span data-stu-id="7307a-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="7307a-111">Bağımsız değişken **GetOleDbSchemaTable** götüren bir <xref:System.Data.OleDb.OleDbSchemaGuid> döndürmek için şema bilgileri tanımlayan ve bu kısıtlamaları bir dizi sütun döndürdü.</span><span class="sxs-lookup"><span data-stu-id="7307a-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="7307a-112">**GetOleDbSchemaTable** döndürür bir <xref:System.Data.DataTable> istenen şemanın bilgilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="7307a-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7307a-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7307a-113">In This Section</span></span>  
 [<span data-ttu-id="7307a-114">GetSchema ve Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="7307a-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="7307a-115">Açıklar **GetSchema** yöntemi ve nasıl, almak ve şema bilgilerini veritabanından kısıtlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7307a-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="7307a-116">Şema kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="7307a-116">Schema Restrictions</span></span>  
 <span data-ttu-id="7307a-117">İle kullanılan şema kısıtlamaları açıklamaktadır **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="7307a-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="7307a-118">Ortak Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="7307a-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="7307a-119">Tüm tüm .NET Framework yönetilen sağlayıcı tarafından desteklenen ortak şema koleksiyonları açıklar.</span><span class="sxs-lookup"><span data-stu-id="7307a-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="7307a-120">SQL Server Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="7307a-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="7307a-121">SQL Server için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonu açıklar.</span><span class="sxs-lookup"><span data-stu-id="7307a-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="7307a-122">Oracle Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="7307a-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="7307a-123">Oracle için .NET Framework sağlayıcısı tarafından desteklenen şema koleksiyonu açıklar.</span><span class="sxs-lookup"><span data-stu-id="7307a-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="7307a-124">ODBC Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="7307a-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="7307a-125">ODBC sürücüleri için şema koleksiyonları açıklar.</span><span class="sxs-lookup"><span data-stu-id="7307a-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="7307a-126">OLE DB Şema Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="7307a-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="7307a-127">OLE DB sağlayıcısı için şema koleksiyonları açıklar.</span><span class="sxs-lookup"><span data-stu-id="7307a-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7307a-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7307a-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="7307a-129">Açıklar **GetSchema** yöntemi <xref:System.Data.Common.DbConnection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="7307a-130">Açıklar **GetSchema** yöntemi <xref:System.Data.Odbc.OdbcConnection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="7307a-131">Açıklar **GetSchema** yöntemi <xref:System.Data.OleDb.OleDbConnection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="7307a-132">Açıklar **GetSchema** yöntemi <xref:System.Data.OracleClient.OracleConnection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="7307a-133">Açıklar **GetSchema** yöntemi <xref:System.Data.SqlClient.SqlConnection> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="7307a-134">Açıklar **GetSchemaTable** yöntemi <xref:System.Data.Common.DbDataReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="7307a-135">Açıklar **GetSchemaTable** yöntemi <xref:System.Data.Odbc.OdbcDataReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="7307a-136">Açıklar **GetSchemaTable** yöntemi <xref:System.Data.OleDb.OleDbDataReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="7307a-137">Açıklar **GetSchemaTable** yöntemi <xref:System.Data.OracleClient.OracleDataReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="7307a-138">Açıklar **GetSchemaTable** yöntemi <xref:System.Data.SqlClient.SqlDataReader> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7307a-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7307a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7307a-139">See also</span></span>
- [<span data-ttu-id="7307a-140">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7307a-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="7307a-141">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="7307a-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
