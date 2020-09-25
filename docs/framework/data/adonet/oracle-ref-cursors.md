---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: cbf330ba381a825c2d16038c01d7bdc52bc8f482
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180887"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="92584-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="92584-102">Oracle REF CURSORs</span></span>

<span data-ttu-id="92584-103">Oracle için .NET Framework Veri Sağlayıcısı Oracle **ref cursor** veri türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="92584-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="92584-104">Oracle REF IMLEÇLER ile çalışmak için veri sağlayıcısını kullanırken aşağıdaki davranışları göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="92584-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92584-105">Bazı davranışlar Oracle için Microsoft OLE DB Sağlayıcısı (MSDAORA) farklıdır.</span><span class="sxs-lookup"><span data-stu-id="92584-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="92584-106">Performans nedenleriyle, Oracle için Veri Sağlayıcısı, açıkça belirtmediğiniz sürece MSDAORA olarak, **ref cursor** veri türlerini otomatik olarak bağlamayın.</span><span class="sxs-lookup"><span data-stu-id="92584-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="92584-107">Veri sağlayıcısı, REF CURSOR parametrelerini belirtmek için kullanılan {resultset} kaçış dahil olmak üzere herhangi bir ODBC kaçış dizisini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="92584-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="92584-108">REF IMLEÇLER döndüren bir saklı yordamı yürütmek için, içindeki parametreleri <xref:System.Data.OracleClient.OracleParameterCollection> <xref:System.Data.OracleClient.OracleType> **Imlece** ve <xref:System.Data.OracleClient.OracleParameter.Direction%2A> **output**ile tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="92584-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="92584-109">Veri sağlayıcısı yalnızca çıkış parametreleri olarak başvuru Imleçleri bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="92584-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="92584-110">Sağlayıcı, giriş parametresi olarak başvuru Imleçleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="92584-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="92584-111"><xref:System.Data.OracleClient.OracleDataReader>Parametre değerinden alma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="92584-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="92584-112">Değerler, <xref:System.DBNull> komut yürütmeden sonra türüdür.</span><span class="sxs-lookup"><span data-stu-id="92584-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="92584-113">REF Imleçleri (örneğin, çağrılırken) ile birlikte kullanılan tek **CommandBehavior** numaralandırma değeri <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> **CloseConnection**ise, diğerleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="92584-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="92584-114">**OracleDataReader** 'Daki başvuru imleçlerinin sırası, **OracleParameterCollection**içindeki parametrelerin sırasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="92584-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="92584-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A>Özellik yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="92584-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="92584-116">PL/SQL **tablo** veri türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="92584-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="92584-117">Ancak, REF Imleçleri daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="92584-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="92584-118">**Tablo** veri türü kullanmanız GEREKIYORSA, msdaora ile OLE DB .NET veri sağlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="92584-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92584-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="92584-119">In This Section</span></span>  

 [<span data-ttu-id="92584-120">REF CURSOR Örnekleri</span><span class="sxs-lookup"><span data-stu-id="92584-120">REF CURSOR Examples</span></span>](ref-cursor-examples.md)  
 <span data-ttu-id="92584-121">REF IMLEÇLER kullanmayı gösteren üç örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="92584-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="92584-122">OracleDataReader’da REF CURSOR Parametreleri</span><span class="sxs-lookup"><span data-stu-id="92584-122">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="92584-123">Bir başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve değeri bir **OracleDataReader**olarak okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="92584-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="92584-124">OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="92584-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="92584-125">İki başvuru IMLECI parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini ve bir **OracleDataReader**kullanarak değerleri okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="92584-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="92584-126">Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="92584-126">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="92584-127">İki REF CURSOR parametresi döndüren bir PL/SQL saklı yordamının nasıl yürütüleceğini gösterir ve <xref:System.Data.DataSet> döndürülen satırlarla bir ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="92584-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92584-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92584-128">See also</span></span>

- [<span data-ttu-id="92584-129">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="92584-129">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="92584-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92584-130">ADO.NET Overview</span></span>](ado-net-overview.md)
