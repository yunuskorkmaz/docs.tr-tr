---
title: 'Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: eae3681664ab1fd095487a7b7ed395302faf2588
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329537"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="443eb-102">Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma</span><span class="sxs-lookup"><span data-stu-id="443eb-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="443eb-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , Model ve eşleme dosyalarını gömülü kaynaklar bir uygulama dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="443eb-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="443eb-104">Varlık bağlantı aynı uygulama etki alanında derleme ekli model ve eşleme dosyalarını ile yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="443eb-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="443eb-105">Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="443eb-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="443eb-106">Varsayılan olarak, [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] araçları, model ve eşleme dosyalarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="443eb-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="443eb-107">Model ve eşleme dosyalarını el ile tanımladığınızda, dosyaları ile birlikte gömülü kaynak olarak dağıtıldığından emin olmak için bu yordamı kullanın bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="443eb-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="443eb-108">Katıştırılmış kaynakları korumak için model ve eşleme dosyalarını değiştirdiğinde bu yordamı yineleyin gerekir.</span><span class="sxs-lookup"><span data-stu-id="443eb-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="443eb-109">Model ve eşleme dosyalarını eklemek için</span><span class="sxs-lookup"><span data-stu-id="443eb-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="443eb-110">İçinde **Çözüm Gezgini**, kavramsal (.csdl) dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="443eb-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="443eb-111">İçinde **özellikleri** bölmesinde, **derleme eylemi** için **gömülü kaynak**.</span><span class="sxs-lookup"><span data-stu-id="443eb-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="443eb-112">Depolama (.ssdl) dosyası ve eşleme (.msl) dosyası için 1 ve 2 numaralı adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="443eb-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="443eb-113">İçinde **Çözüm Gezgini**, App.config dosyasına çift tıklayın ve ardından değişiklik `Metadata` parametresinde `connectionString` özniteliği aşağıdaki biçimlerden birini temel alan:</span><span class="sxs-lookup"><span data-stu-id="443eb-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   `Metadata=` `res://<assemblyFullName>/<resourceName>;`  
  
    -   `Metadata=` `res://*/<resourceName>;`  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="443eb-114">Daha fazla bilgi için [bağlantı dizeleri](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="443eb-114">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="443eb-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="443eb-115">Example</span></span>  
 <span data-ttu-id="443eb-116">Ekli model ve eşleme dosyaları için aşağıdaki bağlantı dizesi başvuran [AdventureWorks satışları modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="443eb-116">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="443eb-117">Bu bağlantı dizesi, projenin App.config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="443eb-117">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="443eb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="443eb-118">See also</span></span>

- [<span data-ttu-id="443eb-119">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="443eb-119">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)
- [<span data-ttu-id="443eb-120">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="443eb-120">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)
- [<span data-ttu-id="443eb-121">Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="443eb-121">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)
- [<span data-ttu-id="443eb-122">ADO.NET Varlık Veri Modeli Araçları</span><span class="sxs-lookup"><span data-stu-id="443eb-122">ADO.NET Entity Data Model Tools</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
