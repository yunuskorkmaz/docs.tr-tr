---
title: Oracle ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ccfe40f218e3f09de53d6cb596a31b2520d9ff9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783479"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="2c0a6-102">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2c0a6-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="2c0a6-103">İçindeki <xref:System.Data.OracleClient> türler kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="2c0a6-104">Türler geçerli sürüm of.NET çerçevesinde desteklenmeye devam eder, ancak gelecekteki bir sürümde kaldırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="2c0a6-105">Microsoft, üçüncü taraf bir Oracle sağlayıcısı kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="2c0a6-106">Bu bölümde, Oracle için .NET Framework Veri Sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="2c0a6-107">Oracle için .NET Framework Veri Sağlayıcısı Oracle Istemci yazılımı tarafından sağlanan Oracle Çağrı arabirimini (OCı) kullanarak bir Oracle veritabanına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="2c0a6-108">Veri sağlayıcısının işlevselliği, SQL Server, OLE DB ve ODBC için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="2c0a6-109">Oracle için .NET Framework veri sağlayıcısı kullanmak için, bir uygulamanın <xref:System.Data.OracleClient> ad alanına aşağıdaki şekilde başvurması gerekir:</span><span class="sxs-lookup"><span data-stu-id="2c0a6-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="2c0a6-110">Kodunuzu derlerken DLL 'ye bir başvuru de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="2c0a6-111">Örneğin, bir C# program derlerken komut satırlarınız şunları içermelidir:</span><span class="sxs-lookup"><span data-stu-id="2c0a6-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="2c0a6-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2c0a6-112">In This Section</span></span>  
 [<span data-ttu-id="2c0a6-113">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="2c0a6-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="2c0a6-114">Oracle için .NET Framework Veri Sağlayıcısı kullanma gereksinimlerini açıklar ve bunu kullanırken bilinmesi gereken birçok sorunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="2c0a6-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="2c0a6-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="2c0a6-116">Oracle BDOSYA veri türüyle çalışmak için kullanılan sınıfınıaçıklar.<xref:System.Data.OracleClient.OracleBFile></span><span class="sxs-lookup"><span data-stu-id="2c0a6-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="2c0a6-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="2c0a6-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="2c0a6-118">Oracle LOB veri türleriyle çalışmak için kullanılan sınıfınıaçıklar.<xref:System.Data.OracleClient.OracleLob></span><span class="sxs-lookup"><span data-stu-id="2c0a6-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="2c0a6-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="2c0a6-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="2c0a6-120">Oracle REF CURSOR veri türü için desteği açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="2c0a6-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="2c0a6-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="2c0a6-122"><xref:System.Data.OracleClient.OracleNumber> Ve<xref:System.Data.OracleClient.OracleString>dahil Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="2c0a6-123">Oracle Dizileri</span><span class="sxs-lookup"><span data-stu-id="2c0a6-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="2c0a6-124">Sunucu tarafından oluşturulan anahtar Oracle sıra değerlerini alma desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="2c0a6-125">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="2c0a6-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="2c0a6-126">Oracle veri türlerini ve bunların eşlemelerini <xref:System.Data.OracleClient.OracleDataReader>listeler.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="2c0a6-127">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="2c0a6-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="2c0a6-128">Bir işlemin etkin <xref:System.Data.OracleClient.OracleConnection> olduğunu belirlerse, nesnenin var olan bir dağıtılmış işlemde otomatik olarak nasıl listeleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2c0a6-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2c0a6-129">Related Sections</span></span>  
 [<span data-ttu-id="2c0a6-130">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="2c0a6-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="2c0a6-131">ADO.NET kullanılırken güvenli kodlama uygulamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="2c0a6-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="2c0a6-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="2c0a6-133">' `DataSets`Nin nasıl oluşturulduğunu ve kullanılacağını açıklar, `DataSets` `DataTables`türü, ve `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="2c0a6-134">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2c0a6-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="2c0a6-135">ADO.NET içindeki verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="2c0a6-136">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2c0a6-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="2c0a6-137">SQL Server özgü özellikler ve işlevlerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="2c0a6-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="2c0a6-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="2c0a6-139">ADO.NET ' de sağlayıcıya bağımsız kod yazmanıza izin veren genel sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0a6-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c0a6-140">See also</span></span>

- [<span data-ttu-id="2c0a6-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2c0a6-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="2c0a6-142">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2c0a6-142">ADO.NET Overview</span></span>](ado-net-overview.md)
