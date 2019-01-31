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
# <a name="commonbehaviors"></a>\<commonBehaviors >
`commonBehaviors` Bölümü machine.config dosyasında yalnızca tanımlanabilir. Adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon, sırasıyla tüm WCF uç noktaları ve makinede hizmetler tarafından kullanılan davranışı öğeleri tanımlar. İçinde tanımlanan davranışları `endpointBehaviors` yalnızca istemciler ve içinde tanımlanan davranışları uygulanır `serviceBehaviors` yalnızca Hizmetleri için uygulanır. Bir davranış hem de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümler, davranış `behaviors` bölüm tercih verilir.
