---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704368"
---
# \<commonBehaviors>
<span data-ttu-id="7b013-101">`commonBehaviors`Bölüm yalnızca Machine. config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="7b013-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="7b013-102">Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="7b013-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="7b013-103">Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7b013-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="7b013-104">İçinde tanımlanan davranışlar `endpointBehaviors` yalnızca istemcilere uygulanır ve ' de tanımlanan davranışlar `serviceBehaviors` yalnızca hizmetlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7b013-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="7b013-105">Bir davranış hem hem de bölümlerinde tanımlanmışsa `commonBehaviors` `behaviors` , `behaviors` bölümdeki davranışa tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="7b013-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
