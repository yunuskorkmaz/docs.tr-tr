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
`commonBehaviors`Bölüm yalnızca Machine. config dosyasında tanımlanabilir. Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .  Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar. İçinde tanımlanan davranışlar `endpointBehaviors` yalnızca istemcilere uygulanır ve ' de tanımlanan davranışlar `serviceBehaviors` yalnızca hizmetlere uygulanır. Bir davranış hem hem de bölümlerinde tanımlanmışsa `commonBehaviors` `behaviors` , `behaviors` bölümdeki davranışa tercih edilir.
