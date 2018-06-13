---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350328"
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="f9a21-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="f9a21-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="f9a21-103">`commonBehaviors` Bölümü yalnızca machine.config dosyasındaki tanımlanması.</span><span class="sxs-lookup"><span data-stu-id="f9a21-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="f9a21-104">Adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="f9a21-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="f9a21-105">Her koleksiyon tüm WCF uç noktaları ve hizmetler makinedeki sırasıyla tüketilen davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9a21-105">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="f9a21-106">Tanımlanan davranışları `endpointBehaviors` tanımlanan davranışları ve istemcilere yalnızca uygulanan `serviceBehaviors` yalnızca Hizmetleri için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f9a21-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="f9a21-107">Bir davranış ikisi de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümlerinde, davranış `behaviors` bölümü tercih verilen.</span><span class="sxs-lookup"><span data-stu-id="f9a21-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
