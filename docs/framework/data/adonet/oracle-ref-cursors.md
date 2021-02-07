---
description: 'Daha fazla bilgi edinin: Oracle REF IMLEÇLER'
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 0a9c5e95a9f0d2da74fd6a3db19f15699a3e2787
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672458"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="cca8b-103">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="cca8b-103">Oracle REF CURSORs</span></span>

<span data-ttu-id="cca8b-104">Oracle için .NET Framework Veri Sağlayıcısı Oracle **ref cursor** veri türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="cca8b-104">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="cca8b-105">Oracle REF IMLEÇLER ile çalışmak için veri sağlayıcısını kullanırken aşağıdaki davranışları göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cca8b-105">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cca8b-106">Bazı davranışlar Oracle için Microsoft OLE DB Sağlayıcısı (MSDAORA) farklıdır.</span><span class="sxs-lookup"><span data-stu-id="cca8b-106">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="cca8b-107">Performans nedenleriyle, Oracle için Veri Sağlayıcısı, açıkça belirtmediğiniz sürece MSDAORA olarak, **ref cursor** veri türlerini otomatik olarak bağlamayın.</span><span class="sxs-lookup"><span data-stu-id="cca8b-107">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="cca8b-108">Veri sağlayıcısı, REF CURSOR parametrelerini belirtmek için kullanılan {resultset} kaçış dahil olmak üzere herhangi bir ODBC kaçış dizisini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cca8b-108">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="cca8b-109">REF IMLEÇLER döndüren bir saklı yordamı yürütmek için, içindeki parametreleri <xref:System.Data.OracleClient.OracleParameterCollection> <xref:System.Data.OracleClient.OracleType> **Imlece** ve <xref:System.Data.OracleClient.OracleParameter.Direction%2A> **output** ile tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cca8b-109">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="cca8b-110">Veri sağlayıcısı yalnızca çıkış parametreleri olarak başvuru Imleçleri bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="cca8b-110">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="cca8b-111">Sağlayıcı, giriş parametresi olarak başvuru Imleçleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cca8b-111">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="cca8b-112"><xref:System.Data.OracleClient.OracleDataReader>Parametre değerinden alma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cca8b-112">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="cca8b-113">Değerler, <xref:System.DBNull> komut yürütmeden sonra türüdür.</span><span class="sxs-lookup"><span data-stu-id="cca8b-113">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="cca8b-114">REF Imleçleri (örneğin, çağrılırken) ile birlikte kullanılan tek **CommandBehavior** numaralandırma değeri <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> **CloseConnection** ise, diğerleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="cca8b-114">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="cca8b-115">**OracleDataReader** 'Daki başvuru imleçlerinin sırası, **OracleParameterCollection** içindeki parametrelerin sırasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cca8b-115">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="cca8b-116"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A>Özellik yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="cca8b-116">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="cca8b-117">PL/SQL **tablo** veri türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="cca8b-117">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="cca8b-118">Ancak, REF Imleçleri daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="cca8b-118">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="cca8b-119">**Tablo** veri türü kullanmanız GEREKIYORSA, msdaora ile OLE DB .NET veri sağlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="cca8b-119">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cca8b-120">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cca8b-120">In This Section</span></span>  

 [<span data-ttu-id="cca8b-121">REF CURSOR Örnekleri</span><span class="sxs-lookup"><span data-stu-id="cca8b-121">REF CURSOR Examples</span></span>](ref-cursor-examples.md)  
 <span data-ttu-id="cca8b-122">REF IMLEÇLER kullanmayı gösteren üç örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="cca8b-122">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="cca8b-123">OracleDataReader’da REF CURSOR Parametreleri</span><span class="sxs-lookup"><span data-stu-id="cca8b-123">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="cca8b-124">Bir başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve değeri bir **OracleDataReader** olarak okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cca8b-124">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="cca8b-125">OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="cca8b-125">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="cca8b-126">İki başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve bir **OracleDataReader** kullanarak değerleri okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cca8b-126">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="cca8b-127">Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="cca8b-127">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="cca8b-128">İki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini gösterir ve <xref:System.Data.DataSet> döndürülen satırlarla bir ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="cca8b-128">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca8b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cca8b-129">See also</span></span>

- [<span data-ttu-id="cca8b-130">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cca8b-130">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="cca8b-131">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cca8b-131">ADO.NET Overview</span></span>](ado-net-overview.md)
