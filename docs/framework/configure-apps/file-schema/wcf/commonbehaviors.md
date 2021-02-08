---
description: 'Hakkında daha fazla bilgi edinin: <commonBehaviors>'
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 2fa7397a2833623728bcca286682178d1cf3e1df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802326"
---
# \<commonBehaviors>

<span data-ttu-id="1f56d-102">`commonBehaviors`Bölüm yalnızca machine.config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1f56d-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="1f56d-103">Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="1f56d-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1f56d-104">Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1f56d-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="1f56d-105">İçinde tanımlanan davranışlar `endpointBehaviors` yalnızca istemcilere uygulanır ve ' de tanımlanan davranışlar `serviceBehaviors` yalnızca hizmetlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1f56d-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="1f56d-106">Bir davranış hem hem de bölümlerinde tanımlanmışsa `commonBehaviors` `behaviors` , `behaviors` bölümdeki davranışa tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="1f56d-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
