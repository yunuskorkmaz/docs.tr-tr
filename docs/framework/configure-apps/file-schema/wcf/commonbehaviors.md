---
title: '&lt;commonBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fceca3c1cf0cc980310b1c4fbf85f6bce5ad1a0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="e3fae-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="e3fae-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="e3fae-103">`commonBehaviors` Bölümü yalnızca machine.config dosyasındaki tanımlanması.</span><span class="sxs-lookup"><span data-stu-id="e3fae-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="e3fae-104">Adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="e3fae-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e3fae-105">Her bir koleksiyon tarafından tüketilen davranışı öğeleri tanımlayan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uç noktaları ve hizmetler makinedeki sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e3fae-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="e3fae-106">Tanımlanan davranışları `endpointBehaviors` tanımlanan davranışları ve istemcilere yalnızca uygulanan `serviceBehaviors` yalnızca Hizmetleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e3fae-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="e3fae-107">Bir davranış ikisi de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümlerinde, davranış `behaviors` bölümü tercih verilen.</span><span class="sxs-lookup"><span data-stu-id="e3fae-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
