---
title: Azure Mantık Uygulamaları - Sunucusuz uygulamalar
description: Azure Logic Apps, bulut hizmetleri ve şirket içi sistemler arasında uygulamaları ve verileri tümleştiren otomatik ölçeklenebilir iş akışları oluşturmayı sağlar.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676753"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="247d7-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="247d7-103">Azure Logic Apps</span></span>

<span data-ttu-id="247d7-104">[Azure Logic Apps,](https://docs.microsoft.com/azure/logic-apps) bulut hizmetleri ve şirket içi sistemler arasında uygulamaları ve verileri tümleştirmek için otomatik iş akışları oluşturmak için sunucusuz bir altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="247d7-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="247d7-105">Görsel bir tasarımcı kullanarak iş akışları oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="247d7-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="247d7-106">Olaylara veya zamanlayıcılara dayalı iş akışlarını tetikleyebilir ve tümleştirme uygulamalarına konektörleri kullanabilir ve işletmeler arası (B2B) iletişimi kolaylaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="247d7-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="247d7-107">Logic Apps, Azure Fonksiyonları ile sorunsuz bir şekilde tümleşir.</span><span class="sxs-lookup"><span data-stu-id="247d7-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Azure Logic Apps logosu](./media/logic-apps-logo.png)

<span data-ttu-id="247d7-109">Logic Apps, bulut hizmetlerinizi (işlevler gibi) bulut kaynaklarıyla (kuyruklar ve veritabanları gibi) bağlamaktan daha fazlasını yapabilir.</span><span class="sxs-lookup"><span data-stu-id="247d7-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="247d7-110">Ayrıca şirket içi ağ geçidi ile şirket içi iş akışları düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="247d7-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="247d7-111">Örneğin, iş akışınızdaki bulut tabanlı bir olaya veya koşullu mantığa yanıt olarak şirket içi SQL depolanan yordamı tetiklemek için Mantık Uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="247d7-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="247d7-112">[Azure Şirket Içi Veri Ağ Geçidi ile şirket içi veri kaynaklarına bağlanma](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="247d7-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Logic Apps mimarisi](./media/logic-apps-architecture.png)

<span data-ttu-id="247d7-114">Azure İşlevleri gibi, Logic App iş akışlarını bir tetikleyiciyle başlatırsınız.</span><span class="sxs-lookup"><span data-stu-id="247d7-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="247d7-115">Seçim yapabileceğiniz birçok tetikleyici vardır.</span><span class="sxs-lookup"><span data-stu-id="247d7-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="247d7-116">Aşağıdaki yakalama, mevcut yüzlerce daha popüler olanlardan sadece birkaçını gösterir.</span><span class="sxs-lookup"><span data-stu-id="247d7-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Logic Apps tetikleyicileri](./media/logic-app-triggers.png)

<span data-ttu-id="247d7-118">Uygulama tetiklendikten sonra, adımları, döngüleri, koşulları ve eylemleri oluşturmak için görsel tasarımcıyı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="247d7-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="247d7-119">Önceki adımda alınan tüm veriler sonraki adımlarda kullanmanız için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="247d7-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="247d7-120">Aşağıdaki iş akışı URL'leri bir CosmosDB veritabanından yükler.</span><span class="sxs-lookup"><span data-stu-id="247d7-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="247d7-121">Bu twitter'da onlar `t.co` için daha sonra arama bir dizi olanlar bulur.</span><span class="sxs-lookup"><span data-stu-id="247d7-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="247d7-122">Karşılık gelen tweetleri bulursa, bir işlevi arayarak belgeleri ilgili tweetlerle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="247d7-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Mantık Uygulaması iş akışı](./media/logic-app-workflow.png)

<span data-ttu-id="247d7-124">Logic Apps panosu, iş akışlarınızı çalıştırma geçmişini ve her çalıştırmanın başarıyla tamamlanıp tamamlanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="247d7-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="247d7-125">Belirli bir çalıştırmaya gidebilir ve her adımda kullanılan verileri sorun giderme için inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="247d7-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="247d7-126">Logic Apps ayrıca, edinebileceğiniz varolan şablonları da sağlar ve karmaşık kurumsal iş akışları için uygundur.</span><span class="sxs-lookup"><span data-stu-id="247d7-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="247d7-127">Daha fazla bilgi için [Azure Mantık Uygulamaları'na](https://docs.microsoft.com/azure/logic-apps)bakın.</span><span class="sxs-lookup"><span data-stu-id="247d7-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="247d7-128">[Önceki](application-insights.md)
>[Sonraki](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="247d7-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
