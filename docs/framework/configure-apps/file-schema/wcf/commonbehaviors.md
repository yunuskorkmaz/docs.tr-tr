---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704368"
---
# <a name="commonbehaviors"></a><span data-ttu-id="a4150-101">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a4150-101">\<commonBehaviors></span></span>
<span data-ttu-id="a4150-102">`commonBehaviors` Bölümü machine.config dosyasında yalnızca tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a4150-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="a4150-103">Adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="a4150-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="a4150-104">Her koleksiyon, sırasıyla tüm WCF uç noktaları ve makinede hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4150-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="a4150-105">İçinde tanımlanan davranışları `endpointBehaviors` yalnızca istemciler ve içinde tanımlanan davranışları uygulanır `serviceBehaviors` yalnızca Hizmetleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a4150-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="a4150-106">Bir davranış hem de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümler, davranış `behaviors` bölüm tercih verilir.</span><span class="sxs-lookup"><span data-stu-id="a4150-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
