---
title: Azure Logic Apps-sunucusuz uygulamalar
description: Azure Logic Apps bulut hizmetleri ve şirket içi sistemler arasında uygulamaları ve verileri tümleştiren otomatik ölçeklenebilir iş akışları oluşturmayı etkinleştirin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676753"
---
# <a name="azure-logic-apps"></a><span data-ttu-id="9c111-103">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="9c111-103">Azure Logic Apps</span></span>

<span data-ttu-id="9c111-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) , bulut hizmetleri ve şirket içi sistemler arasında uygulama ve verileri bütünleştirmek üzere otomatik iş akışları oluşturmak için sunucusuz bir altyapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c111-104">[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) provides a serverless engine to build automated workflows to integrate apps and data between cloud services and on-premises systems.</span></span> <span data-ttu-id="9c111-105">Bir görsel tasarımcı kullanarak iş akışları oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="9c111-105">You build workflows using a visual designer.</span></span> <span data-ttu-id="9c111-106">İş akışlarını olaylara veya zamanlayıcılar temelinde tetikleyip, uygulamaları tümleştirmek ve işletmeler arası (B2B) iletişimini kolaylaştırmak için bağlayıcılardan yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c111-106">You can trigger workflows based on events or timers and leverage connectors to integration applications and facilitate business-to-business (B2B) communication.</span></span> <span data-ttu-id="9c111-107">Logic Apps, Azure Işlevleri ile sorunsuz bir şekilde tümleşir.</span><span class="sxs-lookup"><span data-stu-id="9c111-107">Logic Apps integrates seamlessly with Azure Functions.</span></span>

![Azure Logic Apps logosu](./media/logic-apps-logo.png)

<span data-ttu-id="9c111-109">Logic Apps, bulut hizmetlerinizi (işlevler gibi) bulut kaynaklarıyla (kuyruklar ve veritabanları gibi) yalnızca bağlama özelliğinden daha fazlasını yapabilir.</span><span class="sxs-lookup"><span data-stu-id="9c111-109">Logic Apps can do more than just connect your cloud services (like functions) with cloud resources (like queues and databases).</span></span> <span data-ttu-id="9c111-110">Şirket içi ağ geçidi ile şirket içi iş akışlarını da düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c111-110">You can also orchestrate on-premises workflows with the on-premises gateway.</span></span> <span data-ttu-id="9c111-111">Örneğin, mantıksal uygulamayı kullanarak bir şirket içi SQL saklı yordamını, iş akışınızda bulut tabanlı bir olaya veya koşullu mantığa yanıt olarak tetikleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c111-111">For example, you can use the Logic App to trigger an on-premises SQL stored procedure in response to a cloud-based event or conditional logic in your workflow.</span></span> <span data-ttu-id="9c111-112">[Azure şirket Içi veri ağ geçidi ile şirket içi veri kaynaklarına bağlanma](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="9c111-112">Learn more about [Connecting to on-premises data sources with Azure On-premises Data Gateway](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).</span></span>

![Logic Apps mimarisi](./media/logic-apps-architecture.png)

<span data-ttu-id="9c111-114">Azure Işlevleri gibi, mantıksal uygulama iş akışlarını bir tetikleyici ile başlatılersiniz.</span><span class="sxs-lookup"><span data-stu-id="9c111-114">Like Azure Functions, you kick off Logic App workflows with a trigger.</span></span> <span data-ttu-id="9c111-115">Aralarından seçim yapabileceğiniz birçok tetikleyici vardır.</span><span class="sxs-lookup"><span data-stu-id="9c111-115">There are many triggers for you to choose from.</span></span> <span data-ttu-id="9c111-116">Aşağıdaki yakalama, mevcut yüzlerce yüzlerce daha popüler olanlarından yalnızca birkaçını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c111-116">The following capture shows just a few of the more popular ones out of hundreds that are available.</span></span>

![Logic Apps Tetikleyicileri](./media/logic-app-triggers.png)

<span data-ttu-id="9c111-118">Uygulama tetiklendikten sonra, adımları, döngüleri, koşulları ve eylemleri oluşturmak için görsel tasarımcı 'yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c111-118">Once the app is triggered, you can use the visual designer to build out steps, loops, conditions, and actions.</span></span> <span data-ttu-id="9c111-119">Önceki adımda alınan tüm veriler sonraki adımlarda kullanabileceğiniz şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c111-119">Any data ingested in a previous step is available for you to use in subsequent steps.</span></span> <span data-ttu-id="9c111-120">Aşağıdaki iş akışı, CosmosDB veritabanından URL 'Leri yükler.</span><span class="sxs-lookup"><span data-stu-id="9c111-120">The following workflow loads URLs from a CosmosDB database.</span></span> <span data-ttu-id="9c111-121">`t.co` barındırmalarını bulur ve sonra Twitter 'da arar.</span><span class="sxs-lookup"><span data-stu-id="9c111-121">It finds the ones with a host of `t.co` then searches for them on Twitter.</span></span> <span data-ttu-id="9c111-122">Bunlara karşılık gelen fazla yer bulunursa, bir işlevi çağırarak ilgili alanı bulunan belgeleri güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9c111-122">If it finds corresponding tweets, it updates the documents with the related tweets by calling a function.</span></span>

![Mantıksal uygulama iş akışı](./media/logic-app-workflow.png)

<span data-ttu-id="9c111-124">Logic Apps panosu, iş akışlarınızı çalıştırmanın geçmişini ve her çalıştırmanın başarıyla tamamlanıp tamamlanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c111-124">The Logic Apps dashboard shows the history of running your workflows and whether each run completed successfully or not.</span></span> <span data-ttu-id="9c111-125">Belirli bir çalıştırmaya gidebilir ve sorun giderme için her adım tarafından kullanılan verileri inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c111-125">You can navigate into any given run and inspect the data used by each step for troubleshooting.</span></span> <span data-ttu-id="9c111-126">Logic Apps Ayrıca, düzenleyebileceğiniz ve karmaşık kurumsal iş akışları için uygun olan şablonları da sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c111-126">Logic Apps also provides existing templates you can edit and are well suited for complex enterprise workflows.</span></span>

<span data-ttu-id="9c111-127">Daha fazla bilgi için bkz. [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span><span class="sxs-lookup"><span data-stu-id="9c111-127">To learn more, see [Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9c111-128">[Önceki](application-insights.md)
>[İleri](event-grid.md)</span><span class="sxs-lookup"><span data-stu-id="9c111-128">[Previous](application-insights.md)
[Next](event-grid.md)</span></span>
