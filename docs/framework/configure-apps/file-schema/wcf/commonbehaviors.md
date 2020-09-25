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

`commonBehaviors`Bölüm yalnızca machine.config dosyasında tanımlanabilir. Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .  Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar. İçinde tanımlanan davranışlar `endpointBehaviors` yalnızca istemcilere uygulanır ve ' de tanımlanan davranışlar `serviceBehaviors` yalnızca hizmetlere uygulanır. Bir davranış hem hem de bölümlerinde tanımlanmışsa `commonBehaviors` `behaviors` , `behaviors` bölümdeki davranışa tercih edilir.
