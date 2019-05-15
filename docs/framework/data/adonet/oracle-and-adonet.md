---
title: Oracle ve ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: a8668ee115a3babbdf1ef549a418187d2c5e26b8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583413"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="8f0c8-102">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8f0c8-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="8f0c8-103">Türlerinde <xref:System.Data.OracleClient> kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="8f0c8-104">Türleri geçerli sürümü of.NET Framework içinde desteklenen kalır, ancak gelecekteki bir sürümde kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="8f0c8-105">Microsoft, üçüncü taraf Oracle sağlayıcısı kullanmanızı önerir.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="8f0c8-106">Bu bölümde, özellikler ve Oracle için .NET Framework veri sağlayıcısı özgü davranışları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="8f0c8-107">Oracle için .NET Framework veri sağlayıcısı, Oracle istemci yazılımı tarafından sağlanan Oracle Çağrı Arabirimi (OCI) kullanarak bir Oracle veritabanına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="8f0c8-108">Veri sağlayıcısı işlevselliği, SQL Server, OLE DB ve ODBC için .NET Framework veri sağlayıcıları benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="8f0c8-109">Oracle için .NET Framework veri sağlayıcısı kullanmak için bir uygulama başvurmalıdır <xref:System.Data.OracleClient> gösterildiği gibi ad alanı:</span><span class="sxs-lookup"><span data-stu-id="8f0c8-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="8f0c8-110">Kodunuzu derlediğinizde de DLL'ye bir başvuru içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="8f0c8-111">Örneğin, bir C# programı derleme yapıyorsanız, komut satırınızda içermelidir:</span><span class="sxs-lookup"><span data-stu-id="8f0c8-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="8f0c8-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8f0c8-112">In This Section</span></span>  
 [<span data-ttu-id="8f0c8-113">Sistem Gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="8f0c8-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="8f0c8-114">Oracle için .NET Framework veri sağlayıcısı kullanma gereksinimleri ve bir dizi kullanırken dikkat etmeniz gereken sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="8f0c8-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="8f0c8-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="8f0c8-116">Açıklar <xref:System.Data.OracleClient.OracleBFile> Oracle BDOSYA veri türü ile çalışmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="8f0c8-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="8f0c8-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="8f0c8-118">Açıklar <xref:System.Data.OracleClient.OracleLob> Oracle LOB veri türleriyle çalışmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="8f0c8-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="8f0c8-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="8f0c8-120">Oracle REF CURSOR veri türü için destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="8f0c8-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="8f0c8-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="8f0c8-122">Yapıları dahil olmak üzere Oracle veri türleriyle çalışmak için kullanabileceğiniz açıklar <xref:System.Data.OracleClient.OracleNumber> ve <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="8f0c8-123">Oracle Dizileri</span><span class="sxs-lookup"><span data-stu-id="8f0c8-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="8f0c8-124">Anahtar Oracle sırası sunucu tarafından oluşturulan değerleri almak için destek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="8f0c8-125">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="8f0c8-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="8f0c8-126">Oracle veri türleri ve eşleşmeleri listeler <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="8f0c8-127">Oracle Dağıtılmış İşlemleri</span><span class="sxs-lookup"><span data-stu-id="8f0c8-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="8f0c8-128">Açıklayan nasıl <xref:System.Data.OracleClient.OracleConnection> nesne bir işlem etkin olduğunu belirlerse, varolan bir dağıtılmış işlemde otomatik olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8f0c8-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8f0c8-129">Related Sections</span></span>  
 [<span data-ttu-id="8f0c8-130">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="8f0c8-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="8f0c8-131">Güvenli kodlama uygulamalarını kullanırken tanımlar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f0c8-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="8f0c8-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="8f0c8-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="8f0c8-133">Oluşturma ve kullanma işlemini açıklamaktadır `DataSets`, belirlenmiş `DataSets`, `DataTables`, ve `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="8f0c8-134">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="8f0c8-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="8f0c8-135">ADO.NET'te veri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="8f0c8-136">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8f0c8-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="8f0c8-137">Özellikler ve SQL Server'a özel işlevler ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="8f0c8-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="8f0c8-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="8f0c8-139">Sağlayıcı-bağımsız kod yazmaya olanak tanıyan genel sınıfları açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f0c8-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0c8-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f0c8-140">See also</span></span>

- [<span data-ttu-id="8f0c8-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8f0c8-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="8f0c8-142">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8f0c8-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
