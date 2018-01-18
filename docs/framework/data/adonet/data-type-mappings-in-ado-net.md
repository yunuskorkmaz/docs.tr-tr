---
title: "ADO.NET veri türü eşlemeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45061ed18d5854092db4a8d90bc18d48e2e6e6db
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="cff44-102">ADO.NET veri türü eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="cff44-102">Data Type Mappings in ADO.NET</span></span>
<span data-ttu-id="cff44-103">.NET Framework nasıl türleri bildirilen kullanılan ve çalışma zamanı'nda yönetilen tanımlar ortak tür sistemi dayanır.</span><span class="sxs-lookup"><span data-stu-id="cff44-103">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="cff44-104">Değer türleri ve türetilen tüm hangi başvuru türleri oluşur <xref:System.Object> temel türü.</span><span class="sxs-lookup"><span data-stu-id="cff44-104">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="cff44-105">Açıkça belirtilmezse, bir veri kaynağı ile çalışırken, veri türü veri sağlayıcısı'ndan algılanır.</span><span class="sxs-lookup"><span data-stu-id="cff44-105">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="cff44-106">Örneğin, bir <xref:System.Data.DataSet> nesnesidir herhangi belirli veri kaynağından bağımsız.</span><span class="sxs-lookup"><span data-stu-id="cff44-106">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="cff44-107">Verileri bir `DataSet` bir veri kaynağından alınan ve değişiklikleri kullanarak veri kaynağına geri kaldı bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="cff44-107">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="cff44-108">Yani bir `DataAdapter` doldurur bir <xref:System.Data.DataTable> içinde bir `DataSet` sütunları sonuç veri türleri bir veri kaynağından alınan değerlerle `DataTable` olan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri için belirli yerine türleri [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri veri kaynağına bağlanmak için kullanılan sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="cff44-108">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, instead of types specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="cff44-109">Benzer şekilde, bir `DataReader` bir veri kaynağı, sonuçlanan değer arasında bir değer olan yerel bir değişkende depolanan döndürür bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türü.</span><span class="sxs-lookup"><span data-stu-id="cff44-109">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type.</span></span> <span data-ttu-id="cff44-110">Her ikisi için de `Fill` işlemlerini `DataAdapter` ve `Get` yöntemlerinin `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] döndürülen değerin türü olayla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="cff44-110">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the value returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
 <span data-ttu-id="cff44-111">Çıkarsanan veri türüne bağlı olan yerine yazılan erişimci yöntemlerini kullanabilirsiniz `DataReader` belirli türde bir döndürülen değer bildiğinizde.</span><span class="sxs-lookup"><span data-stu-id="cff44-111">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="cff44-112">Yazılı erişimci yöntemleri size daha iyi performans belirli bir olarak bir değer döndürerek [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ek tür dönüştürme ihtiyacını ortadan kaldıran türü.</span><span class="sxs-lookup"><span data-stu-id="cff44-112">Typed accessor methods give you better performance by returning a value as a specific [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cff44-113">Null değerler için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcı veri türlerini temsil ettiği `DBNull.Value`.</span><span class="sxs-lookup"><span data-stu-id="cff44-113">Null values for [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cff44-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cff44-114">In This Section</span></span>  
 [<span data-ttu-id="cff44-115">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="cff44-115">SQL Server Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 <span data-ttu-id="cff44-116">Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="cff44-116">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="cff44-117">OLE DB Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="cff44-117">OLE DB Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 <span data-ttu-id="cff44-118">Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="cff44-118">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="cff44-119">ODBC Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="cff44-119">ODBC Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 <span data-ttu-id="cff44-120">Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.Odbc>.</span><span class="sxs-lookup"><span data-stu-id="cff44-120">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="cff44-121">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="cff44-121">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="cff44-122">Veri türü eşlemeleri ve veri erişimci yöntemlerini listeler çıkarımı yapılan <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="cff44-122">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="cff44-123">Kayan Noktalı Sayılar</span><span class="sxs-lookup"><span data-stu-id="cff44-123">Floating-Point Numbers</span></span>](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 <span data-ttu-id="cff44-124">Geliştiriciler kayan nokta sayıları ile çalışırken sık karşılaştığınız sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="cff44-124">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff44-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cff44-125">See Also</span></span>  
 [<span data-ttu-id="cff44-126">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cff44-126">SQL Server Data Types and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="cff44-127">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cff44-127">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="cff44-128">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="cff44-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="cff44-129">Ortak Tür Sistemi</span><span class="sxs-lookup"><span data-stu-id="cff44-129">Common Type System</span></span>](../../../../docs/standard/base-types/common-type-system.md)  
 [<span data-ttu-id="cff44-130">Türleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cff44-130">Converting Types</span></span>](http://msdn.microsoft.com/en-us/6038316e-bdaf-4f55-8006-407f591ce156)  
 [<span data-ttu-id="cff44-131">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="cff44-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
