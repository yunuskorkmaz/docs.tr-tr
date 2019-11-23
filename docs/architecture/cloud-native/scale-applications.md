---
title: Bulutta yerel uygulamaları ölçeklendirme
description: Azure Kubernetes hizmeti ve Azure Işlevleri ile bulut Yerel uygulamalarını ölçeklendirerek Kullanıcı talebini uygun maliyetli bir şekilde karşılayın.
ms.date: 09/23/2019
ms.openlocfilehash: 5f4aac5804c5498c331787083c943a6ea1b69748
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184829"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="dddc8-103">Bulutta yerel uygulamaları ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="dddc8-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="dddc8-104">Bulut barındırma ortamına geçme için en sık kullanılan ve en sık kullanılan avantajlardan biri ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="dddc8-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="dddc8-105">Ölçeklenebilirlik ya da bir uygulamanın, her kullanıcı için etkilenmemesi düşürmeden ek kullanıcı yükünü kabul etmesine izin verme yeteneği, çoğu zaman, her biri ihtiyaç duydukları her türlü kaynağa verilen uygulamaları küçük parçalara ayırarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="dddc8-105">Scalability, or the ability for an application to accept additional user load without unduly degrading performance for each user, is most often achieved by breaking up applications into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="dddc8-106">Bu bölümde, bulutta yerel uygulamaların Kullanıcı talebini karşılayacak şekilde ölçeklendirilmesine olanak tanıyan teknolojiler tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dddc8-106">In this chapter, we introduce the technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="dddc8-107">Bu teknolojiler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="dddc8-107">These technologies include:</span></span>

- <span data-ttu-id="dddc8-108">Kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="dddc8-108">Containers</span></span>
- <span data-ttu-id="dddc8-109">Düzenleyicileri</span><span class="sxs-lookup"><span data-stu-id="dddc8-109">Orchestrators</span></span>
- <span data-ttu-id="dddc8-110">Sunucusuz bilgi işlem</span><span class="sxs-lookup"><span data-stu-id="dddc8-110">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dddc8-111">[Önceki](centralized-configuration.md)
>[İleri](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="dddc8-111">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
