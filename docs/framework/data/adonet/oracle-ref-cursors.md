---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: b23b0f07d7755fed820481a3ad1fe831ae3f5224
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213174"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="25b4e-102">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="25b4e-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="25b4e-103">Oracle, Oracle için .NET Framework veri sağlayıcısı sunuyor **REF CURSOR** veri türü.</span><span class="sxs-lookup"><span data-stu-id="25b4e-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="25b4e-104">Oracle REF CURSOR ile çalışmak için veri sağlayıcısı'nı kullanarak, aşağıdaki davranışları düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="25b4e-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25b4e-105">Bazı davranışları Microsoft OLE DB Sağlayıcısı'nın Oracle (MSDAORA) farklı.</span><span class="sxs-lookup"><span data-stu-id="25b4e-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="25b4e-106">Performansla ilgili nedenlerle, Oracle için veri sağlayıcısı otomatik olarak bağlama **REF CURSOR** veri türleri, MSDAORA gibi bunları açıkça belirtmediğiniz sürece.</span><span class="sxs-lookup"><span data-stu-id="25b4e-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="25b4e-107">Veri sağlayıcısı REF CURSOR parametreleri belirtmek için kullanılan {sonuç} kaçış dahil olmak üzere tüm ODBC kaçış dizileri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="25b4e-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="25b4e-108">REF CURSOR döndüren bir saklı yordamı yürütmek için parametreleri tanımlayın <xref:System.Data.OracleClient.OracleParameterCollection> ile bir <xref:System.Data.OracleClient.OracleType> , **imleç** ve <xref:System.Data.OracleClient.OracleParameter.Direction%2A> , **çıkış**.</span><span class="sxs-lookup"><span data-stu-id="25b4e-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="25b4e-109">Veri sağlayıcısı, yalnızca çıkış parametreleri REF CURSOR bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="25b4e-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="25b4e-110">Sağlayıcı REF CURSOR giriş parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="25b4e-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="25b4e-111">Alma bir <xref:System.Data.OracleClient.OracleDataReader> parametresinden değeri desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="25b4e-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="25b4e-112">Türünde değerleri olan <xref:System.DBNull> komut yürütmenin sonrasına.</span><span class="sxs-lookup"><span data-stu-id="25b4e-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="25b4e-113">Yalnızca **CommandBehavior** REF CURSOR ile çalışan numaralandırma değeri (örneğin, çağrılırken <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) olan **CloseConnection**; diğerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="25b4e-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="25b4e-114">REF CURSOR içinde sırasını **OracleDataReader** parametrelerinde bazında bağlıdır **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="25b4e-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="25b4e-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Özelliği yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="25b4e-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="25b4e-116">PL/SQL **tablo** veri türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="25b4e-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="25b4e-117">Ancak, REF CURSOR daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="25b4e-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="25b4e-118">Kullanmanız gerekiyorsa bir **tablo** veri türü, OLE DB .NET veri sağlayıcısı MSDAORA ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="25b4e-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25b4e-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="25b4e-119">In This Section</span></span>  
 [<span data-ttu-id="25b4e-120">REF CURSOR Örnekleri</span><span class="sxs-lookup"><span data-stu-id="25b4e-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="25b4e-121">REF CURSOR kullanarak gösteren üç örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="25b4e-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="25b4e-122">OracleDataReader’da REF CURSOR Parametreleri</span><span class="sxs-lookup"><span data-stu-id="25b4e-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="25b4e-123">Bir REF CURSOR parametresiyle döndürür ve olarak değeri okuyan bir PL/SQL saklı yordamı yürütme yapmayı gösteren bir **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="25b4e-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="25b4e-124">OracleDataReader Kullanarak Birden Çok REF CURSOR’dan Veri Alma</span><span class="sxs-lookup"><span data-stu-id="25b4e-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="25b4e-125">İki REF CURSOR parametreleri döndürür ve kullanarak değerlerini okur PL/SQL saklı yordamı yürütmek anlatan bir **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="25b4e-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="25b4e-126">Bir veya daha fazla REF CURSOR Kullanarak DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="25b4e-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="25b4e-127">İki REF CURSOR parametreleri döndürür ve dolduran bir PL/SQL saklı yordamı yürütme yapmayı gösteren bir <xref:System.Data.DataSet> satırlarla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="25b4e-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b4e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25b4e-128">See also</span></span>

- [<span data-ttu-id="25b4e-129">Oracle ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="25b4e-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="25b4e-130">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="25b4e-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
