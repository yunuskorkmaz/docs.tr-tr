---
title: Oracle ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 381f796bec31bece354001ad46bf5079381d1b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914551"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="dad80-102">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dad80-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="dad80-103">İçindeki <xref:System.Data.OracleClient> türler kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="dad80-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="dad80-104">Türler geçerli sürüm of.NET çerçevesinde desteklenmeye devam eder, ancak gelecekteki bir sürümde kaldırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="dad80-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="dad80-105">Microsoft, üçüncü taraf bir Oracle sağlayıcısı kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="dad80-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="dad80-106">Bu bölümde, Oracle için .NET Framework Veri Sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dad80-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="dad80-107">Oracle için .NET Framework Veri Sağlayıcısı Oracle Istemci yazılımı tarafından sağlanan Oracle Çağrı arabirimini (OCı) kullanarak bir Oracle veritabanına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="dad80-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="dad80-108">Veri sağlayıcısının işlevselliği, SQL Server, OLE DB ve ODBC için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dad80-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="dad80-109">Oracle için .NET Framework veri sağlayıcısı kullanmak için, bir uygulamanın <xref:System.Data.OracleClient> ad alanına aşağıdaki şekilde başvurması gerekir:</span><span class="sxs-lookup"><span data-stu-id="dad80-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="dad80-110">Kodunuzu derlerken DLL 'ye bir başvuru de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dad80-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="dad80-111">Örneğin, bir C# program derlerken komut satırlarınız şunları içermelidir:</span><span class="sxs-lookup"><span data-stu-id="dad80-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="dad80-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dad80-112">In This Section</span></span>  
 [<span data-ttu-id="dad80-113">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="dad80-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="dad80-114">Oracle için .NET Framework Veri Sağlayıcısı kullanma gereksinimlerini açıklar ve bunu kullanırken bilinmesi gereken birçok sorunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="dad80-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="dad80-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="dad80-116">Oracle BDOSYA veri türüyle çalışmak için kullanılan sınıfınıaçıklar.<xref:System.Data.OracleClient.OracleBFile></span><span class="sxs-lookup"><span data-stu-id="dad80-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="dad80-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="dad80-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="dad80-118">Oracle LOB veri türleriyle çalışmak için kullanılan sınıfınıaçıklar.<xref:System.Data.OracleClient.OracleLob></span><span class="sxs-lookup"><span data-stu-id="dad80-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="dad80-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="dad80-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="dad80-120">Oracle REF CURSOR veri türü için desteği açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="dad80-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="dad80-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="dad80-122"><xref:System.Data.OracleClient.OracleNumber> Ve<xref:System.Data.OracleClient.OracleString>dahil Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="dad80-123">Oracle Dizileri</span><span class="sxs-lookup"><span data-stu-id="dad80-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="dad80-124">Sunucu tarafından oluşturulan anahtar Oracle sıra değerlerini alma desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="dad80-125">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="dad80-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="dad80-126">Oracle veri türlerini ve bunların eşlemelerini <xref:System.Data.OracleClient.OracleDataReader>listeler.</span><span class="sxs-lookup"><span data-stu-id="dad80-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="dad80-127">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="dad80-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="dad80-128">Bir işlemin etkin <xref:System.Data.OracleClient.OracleConnection> olduğunu belirlerse, nesnenin var olan bir dağıtılmış işlemde otomatik olarak nasıl listeleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dad80-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dad80-129">Related Sections</span></span>  
 [<span data-ttu-id="dad80-130">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="dad80-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="dad80-131">ADO.NET kullanılırken güvenli kodlama uygulamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="dad80-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="dad80-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="dad80-133">' `DataSets`Nin nasıl oluşturulduğunu ve kullanılacağını açıklar, `DataSets` `DataTables`türü, ve `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="dad80-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="dad80-134">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="dad80-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="dad80-135">ADO.NET içindeki verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="dad80-136">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dad80-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="dad80-137">SQL Server özgü özellikler ve işlevlerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="dad80-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="dad80-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="dad80-139">ADO.NET ' de sağlayıcıya bağımsız kod yazmanıza izin veren genel sınıfları açıklar.</span><span class="sxs-lookup"><span data-stu-id="dad80-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad80-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dad80-140">See also</span></span>

- [<span data-ttu-id="dad80-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dad80-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="dad80-142">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="dad80-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
