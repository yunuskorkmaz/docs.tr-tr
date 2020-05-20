---
title: İzleme ve sistem durumu
description: İzleme ve sistem durumu
ms.date: 05/13/2020
ms.openlocfilehash: 28e98bbdb39a68d8961d4f3ab48cde5a07a4762b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613804"
---
# <a name="monitoring-and-health"></a><span data-ttu-id="f0b2c-103">İzleme ve sistem durumu</span><span class="sxs-lookup"><span data-stu-id="f0b2c-103">Monitoring and health</span></span>

<span data-ttu-id="f0b2c-104">Mikro hizmetler ve bulutta yerel uygulamalar, iyi DevOps uygulamalarıyla birlikte ele geçer.</span><span class="sxs-lookup"><span data-stu-id="f0b2c-104">Microservices and cloud-native applications go hand in hand with good DevOps practices.</span></span> <span data-ttu-id="f0b2c-105">DevOps birçok kişiye çok şey yapıyor, ancak belki de daha iyi tanımlardan biri bulut danışmanı ve DevOps yenilik öncüsü Donovan kahverengi 'dan geliyor:</span><span class="sxs-lookup"><span data-stu-id="f0b2c-105">DevOps is many things to many people but perhaps one of the better definitions comes from cloud advocate and DevOps evangelist Donovan Brown:</span></span>

<span data-ttu-id="f0b2c-106">"DevOps, son kullanıcılarımıza sürekli değer teslimi sağlayan kişiler, süreç ve ürünlerin birleşimidir."</span><span class="sxs-lookup"><span data-stu-id="f0b2c-106">"DevOps is the union of people, process, and products to enable continuous delivery of value to our end users."</span></span>

<span data-ttu-id="f0b2c-107">Ne yazık ki, terse tanımlarına göre her zaman daha fazla şey söyleyebileceğiniz yer vardır.</span><span class="sxs-lookup"><span data-stu-id="f0b2c-107">Unfortunately, with terse definitions, there's always room to say more things.</span></span> <span data-ttu-id="f0b2c-108">DevOps 'un temel bileşenlerinden biri, üretimde çalışan uygulamaların doğru ve verimli şekilde çalıştığından emin olmanızı sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f0b2c-108">One of the key components of DevOps is ensuring that the applications running in production are functioning properly and efficiently.</span></span> <span data-ttu-id="f0b2c-109">Üretimde uygulamanın sistem durumunu ölçmek için, sunuculardan, konaklardan ve uygulamadan oluşturulan çeşitli günlükleri ve ölçümleri izlemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f0b2c-109">To gauge the health of the application in production, it's necessary to monitor the various logs and metrics being produced from the servers, hosts, and the application proper.</span></span> <span data-ttu-id="f0b2c-110">Bulutta yerel bir uygulamayı desteklemek için çalışan farklı hizmetlerin sayısı, tek tek bileşenlerin ve uygulamanın sistem durumunu kritik bir sınama olarak izlemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0b2c-110">The number of different services running in support of a cloud-native application makes monitoring the health of individual components and the application as a whole a critical challenge.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f0b2c-111">[Önceki](resilient-communications.md) 
> [Sonraki](observability-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f0b2c-111">[Previous](resilient-communications.md)
[Next](observability-patterns.md)</span></span>
