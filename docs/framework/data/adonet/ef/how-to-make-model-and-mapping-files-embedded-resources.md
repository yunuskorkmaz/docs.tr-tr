---
title: 'Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: c88e0c09742d76c7508d7d782eabbe46035d3501
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251440"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="4e785-102">Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma</span><span class="sxs-lookup"><span data-stu-id="4e785-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="4e785-103">, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Model ve eşleme dosyalarını bir uygulamanın katıştırılmış kaynakları olarak dağıtmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e785-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="4e785-104">Katıştırılmış model ve eşleme dosyaları olan derlemenin, varlık bağlantısıyla aynı uygulama etki alanında yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e785-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="4e785-105">Daha fazla bilgi için bkz. [bağlantı dizeleri](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="4e785-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="4e785-106">Varsayılan olarak, Varlık Veri Modeli araçları modeli ve eşleme dosyalarını gömer.</span><span class="sxs-lookup"><span data-stu-id="4e785-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="4e785-107">Model ve eşleme dosyalarını el ile tanımladığınızda, dosyaların bir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uygulamayla birlikte gömülü kaynaklar olarak dağıtıldığından emin olmak için bu yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e785-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e785-108">Katıştırılmış kaynakları korumak için, model ve eşleme dosyaları her değiştirildiğinde bu yordamı yinelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e785-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="4e785-109">Model ve eşleme dosyalarını eklemek için</span><span class="sxs-lookup"><span data-stu-id="4e785-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="4e785-110">**Çözüm Gezgini**, kavramsal (. csdl) dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="4e785-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="4e785-111">**Özellikler** bölmesinde, **derleme eylemini** **katıştırılmış kaynak**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4e785-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="4e785-112">Depolama (. ssdl) dosyası ve eşleme (. MSL) dosyası için 1 ve 2. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="4e785-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="4e785-113">**Çözüm Gezgini**, App. config dosyasına çift tıklayın ve ardından `Metadata` `connectionString` özniteliğinde parametresini aşağıdaki biçimlerden birine göre değiştirin:</span><span class="sxs-lookup"><span data-stu-id="4e785-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="4e785-114">`Metadata=``res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="4e785-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="4e785-115">`Metadata=``res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="4e785-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="4e785-116">Daha fazla bilgi için bkz. [bağlantı dizeleri](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="4e785-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e785-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e785-117">Example</span></span>  
 <span data-ttu-id="4e785-118">Aşağıdaki bağlantı dizesi, [AdventureWorks Sales modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)için gömülü modele ve eşleme dosyalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="4e785-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="4e785-119">Bu bağlantı dizesi projenin App. config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="4e785-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4e785-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e785-120">See also</span></span>

- [<span data-ttu-id="4e785-121">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="4e785-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="4e785-122">Nasıl yapılır: Bağlantı dizesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="4e785-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="4e785-123">Nasıl yapılır: Bir EntityConnection bağlantı dizesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e785-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="4e785-124">[ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4e785-124">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
