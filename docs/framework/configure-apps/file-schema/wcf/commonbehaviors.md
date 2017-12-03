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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06d09763b0281eb7edafadbbd59ff924b751d73e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` Bölümü yalnızca machine.config dosyasındaki tanımlanması. Adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her bir koleksiyon tarafından tüketilen davranışı öğeleri tanımlayan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uç noktaları ve hizmetler makinedeki sırasıyla. Tanımlanan davranışları `endpointBehaviors` tanımlanan davranışları ve istemcilere yalnızca uygulanan `serviceBehaviors` yalnızca Hizmetleri için uygulanır. Bir davranış ikisi de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümlerinde, davranış `behaviors` bölümü tercih verilen.
