---
title: Oracle ve ADO.NET
description: Oracle Çağrı arabirimini kullanarak Oracle veritabanına erişim sağlayan Oracle için .NET Framework Veri Sağlayıcısı özellikleri ve davranışları hakkında bilgi edinin.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 736b8dc5179a15ec219c1dae06b9ee6b5d6c3ef3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166631"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="8e070-103">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8e070-103">Oracle and ADO.NET</span></span>

> [!NOTE]
> <span data-ttu-id="8e070-104">İçindeki türler <xref:System.Data.OracleClient> kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8e070-104">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="8e070-105">Türler geçerli sürüm of.NET çerçevesinde desteklenmeye devam eder, ancak gelecekteki bir sürümde kaldırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="8e070-105">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="8e070-106">Microsoft, üçüncü taraf bir Oracle sağlayıcısı kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="8e070-106">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="8e070-107">Bu bölümde, Oracle için .NET Framework Veri Sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e070-107">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="8e070-108">Oracle için .NET Framework Veri Sağlayıcısı Oracle Istemci yazılımı tarafından sağlanan Oracle Çağrı arabirimini (OCı) kullanarak bir Oracle veritabanına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e070-108">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="8e070-109">Veri sağlayıcısının işlevselliği, SQL Server, OLE DB ve ODBC için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8e070-109">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="8e070-110">Oracle için .NET Framework Veri Sağlayıcısı kullanmak için, bir uygulamanın <xref:System.Data.OracleClient> ad alanına aşağıdaki şekilde başvurması gerekir:</span><span class="sxs-lookup"><span data-stu-id="8e070-110">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="8e070-111">Kodunuzu derlerken DLL 'ye bir başvuru de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e070-111">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="8e070-112">Örneğin, bir C# programı derlerken komut satırlarınız şunları içermelidir:</span><span class="sxs-lookup"><span data-stu-id="8e070-112">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="8e070-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8e070-113">In This Section</span></span>  

 [<span data-ttu-id="8e070-114">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="8e070-114">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="8e070-115">Oracle için .NET Framework Veri Sağlayıcısı kullanma gereksinimlerini açıklar ve bunu kullanırken bilinmesi gereken birçok sorunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-115">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="8e070-116">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="8e070-116">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="8e070-117"><xref:System.Data.OracleClient.OracleBFile>Oracle BDOSYA veri türüyle çalışmak için kullanılan sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-117">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="8e070-118">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="8e070-118">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="8e070-119"><xref:System.Data.OracleClient.OracleLob>Oracle LOB veri türleriyle çalışmak için kullanılan sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-119">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="8e070-120">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="8e070-120">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="8e070-121">Oracle REF CURSOR veri türü için desteği açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-121">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="8e070-122">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="8e070-122">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="8e070-123">Ve dahil Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar <xref:System.Data.OracleClient.OracleNumber> <xref:System.Data.OracleClient.OracleString> .</span><span class="sxs-lookup"><span data-stu-id="8e070-123">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="8e070-124">Oracle Dizileri</span><span class="sxs-lookup"><span data-stu-id="8e070-124">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="8e070-125">Sunucu tarafından oluşturulan anahtar Oracle sıra değerlerini alma desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-125">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="8e070-126">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="8e070-126">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="8e070-127">Oracle veri türlerini ve bunların eşlemelerini listeler <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="8e070-127">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="8e070-128">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="8e070-128">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="8e070-129"><xref:System.Data.OracleClient.OracleConnection>Bir işlemin etkin olduğunu belirlerse, nesnenin var olan bir dağıtılmış işlemde otomatik olarak nasıl listeleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-129">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8e070-130">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8e070-130">Related Sections</span></span>  

 [<span data-ttu-id="8e070-131">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="8e070-131">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="8e070-132">ADO.NET kullanılırken güvenli kodlama uygulamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-132">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="8e070-133">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="8e070-133">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="8e070-134">' Nin nasıl oluşturulduğunu ve kullanılacağını açıklar, `DataSets` türü, `DataSets` `DataTables` ve `DataViews` .</span><span class="sxs-lookup"><span data-stu-id="8e070-134">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="8e070-135">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8e070-135">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="8e070-136">ADO.NET içindeki verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-136">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="8e070-137">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8e070-137">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="8e070-138">SQL Server özgü özellikler ve işlevlerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-138">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="8e070-139">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="8e070-139">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="8e070-140">ADO.NET ' de sağlayıcıya bağımsız kod yazmanıza izin veren genel sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e070-140">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e070-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e070-141">See also</span></span>

- [<span data-ttu-id="8e070-142">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8e070-142">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="8e070-143">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8e070-143">ADO.NET Overview</span></span>](ado-net-overview.md)
