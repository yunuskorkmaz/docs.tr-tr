---
title: Azure Logic Apps - sunucusuz uygulamalar
description: Azure Logic Apps uygulamaları tümleştirin otomatik ölçeklenebilir iş akışlarını oluşturmayı etkinleştirin ve verileri bulut Hizmetleri ve şirket içi sistemler.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 019539f0da1d38259870907c38ed0eb6a62f1929
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37405021"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="b8a04-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="b8a04-103">Azure Logic Apps</span></span>

<span data-ttu-id="b8a04-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) uygulamaları ve bulut hizmetleri arasında verileri tümleştirmek için otomatik iş akışları oluşturmak için sunucusuz bir altyapı sağlar ve şirket içi sistemler.</span><span class="sxs-lookup"><span data-stu-id="b8a04-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="b8a04-105">Bir görsel tasarımcı kullanarak iş akışları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b8a04-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="b8a04-106">Olayları veya süreölçerler ve Dengeleme bağlayıcılar tümleştirme uygulamalara dayalı iş akışlarını tetikleyin ve işletmeden işletmeye (B2B) iletişimi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b8a04-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="b8a04-107">Logic Apps, Azure işlevleri ile sorunsuz şekilde entegre olur.</span><span class="sxs-lookup"><span data-stu-id="b8a04-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Azure Logic Apps logosu](./media/logic-apps-logo.png)

<span data-ttu-id="b8a04-109">Logic Apps, bulut hizmetlerinizde (gibi işlevler) bağlamanız yeterlidir birden fazla (kuyruklar ve veritabanları gibi) bulut kaynakları ile yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a04-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="b8a04-110">Şirket içi ağ geçidi ile şirket içi iş akışları da düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a04-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="b8a04-111">Örneğin, mantıksal uygulama, bulut tabanlı bir olaya yanıt olarak bir şirket içi SQL saklı yordamı veya koşullu mantığı, iş akışı tetiklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a04-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="b8a04-112">Daha fazla bilgi edinin [Azure şirket içi veri ağ geçidi ile şirket içi veri kaynaklarına bağlanma](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span><span class="sxs-lookup"><span data-stu-id="b8a04-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Logic Apps mimarisi](./media/logic-apps-architecture.png)

<span data-ttu-id="b8a04-114">Azure işlevleri gibi bir tetikleyici ile mantıksal uygulama iş akışlarını başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="b8a04-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="b8a04-115">Aralarından seçim yapabileceğiniz birçok tetikleyici vardır.</span><span class="sxs-lookup"><span data-stu-id="b8a04-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="b8a04-116">Aşağıdaki yakalama daha popüler olanları tanesi kullanılabilir olan yüzlerce birkaçı gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b8a04-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Mantıksal uygulama Tetikleyicileri](./media/logic-app-triggers.png)

<span data-ttu-id="b8a04-118">Uygulama tetiklendikten sonra görsel tasarımcı adımları, döngüler, koşullar ve Eylemler oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a04-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="b8a04-119">Bir önceki adımda alınan tüm veriler, sonraki adımlarda kullanılacağı için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8a04-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="b8a04-120">Aşağıdaki iş akışı URL'leri CosmosDB veritabanından yükler.</span><span class="sxs-lookup"><span data-stu-id="b8a04-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="b8a04-121">Çok sayıda oluşturduklarıyla bulduğu `t.co` kendileri için Twitter'da arama yapar.</span><span class="sxs-lookup"><span data-stu-id="b8a04-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="b8a04-122">İlgili tweetleri bulur, belgeleri ile ilgili tweetleri bir işlev çağırarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b8a04-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Mantıksal uygulama iş akışı](./media/logic-app-workflow.png)

<span data-ttu-id="b8a04-124">Logic Apps Panosu, akışlarınızı ve her çalışıp tamamlanmış başarılı ya da başarısız çalıştırma geçmişini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8a04-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="b8a04-125">Verilen tüm run gidin ve sorun giderme için her adımı tarafından kullanılan verileri inceleyin.</span><span class="sxs-lookup"><span data-stu-id="b8a04-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="b8a04-126">Logic Apps ayrıca düzenleyebilir ve karışık kurumsal iş akışları için uygun olan mevcut şablonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8a04-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="b8a04-127">Daha fazla bilgi için bkz. [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="b8a04-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b8a04-128">[Önceki](application-insights.md)
[İleri](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="b8a04-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>