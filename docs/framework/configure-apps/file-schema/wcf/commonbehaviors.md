---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: aaf89f73b6de250aaa572b8fef31e5a1ebd5482b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="29f46-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="29f46-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="29f46-103">`commonBehaviors` Bölümü yalnızca machine.config dosyasındaki tanımlanması.</span><span class="sxs-lookup"><span data-stu-id="29f46-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="29f46-104">Adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="29f46-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="29f46-105">Her bir koleksiyon tarafından tüketilen davranışı öğeleri tanımlayan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uç noktaları ve hizmetler makinedeki sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="29f46-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="29f46-106">Tanımlanan davranışları `endpointBehaviors` tanımlanan davranışları ve istemcilere yalnızca uygulanan `serviceBehaviors` yalnızca Hizmetleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="29f46-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="29f46-107">Bir davranış ikisi de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümlerinde, davranış `behaviors` bölümü tercih verilen.</span><span class="sxs-lookup"><span data-stu-id="29f46-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
