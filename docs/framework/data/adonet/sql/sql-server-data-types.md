---
title: SQL Server Veri Türleri ve ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: db4618ac624ea8401cab682a8c21d8f23c253d05
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155464"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="4d9b4-102">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4d9b4-102">SQL Server Data Types and ADO.NET</span></span>

<span data-ttu-id="4d9b4-103">SQL Server ve .NET Framework, farklı tür sistemlerine dayalıdır, bu da olası veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="4d9b4-104">Veri bütünlüğünü korumak için, SQL Server () için .NET Framework Veri Sağlayıcısı, <xref:System.Data.SqlClient> SQL Server verileriyle çalışmak üzere türsüz erişimci yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="4d9b4-105"><xref:System.Data.SqlDbType>Veri türlerini belirtmek için sınıflardaki numaralandırmalar kullanabilirsiniz <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="4d9b4-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="4d9b4-106">SQL Server ve .NET Framework veri türleri arasındaki veri türü eşlemelerini açıklayan bir tablo ve daha fazla bilgi için bkz. [SQL Server veri türü eşlemeleri](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="4d9b4-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="4d9b4-107">SQL Server 2008; tarih ve saat, yapılandırılmış, yarı yapılandırılmış ve yapılandırılmamış verilerle çalışması için iş ihtiyaçlarını karşılamak üzere tasarlanan yeni veri türlerini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="4d9b4-108">Bunlar SQL Server 2008 Books Online 'da belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="4d9b4-109">Uygulamanızda kullanıma sunulan SQL Server veri türleri, kullanmakta olduğunuz SQL Server sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="4d9b4-110">Daha fazla bilgi için aşağıdaki tabloda SQL Server Books Online 'ın ilgili sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="4d9b4-111">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="4d9b4-111">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="4d9b4-112">Veri türleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="4d9b4-112">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a><span data-ttu-id="4d9b4-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4d9b4-113">In This Section</span></span>  

 [<span data-ttu-id="4d9b4-114">SqlTypes ve DataSet</span><span class="sxs-lookup"><span data-stu-id="4d9b4-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="4d9b4-115">İçinde için tür desteğini açıklar `SqlTypes` `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="4d9b4-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="4d9b4-116">Null Değerleri İşleme</span><span class="sxs-lookup"><span data-stu-id="4d9b4-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="4d9b4-117">Null değerlerle ve üç değerli mantığın nasıl çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="4d9b4-118">GUID ve uniqueidentifier Değerlerini Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="4d9b4-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="4d9b4-119">SQL Server ve .NET Framework GUID ve uniqueidentifier değerleriyle nasıl çalışabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="4d9b4-120">Tarih ve Saat Verileri</span><span class="sxs-lookup"><span data-stu-id="4d9b4-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="4d9b4-121">SQL Server 2008 ' de tanıtılan yeni tarih ve saat veri türlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="4d9b4-122">Büyük UDT’ler</span><span class="sxs-lookup"><span data-stu-id="4d9b4-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="4d9b4-123">SQL Server 2008 ' de tanıtılan büyük değerden verilerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="4d9b4-124">SQL Server'da XML Verileri</span><span class="sxs-lookup"><span data-stu-id="4d9b4-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="4d9b4-125">SQL Server alınan XML verileriyle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4d9b4-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="4d9b4-126">Reference</span></span>  

 <xref:System.Data.DataSet>  
 <span data-ttu-id="4d9b4-127">`DataSet`Sınıfını ve tüm üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="4d9b4-128">`SqlTypes`Ad alanını ve tüm üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="4d9b4-129">Listelemeyi `SqlDbType` ve tüm üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="4d9b4-130">Listelemeyi `DbType` ve tüm üyelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d9b4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-131">See also</span></span>

- [<span data-ttu-id="4d9b4-132">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="4d9b4-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="4d9b4-133">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4d9b4-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="4d9b4-134">Tablo Değerli Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d9b4-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="4d9b4-135">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="4d9b4-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="4d9b4-136">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4d9b4-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
