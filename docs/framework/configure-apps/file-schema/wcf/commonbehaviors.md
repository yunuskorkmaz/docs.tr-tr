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
# <a name="commonbehaviors"></a>\<commonBehaviors >
`commonBehaviors` Bölümü machine.config dosyasında yalnızca tanımlanabilir. Adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon, sırasıyla tüm WCF uç noktaları ve makinede hizmetler tarafından kullanılan davranışı öğeleri tanımlar. İçinde tanımlanan davranışları `endpointBehaviors` yalnızca istemciler ve içinde tanımlanan davranışları uygulanır `serviceBehaviors` yalnızca Hizmetleri için uygulanır. Bir davranış hem de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümler, davranış `behaviors` bölüm tercih verilir.
