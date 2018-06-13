---
title: Oracle ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: d4a86abeca19a0c634d362c1a8a41f5be7346ed7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765795"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="b157c-102">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b157c-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="b157c-103">Türler <xref:System.Data.OracleClient> kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b157c-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="b157c-104">Türleri geçerli sürüm of.NET Framework içinde desteklenen kalır, ancak gelecekteki bir sürümde kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="b157c-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="b157c-105">Microsoft, üçüncü taraf Oracle sağlayıcısı kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="b157c-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="b157c-106">Bu bölümde özellikleri ve özgü davranışları açıklanmaktadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b157c-106">This section describes features and behaviors that are specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="b157c-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Veri sağlayıcısı Oracle için Oracle Çağrı Arabirimi (OCI) Oracle istemci yazılımı tarafından sağlanan adımları kullanarak bir Oracle veritabanına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b157c-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="b157c-108">Veri sağlayıcısı işlevselliğini benzer şekilde tasarlanmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server, OLE DB ve ODBC için veri sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="b157c-108">The functionality of the data provider is designed to be similar to that of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="b157c-109">Kullanılacak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için Oracle veri sağlayıcısı, bir uygulama başvurmalıdır <xref:System.Data.OracleClient> şekilde ad alanı:</span><span class="sxs-lookup"><span data-stu-id="b157c-109">To use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="b157c-110">Kodunuzu derlerken DLL bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b157c-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="b157c-111">Örneğin, C# programı derleme, komut satırında içermelidir:</span><span class="sxs-lookup"><span data-stu-id="b157c-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="b157c-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b157c-112">In This Section</span></span>  
 [<span data-ttu-id="b157c-113">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="b157c-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="b157c-114">Kullanma gereksinimleri açıklanır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] , Oracle için veri sağlayıcı ve onu kullanırken dikkate etmeniz gereken sorunlar sayısını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b157c-114">Describes requirements for using the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="b157c-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="b157c-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="b157c-116">Açıklar <xref:System.Data.OracleClient.OracleBFile> Oracle BDOSYA veri türü ile çalışmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="b157c-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="b157c-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="b157c-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="b157c-118">Açıklar <xref:System.Data.OracleClient.OracleLob> Oracle LOB veri türleriyle çalışmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="b157c-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="b157c-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="b157c-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="b157c-120">Oracle REF İMLEÇ veri türü için destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b157c-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="b157c-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="b157c-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="b157c-122">Dahil olmak üzere Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar <xref:System.Data.OracleClient.OracleNumber> ve <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="b157c-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="b157c-123">Oracle Dizileri</span><span class="sxs-lookup"><span data-stu-id="b157c-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="b157c-124">Anahtar Oracle sırası sunucu tarafından üretilen değerleri almak için destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b157c-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="b157c-125">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="b157c-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="b157c-126">Oracle veri türlerini ve bunların eşlemelere listeler <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b157c-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="b157c-127">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="b157c-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="b157c-128">Açıklar nasıl <xref:System.Data.OracleClient.OracleConnection> nesne bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b157c-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b157c-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b157c-129">Related Sections</span></span>  
 [<span data-ttu-id="b157c-130">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="b157c-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="b157c-131">Güvenli kodlama uygulamalarını kullanırken açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b157c-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="b157c-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="b157c-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="b157c-133">Oluşturma ve kullanma açıklar `DataSets`, yazılı `DataSets`, `DataTables`, ve `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="b157c-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="b157c-134">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b157c-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="b157c-135">ADO.NET veri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b157c-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="b157c-136">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b157c-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="b157c-137">Özellikleri ve SQL Server için belirli işlevleri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b157c-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="b157c-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="b157c-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="b157c-139">Sağlayıcı bağımsız kod yazmanıza izin Genel sınıflar açıklanmaktadır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b157c-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b157c-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b157c-140">See Also</span></span>  
 [<span data-ttu-id="b157c-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b157c-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="b157c-142">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b157c-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
