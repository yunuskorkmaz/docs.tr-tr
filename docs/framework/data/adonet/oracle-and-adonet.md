---
title: Oracle ve ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 5683f2b4ba57021ff6dda3a51baca016f886b605
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980086"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="889ff-102">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="889ff-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="889ff-103"><xref:System.Data.OracleClient> türler kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="889ff-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="889ff-104">Türler geçerli sürüm of.NET çerçevesinde desteklenmeye devam eder, ancak gelecekteki bir sürümde kaldırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="889ff-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="889ff-105">Microsoft, üçüncü taraf bir Oracle sağlayıcısı kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="889ff-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="889ff-106">Bu bölümde, Oracle için .NET Framework Veri Sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="889ff-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="889ff-107">Oracle için .NET Framework Veri Sağlayıcısı Oracle Istemci yazılımı tarafından sağlanan Oracle Çağrı arabirimini (OCı) kullanarak bir Oracle veritabanına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="889ff-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="889ff-108">Veri sağlayıcısının işlevselliği, SQL Server, OLE DB ve ODBC için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="889ff-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="889ff-109">Oracle için .NET Framework Veri Sağlayıcısı kullanmak için, bir uygulamanın <xref:System.Data.OracleClient> ad alanına aşağıdaki gibi başvurması gerekir:</span><span class="sxs-lookup"><span data-stu-id="889ff-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="889ff-110">Kodunuzu derlerken DLL 'ye bir başvuru de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="889ff-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="889ff-111">Örneğin, bir C# program derlerken komut satırlarınız şunları içermelidir:</span><span class="sxs-lookup"><span data-stu-id="889ff-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="889ff-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="889ff-112">In This Section</span></span>  
 [<span data-ttu-id="889ff-113">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="889ff-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="889ff-114">Oracle için .NET Framework Veri Sağlayıcısı kullanma gereksinimlerini açıklar ve bunu kullanırken bilinmesi gereken birçok sorunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="889ff-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="889ff-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="889ff-116">Oracle BDOSYA veri türüyle çalışmak için kullanılan <xref:System.Data.OracleClient.OracleBFile> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="889ff-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="889ff-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="889ff-118">Oracle LOB veri türleriyle çalışmak için kullanılan <xref:System.Data.OracleClient.OracleLob> sınıfını açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="889ff-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="889ff-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="889ff-120">Oracle REF CURSOR veri türü için desteği açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="889ff-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="889ff-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="889ff-122"><xref:System.Data.OracleClient.OracleNumber> ve <xref:System.Data.OracleClient.OracleString>dahil Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="889ff-123">Oracle Dizileri</span><span class="sxs-lookup"><span data-stu-id="889ff-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="889ff-124">Sunucu tarafından oluşturulan anahtar Oracle sıra değerlerini alma desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="889ff-125">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="889ff-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="889ff-126">Oracle veri türlerini ve bunların <xref:System.Data.OracleClient.OracleDataReader>eşlemelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="889ff-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="889ff-127">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="889ff-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="889ff-128"><xref:System.Data.OracleClient.OracleConnection> nesnesinin, bir işlemin etkin olduğunu belirlerse mevcut bir dağıtılmış işlemde nasıl otomatik olarak bir şekilde listeleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="889ff-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="889ff-129">Related Sections</span></span>  
 [<span data-ttu-id="889ff-130">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="889ff-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="889ff-131">ADO.NET kullanılırken güvenli kodlama uygulamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="889ff-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="889ff-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="889ff-133">`DataSets`, `DataSets`, `DataTables`ve `DataViews`oluşturmayı ve kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="889ff-134">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="889ff-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="889ff-135">ADO.NET içindeki verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="889ff-136">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="889ff-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="889ff-137">SQL Server özgü özellikler ve işlevlerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="889ff-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="889ff-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="889ff-139">ADO.NET ' de sağlayıcıya bağımsız kod yazmanıza izin veren genel sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="889ff-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889ff-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="889ff-140">See also</span></span>

- [<span data-ttu-id="889ff-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="889ff-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="889ff-142">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="889ff-142">ADO.NET Overview</span></span>](ado-net-overview.md)
