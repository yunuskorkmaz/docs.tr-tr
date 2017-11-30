---
title: "Oracle REF imleçler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 277e12e59ea85be4d22e28a59bd7404e5e0111f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="b3912-102">Oracle REF imleçler</span><span class="sxs-lookup"><span data-stu-id="b3912-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="b3912-103">.NET Framework veri sağlayıcısı Oracle için Oracle destekleyen **REF İMLEÇ** veri türü.</span><span class="sxs-lookup"><span data-stu-id="b3912-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="b3912-104">Oracle REF imleçlerle çalışmak için veri sağlayıcısı kullanarak, aşağıdaki davranışları dikkate almanız.</span><span class="sxs-lookup"><span data-stu-id="b3912-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3912-105">Bazı davranışları Microsoft OLE DB Sağlayıcısı'nın Oracle (MSDAORA) farklı.</span><span class="sxs-lookup"><span data-stu-id="b3912-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="b3912-106">Performansı artırmak için Oracle veri sağlayıcısı otomatik olarak bağlanmaz **REF İMLEÇ** veri türleri, MSDAORA yaptığı gibi bunları açıkça belirtmediğiniz sürece.</span><span class="sxs-lookup"><span data-stu-id="b3912-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="b3912-107">Veri sağlayıcısı REF İMLEÇ parametrelerini belirtmek için kullanılan {sonuç} kaçış dahil olmak üzere tüm ODBC kaçış sıraları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b3912-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="b3912-108">REF imleçler döndüren bir saklı yordamı yürütme için parametre tanımlayın <xref:System.Data.OracleClient.OracleParameterCollection> ile bir <xref:System.Data.OracleClient.OracleType> , **imleç** ve <xref:System.Data.OracleClient.OracleParameter.Direction%2A> , **çıkış**.</span><span class="sxs-lookup"><span data-stu-id="b3912-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="b3912-109">Veri sağlayıcısı yalnızca çıkış parametreleri REF imleçler bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="b3912-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="b3912-110">Sağlayıcı REF imleçler giriş parametreleri olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="b3912-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="b3912-111">Alma bir <xref:System.Data.OracleClient.OracleDataReader> parametresi değeri desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b3912-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="b3912-112">Tür değerler <xref:System.DBNull> komut yürütme sonra.</span><span class="sxs-lookup"><span data-stu-id="b3912-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="b3912-113">Yalnızca **CommandBehavior** REF imleçlerle çalışır numaralandırma değeri (örneğin, çağrılırken <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) olan **CloseConnection**; diğerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b3912-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="b3912-114">REF imleçler sırasını **OracleDataReader** parametrelerinde terabayt bağlıdır **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="b3912-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="b3912-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Özelliği yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b3912-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="b3912-116">PL/SQL **tablo** veri türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="b3912-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="b3912-117">Ancak, REF imleçler daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="b3912-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="b3912-118">Kullanmanız gerekiyorsa bir **tablo** veri türü, OLE DB .NET veri sağlayıcısı MSDAORA ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3912-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3912-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b3912-119">In This Section</span></span>  
 [<span data-ttu-id="b3912-120">REF İMLEÇ örnekleri</span><span class="sxs-lookup"><span data-stu-id="b3912-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="b3912-121">REF imleçler kullanarak gösteren üç örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b3912-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="b3912-122">Bir OracleDataReader REF İMLEÇ parametreleri</span><span class="sxs-lookup"><span data-stu-id="b3912-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="b3912-123">Değeri olarak okur ve REF CURSOR parametresiyle döndüren bir PL/SQL saklı yordamı yürütme yapmayı gösteren bir **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="b3912-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="b3912-124">Bir OracleDataReader kullanarak birden çok REF imleçler veri alma</span><span class="sxs-lookup"><span data-stu-id="b3912-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="b3912-125">Kullanarak değerlerini okur ve iki REF İMLEÇ parametreleri döndüren bir PL/SQL saklı yordamı yürütme yapmayı gösteren bir **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="b3912-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="b3912-126">Kullanarak bir veri kümesi doldurma ya da daha fazla REF imleçler</span><span class="sxs-lookup"><span data-stu-id="b3912-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="b3912-127">Doldurur ve iki REF İMLEÇ parametreleri döndüren bir PL/SQL saklı yordamı yürütme yapmayı gösteren bir <xref:System.Data.DataSet> satırlarla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b3912-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3912-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3912-128">See Also</span></span>  
 [<span data-ttu-id="b3912-129">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b3912-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="b3912-130">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b3912-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
