---
title: İzleme ve sistem durumu
description: İzleme ve sistem durumu
ms.date: 09/23/2019
ms.openlocfilehash: 6e62c0dad3bdac9bed8eccfadd9011f9b6256efc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184976"
---
# <a name="monitoring-and-health"></a><span data-ttu-id="fb2f0-103">İzleme ve sistem durumu</span><span class="sxs-lookup"><span data-stu-id="fb2f0-103">Monitoring and health</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fb2f0-104">Mikro hizmetler ve bulutta yerel uygulamalar, iyi DevOps uygulamalarıyla birlikte ele geçer.</span><span class="sxs-lookup"><span data-stu-id="fb2f0-104">Microservices and cloud-native applications go hand in hand with good DevOps practices.</span></span> <span data-ttu-id="fb2f0-105">DevOps birçok kişiye çok şey yapıyor, ancak belki de daha iyi tanımlardan biri bulut danışmanı ve DevOps yenilik öncüsü Donovan kahverengi 'dan geliyor:</span><span class="sxs-lookup"><span data-stu-id="fb2f0-105">DevOps is many things to many people but perhaps one of the better definitions comes from cloud advocate and DevOps evangelist Donovan Brown:</span></span> 

<span data-ttu-id="fb2f0-106">"DevOps, son kullanıcılarımıza sürekli değer teslimi sağlayan kişiler, süreç ve ürünlerin birleşimidir."</span><span class="sxs-lookup"><span data-stu-id="fb2f0-106">"DevOps is the union of people, process, and products to enable continuous delivery of value to our end users."</span></span>

<span data-ttu-id="fb2f0-107">Ne yazık ki, terse tanımlarına göre her zaman daha fazla şey söyleyebileceğiniz yer vardır.</span><span class="sxs-lookup"><span data-stu-id="fb2f0-107">Unfortunately, with terse definitions, there's always room to say more things.</span></span> <span data-ttu-id="fb2f0-108">DevOps 'un temel bileşenlerinden biri, üretimde çalışan uygulamaların doğru ve verimli şekilde çalıştığından emin olmanızı sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="fb2f0-108">One of the key components of DevOps is ensuring that the applications running in production are functioning properly and efficiently.</span></span> <span data-ttu-id="fb2f0-109">Üretimde uygulamanın sistem durumunu ölçmek için, sunuculardan, konaklardan ve uygulamadan oluşturulan çeşitli günlükleri ve ölçümleri izlemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fb2f0-109">To gauge the health of the application in production, it's necessary to monitor the various logs and metrics being produced from the servers, hosts, and the application proper.</span></span> <span data-ttu-id="fb2f0-110">Bulutta yerel bir uygulamayı desteklemek için çalışan farklı hizmetlerin sayısı, tek tek bileşenlerin ve uygulamanın sistem durumunu kritik bir sınama olarak izlemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb2f0-110">The number of different services running in support of a cloud-native application makes monitoring the health of individual components and the application as a whole a critical challenge.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fb2f0-111">[Önceki](resilient-communications.md)
>[İleri](observability-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="fb2f0-111">[Previous](resilient-communications.md)
[Next](observability-patterns.md)</span></span>
