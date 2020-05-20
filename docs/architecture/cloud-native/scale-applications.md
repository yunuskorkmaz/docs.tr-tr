---
title: Bulutta yerel uygulamaları ölçeklendirme
description: Azure Kubernetes hizmeti ve Azure Işlevleri ile bulut Yerel uygulamalarını ölçeklendirerek Kullanıcı talebini uygun maliyetli bir şekilde karşılayın.
ms.date: 05/13/2020
ms.openlocfilehash: d425976eed248461a9c2e4fe03596f9f6dfd2eba
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613739"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="afc1a-103">Bulutta yerel uygulamaları ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="afc1a-103">Scaling cloud-native applications</span></span>

<span data-ttu-id="afc1a-104">Bulut barındırma ortamına geçme için en sık kullanılan ve en sık kullanılan avantajlardan biri ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc1a-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="afc1a-105">Ölçeklenebilirlik veya bir uygulamanın, her kullanıcı için performansı tehlikeye atmadan ek kullanıcı yükünü kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="afc1a-105">Scalability, or the ability for an application to accept additional user load without compromising performance for each user.</span></span> <span data-ttu-id="afc1a-106">En sık, her birine gerek duydukları kaynakları verilmeyen küçük parçalara kadar bir uygulamayı kırarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="afc1a-106">It's most often achieved by breaking up an application into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="afc1a-107">Bulut satıcıları dünyanın her yerindeki ve her yerde büyük ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="afc1a-107">Cloud vendors enable massive scalability anytime and anywhere in the world.</span></span>

 <span data-ttu-id="afc1a-108">Bu bölümde, bulutta yerel uygulamaların Kullanıcı talebini karşılayacak şekilde ölçeklendirilmesine olanak tanıyan teknolojiler tartışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="afc1a-108">In this chapter, we discuss technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="afc1a-109">Bu teknolojiler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="afc1a-109">These technologies include:</span></span>

- <span data-ttu-id="afc1a-110">Kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="afc1a-110">Containers</span></span>
- <span data-ttu-id="afc1a-111">Düzenleyiciler</span><span class="sxs-lookup"><span data-stu-id="afc1a-111">Orchestrators</span></span>
- <span data-ttu-id="afc1a-112">Sunucusuz bilgi işlem</span><span class="sxs-lookup"><span data-stu-id="afc1a-112">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="afc1a-113">[Önceki](centralized-configuration.md) 
> [Sonraki](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="afc1a-113">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
