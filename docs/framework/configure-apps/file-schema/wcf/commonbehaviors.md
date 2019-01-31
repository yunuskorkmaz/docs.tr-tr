---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268768"
---
# <a name="commonbehaviors"></a><span data-ttu-id="d3be9-101">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d3be9-101">\<commonBehaviors></span></span>
<span data-ttu-id="d3be9-102">`commonBehaviors` Bölümü machine.config dosyasında yalnızca tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d3be9-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="d3be9-103">Adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="d3be9-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="d3be9-104">Her koleksiyon, sırasıyla tüm WCF uç noktaları ve makinede hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3be9-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="d3be9-105">İçinde tanımlanan davranışları `endpointBehaviors` yalnızca istemciler ve içinde tanımlanan davranışları uygulanır `serviceBehaviors` yalnızca Hizmetleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d3be9-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="d3be9-106">Bir davranış hem de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümler, davranış `behaviors` bölüm tercih verilir.</span><span class="sxs-lookup"><span data-stu-id="d3be9-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
