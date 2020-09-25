---
title: Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 52e64714a17448cd94723bdc216d8ea069fc5eef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177754"
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="0eaf9-102">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="0eaf9-102">Data Type Mappings in ADO.NET</span></span>

<span data-ttu-id="0eaf9-103">.NET Framework, çalışma zamanında türlerin nasıl bildirildiği, kullanıldığı ve yönetildiğini tanımlayan ortak tür sistemine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-103">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="0eaf9-104">Her ikisi de temel türden türetilen değer türleri ve başvuru türlerinden oluşur <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="0eaf9-104">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="0eaf9-105">Bir veri kaynağıyla çalışırken, açıkça belirtilmemişse veri türü veri sağlayıcısından algılanır.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-105">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="0eaf9-106">Örneğin, bir <xref:System.Data.DataSet> nesne belirli bir veri kaynağından bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-106">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="0eaf9-107">İçindeki veriler bir `DataSet` veri kaynağından alınır ve değişiklikler bir kullanılarak veri kaynağına geri kaydedilir `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="0eaf9-107">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="0eaf9-108">Yani `DataAdapter` <xref:System.Data.DataTable> , bir `DataSet` veri kaynağından değerleri olan bir ile bir doldurduğunda, içindeki sütunların sonuç veri türleri, `DataTable` veri kaynağına bağlanmak için kullanılan .NET Framework veri sağlayıcısına özgü türler yerine .NET Framework türlerdir.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-108">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are .NET Framework types, instead of types specific to the .NET Framework data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="0eaf9-109">Benzer şekilde, bir `DataReader` veri kaynağından bir değer döndürdüğünde, sonuçta elde edilen değer .NET Framework türüne sahip yerel bir değişkende depolanır.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-109">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a .NET Framework type.</span></span> <span data-ttu-id="0eaf9-110">Ve yöntemlerinin her ikisi için `Fill` `DataAdapter` `Get` `DataReader` , .NET Framework türü .NET Framework veri sağlayıcısından döndürülen değerden çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-110">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the value returned from the .NET Framework data provider.</span></span>  
  
 <span data-ttu-id="0eaf9-111">Gösterilen veri türüne güvenmek yerine, `DataReader` döndürülmekte olan değerin belirli bir türünü bildiğiniz zaman türü belirlenmiş erişimci yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-111">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="0eaf9-112">Türü belirlenmiş erişimci yöntemleri, bir değeri belirli bir .NET Framework türüne döndürerek daha iyi performans sağlar ve bu da ek tür dönüştürme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-112">Typed accessor methods give you better performance by returning a value as a specific .NET Framework type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0eaf9-113">.NET Framework veri sağlayıcısı veri türleri için null değerler tarafından temsil edilir `DBNull.Value` .</span><span class="sxs-lookup"><span data-stu-id="0eaf9-113">Null values for .NET Framework data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0eaf9-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0eaf9-114">In This Section</span></span>  

 [<span data-ttu-id="0eaf9-115">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="0eaf9-115">SQL Server Data Type Mappings</span></span>](sql-server-data-type-mappings.md)  
 <span data-ttu-id="0eaf9-116">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.SqlClient> .</span><span class="sxs-lookup"><span data-stu-id="0eaf9-116">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="0eaf9-117">OLE DB Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="0eaf9-117">OLE DB Data Type Mappings</span></span>](ole-db-data-type-mappings.md)  
 <span data-ttu-id="0eaf9-118">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.OleDb> .</span><span class="sxs-lookup"><span data-stu-id="0eaf9-118">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="0eaf9-119">ODBC Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="0eaf9-119">ODBC Data Type Mappings</span></span>](odbc-data-type-mappings.md)  
 <span data-ttu-id="0eaf9-120">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.Odbc> .</span><span class="sxs-lookup"><span data-stu-id="0eaf9-120">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="0eaf9-121">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="0eaf9-121">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="0eaf9-122">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.OracleClient> .</span><span class="sxs-lookup"><span data-stu-id="0eaf9-122">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="0eaf9-123">Kayan Noktalı Sayılar</span><span class="sxs-lookup"><span data-stu-id="0eaf9-123">Floating-Point Numbers</span></span>](floating-point-numbers.md)  
 <span data-ttu-id="0eaf9-124">Kayan nokta numaralarıyla çalışırken geliştiricilerin sıkça karşılaştığı sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-124">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eaf9-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0eaf9-125">See also</span></span>

- [<span data-ttu-id="0eaf9-126">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0eaf9-126">SQL Server Data Types and ADO.NET</span></span>](./sql/sql-server-data-types.md)
- [<span data-ttu-id="0eaf9-127">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0eaf9-127">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="0eaf9-128">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="0eaf9-128">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="0eaf9-129">Ortak tür sistemi</span><span class="sxs-lookup"><span data-stu-id="0eaf9-129">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)
- <span data-ttu-id="0eaf9-130">[Türleri dönüştürme](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0eaf9-130">[Converting Types](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span></span>
- [<span data-ttu-id="0eaf9-131">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0eaf9-131">ADO.NET Overview</span></span>](ado-net-overview.md)
