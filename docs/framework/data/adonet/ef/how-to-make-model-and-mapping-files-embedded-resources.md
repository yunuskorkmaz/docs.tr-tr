---
title: "Nasıl yapılır: yapma modeli ve eşleme dosyaları katıştırılmış kaynakları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6b8439e81c9a77f15556c21c5e96add86265c4ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="0db62-102">Nasıl yapılır: yapma modeli ve eşleme dosyaları katıştırılmış kaynakları</span><span class="sxs-lookup"><span data-stu-id="0db62-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="0db62-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Modeli ve eşleme dosyaları uygulamanın gömülü kaynaklar dağıtmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0db62-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="0db62-104">Varlık bağlantısı aynı uygulama etki alanında katıştırılmış modeli ve eşleme dosyaları içeren derlemenin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0db62-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="0db62-105">Daha fazla bilgi için bkz: [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="0db62-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="0db62-106">Varsayılan olarak, [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] araçları katıştırmak modeli ve eşleme dosyaları.</span><span class="sxs-lookup"><span data-stu-id="0db62-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="0db62-107">Model ve eşleme dosyaları el ile tanımladığınızda, dosyaları ile birlikte gömülü kaynaklar olarak dağıtıldığından emin olmak için bu yordamı kullanın bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="0db62-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0db62-108">Katıştırılmış kaynakları korumak için model ve eşleme dosyaları değiştirdiğinde bu yordamı yineleyin gerekir.</span><span class="sxs-lookup"><span data-stu-id="0db62-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="0db62-109">Model ve eşleme dosyaları eklemek için</span><span class="sxs-lookup"><span data-stu-id="0db62-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="0db62-110">İçinde **Çözüm Gezgini**, kavramsal (.csdl) dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="0db62-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="0db62-111">İçinde **özellikleri** kümesi bölmesi, **yapı eylemi** için **katıştırılmış kaynak**.</span><span class="sxs-lookup"><span data-stu-id="0db62-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="0db62-112">Depolama (.ssdl) dosyası ve eşleme (.msl) dosyası için 1 ve 2. adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="0db62-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="0db62-113">İçinde **Çözüm Gezgini**, App.config dosyasına çift tıklayın ve ardından değiştirme `Metadata` parametresinde `connectionString` özniteliği aşağıdaki biçimlerden birini temel alarak:</span><span class="sxs-lookup"><span data-stu-id="0db62-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="0db62-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="0db62-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="0db62-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="0db62-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="0db62-116">Daha fazla bilgi için bkz: [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="0db62-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0db62-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="0db62-117">Example</span></span>  
 <span data-ttu-id="0db62-118">Aşağıdaki bağlantı dizesi başvuran katıştırılmış modeli ve eşleme dosyaları için [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="0db62-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="0db62-119">Bu bağlantı dizesi projenin App.config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="0db62-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="0db62-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0db62-120">See Also</span></span>  
 [<span data-ttu-id="0db62-121">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="0db62-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="0db62-122">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0db62-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="0db62-123">Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0db62-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [<span data-ttu-id="0db62-124">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="0db62-124">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
