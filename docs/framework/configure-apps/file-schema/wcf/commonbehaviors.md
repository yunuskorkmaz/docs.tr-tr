---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 55f70157b6759c5e1cb45da20eed928fa1d4a183
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176064"
---
# \<commonBehaviors>

<span data-ttu-id="889a6-101">`commonBehaviors`Bölüm yalnızca machine.config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="889a6-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="889a6-102">Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="889a6-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="889a6-103">Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="889a6-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="889a6-104">İçinde tanımlanan davranışlar `endpointBehaviors` yalnızca istemcilere uygulanır ve ' de tanımlanan davranışlar `serviceBehaviors` yalnızca hizmetlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="889a6-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="889a6-105">Bir davranış hem hem de bölümlerinde tanımlanmışsa `commonBehaviors` `behaviors` , `behaviors` bölümdeki davranışa tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="889a6-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
