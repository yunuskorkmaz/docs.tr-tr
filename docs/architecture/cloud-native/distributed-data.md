---
title: Dağıtılmış veriler
description: Azure için Cloud Native .NET uygulamaları tasarlama | Bulut Yerel uygulamaları için dağıtılmış veriler
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183135"
---
# <a name="distributed-data-for-cloud-native-apps"></a><span data-ttu-id="51ea7-103">Bulutta yerel uygulamalar için dağıtılmış veriler</span><span class="sxs-lookup"><span data-stu-id="51ea7-103">Distributed data for cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="51ea7-104">Birçok bağımsız mikro hizmetten oluşan, bulut tabanlı bir sistem oluştururken, veri depolama değişikliklerini düşündüğünüz şekilde düşünün.</span><span class="sxs-lookup"><span data-stu-id="51ea7-104">When constructing a cloud-native system that consists of many independent microservices, the way you think about data storage changes.</span></span>

<span data-ttu-id="51ea7-105">Geleneksel tek parçalı uygulamalar Şekil 5-1 ' de gösterilen merkezi bir veri deposuna tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="51ea7-105">Traditional monolithic applications favor a centralized data store shown in Figure 5-1.</span></span> 

![Tek monoparçalı veritabanı](./media/single-monolithic-database.png)

<span data-ttu-id="51ea7-107">**Şekil 5-1**.</span><span class="sxs-lookup"><span data-stu-id="51ea7-107">**Figure 5-1**.</span></span> <span data-ttu-id="51ea7-108">Tek monoparçalı veritabanı</span><span class="sxs-lookup"><span data-stu-id="51ea7-108">Single monolithic database</span></span>

<span data-ttu-id="51ea7-109">Önceki şekilde, tüm uygulama bileşenlerinin tek bir ilişkisel veritabanını nasıl tükettiğine göz önünde.</span><span class="sxs-lookup"><span data-stu-id="51ea7-109">Note in the previous figure how all of the application components consume a single relational database.</span></span>

<span data-ttu-id="51ea7-110">Bu yaklaşımın pek çok avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="51ea7-110">There are many benefits to this approach.</span></span> <span data-ttu-id="51ea7-111">Verileri birden çok tabloya yaymak kolaydır ve veri tutarlılığı sağlayan [ACID işlemlerini](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) uygulamak basittir.</span><span class="sxs-lookup"><span data-stu-id="51ea7-111">It's straightforward to query data spread across  multiple tables, and it's straightforward to implement [ACID transactions](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) that ensure data consistency.</span></span> <span data-ttu-id="51ea7-112">Her zaman *anında tutarlılık*vardır: tüm veri güncelleştirmelerinizi veya hiçbirini hiç bir şekilde sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="51ea7-112">You always end up with *immediate consistency*: either all your data updates or none of it does.</span></span>

<span data-ttu-id="51ea7-113">Bulut Yerel sistemleri, Şekil 5-2 ' de gösterilen, her mikro hizmetin kendi verilerini sahip olduğu ve kapsülleyen bir veri mimarisini tercih ediyor.</span><span class="sxs-lookup"><span data-stu-id="51ea7-113">Cloud-native systems favor a data architecture shown in Figure 5-2 in which each microservice owns and encapsulates its own data.</span></span>

![Mikro hizmetler genelinde birden çok veritabanı](./media/data-across-microservices.png)

<span data-ttu-id="51ea7-115">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="51ea7-115">**Figure 5-2**.</span></span> <span data-ttu-id="51ea7-116">Mikro hizmetler genelinde birden çok veritabanı</span><span class="sxs-lookup"><span data-stu-id="51ea7-116">Multiple databases across microservices</span></span>

<span data-ttu-id="51ea7-117">Önceki şekilde, her bir mikro hizmetin BT veri mağazasını nasıl sahip olduğunu ve bu verileri yalnızca ortak API 'sinden dış dünyayı açığa çıkardığını aklınızda saklayın.</span><span class="sxs-lookup"><span data-stu-id="51ea7-117">Note how in the previous figure each microservice owns and encapsulates it data store and only exposes data to the outside world from its public API.</span></span>
 
<span data-ttu-id="51ea7-118">Bu model, her mikro hizmetin, veri şeması değişikliklerini diğer mikro hizmetlerle koordine etmek zorunda kalmadan bağımsız olarak gelişmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="51ea7-118">This model enables each microservice to evolve independently without having to coordinate data schema changes with other microservices.</span></span> <span data-ttu-id="51ea7-119">Her mikro hizmet, ihtiyaçlarına en iyi eşleşen veri deposunu (ilişkisel veritabanı, belge veritabanı, anahtar-değer deposu) uygulamak için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="51ea7-119">Each microservice is free to implement the data store (relational database, document database, key-value store) type that best matches its needs.</span></span> <span data-ttu-id="51ea7-120">Çalışma zamanında, her mikro hizmet verilerini uygun şekilde ölçeklendirebilir.</span><span class="sxs-lookup"><span data-stu-id="51ea7-120">At runtime, each microservice can scale its data accordingly.</span></span> <span data-ttu-id="51ea7-121">Bu şekil 5-3 ' de gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51ea7-121">This is shown in Figure 5-3:</span></span>

![Çok yönlü veri kalıcılığı](./media/polyglot-data-persistence.png)

<span data-ttu-id="51ea7-123">**Şekil 5-3**.</span><span class="sxs-lookup"><span data-stu-id="51ea7-123">**Figure 5-3**.</span></span> <span data-ttu-id="51ea7-124">Çok yönlü veri kalıcılığı</span><span class="sxs-lookup"><span data-stu-id="51ea7-124">Polyglot data persistence</span></span>

<span data-ttu-id="51ea7-125">Önceki şekilde, ürün kataloğu ve Inventory mikro hizmetlerinin ilişkisel veritabanlarını, sıralama mikro hizmetini, bir NoSql belge veritabanını ve bir dış anahtar-değer deposu olan alışveriş sepeti mikro hizmetini benimsediğini not edin.</span><span class="sxs-lookup"><span data-stu-id="51ea7-125">Note how in the previous figure the product catalog and inventory microservices adopt relational databases, the ordering microservice, a NoSql document database, and the shopping cart microservice, which is an external key-value store.</span></span> <span data-ttu-id="51ea7-126">İlişkisel veritabanları karmaşık verilerle mikro hizmetler için uygun olmaya devam ederken, NoSQL veritabanları önemli ölçüde popülerliği kazanmıştır, hızlı arama ve yüksek kullanılabilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="51ea7-126">While relational databases remain relevant for microservices with complex data, NoSQL databases have gained considerable popularity, providing adaptability, fast lookup, and high availability.</span></span> <span data-ttu-id="51ea7-127">Şeicilerin, veri sınıflarının bir mimarisinden ve ORMs de daha pahalı ve zaman alıcı bir mimariden uzaklaşmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="51ea7-127">Their schemaless nature allows developers to move away from an architecture of typed data classes and ORMs that make change expensive and time-consuming.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="51ea7-128">[Önceki](service-mesh-communication-infrastructure.md)
>[İleri](data-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="51ea7-128">[Previous](service-mesh-communication-infrastructure.md)
[Next](data-patterns.md)</span></span>
