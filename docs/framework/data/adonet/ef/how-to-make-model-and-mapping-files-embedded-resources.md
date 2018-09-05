---
title: 'Nasıl yapılır: yapma Model ve eşleme dosyalarını gömülü kaynak'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 35507f92d0ba9f434156773c8dc5621ed3c423c0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43555356"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="4391f-102">Nasıl yapılır: yapma Model ve eşleme dosyalarını gömülü kaynak</span><span class="sxs-lookup"><span data-stu-id="4391f-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="4391f-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Model ve eşleme dosyalarını gömülü kaynaklar bir uygulama dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4391f-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="4391f-104">Varlık bağlantı aynı uygulama etki alanında derleme ekli model ve eşleme dosyalarını ile yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4391f-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="4391f-105">Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="4391f-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="4391f-106">Varsayılan olarak, [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] araçları, model ve eşleme dosyalarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4391f-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="4391f-107">Model ve eşleme dosyalarını el ile tanımladığınızda, dosyaları ile birlikte gömülü kaynak olarak dağıtıldığından emin olmak için bu yordamı kullanın bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="4391f-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4391f-108">Katıştırılmış kaynakları korumak için model ve eşleme dosyalarını değiştirdiğinde bu yordamı yineleyin gerekir.</span><span class="sxs-lookup"><span data-stu-id="4391f-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="4391f-109">Model ve eşleme dosyalarını eklemek için</span><span class="sxs-lookup"><span data-stu-id="4391f-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="4391f-110">İçinde **Çözüm Gezgini**, kavramsal (.csdl) dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="4391f-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="4391f-111">İçinde **özellikleri** bölmesinde, **derleme eylemi** için **gömülü kaynak**.</span><span class="sxs-lookup"><span data-stu-id="4391f-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="4391f-112">Depolama (.ssdl) dosyası ve eşleme (.msl) dosyası için 1 ve 2 numaralı adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="4391f-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="4391f-113">İçinde **Çözüm Gezgini**, App.config dosyasına çift tıklayın ve ardından değişiklik `Metadata` parametresinde `connectionString` özniteliği aşağıdaki biçimlerden birini temel alan:</span><span class="sxs-lookup"><span data-stu-id="4391f-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="4391f-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="4391f-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="4391f-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="4391f-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="4391f-116">Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="4391f-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4391f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4391f-117">Example</span></span>  
 <span data-ttu-id="4391f-118">Ekli model ve eşleme dosyaları için aşağıdaki bağlantı dizesi başvuran [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="4391f-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="4391f-119">Bu bağlantı dizesi, projenin App.config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="4391f-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="4391f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4391f-120">See Also</span></span>  
 [<span data-ttu-id="4391f-121">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="4391f-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="4391f-122">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="4391f-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="4391f-123">Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4391f-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [<span data-ttu-id="4391f-124">ADO.NET varlık veri modeli araçları</span><span class="sxs-lookup"><span data-stu-id="4391f-124">ADO.NET Entity Data Model  Tools</span></span>](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
