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
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` Bölümü yalnızca machine.config dosyasındaki tanımlanması. Adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.  Her koleksiyon tüm WCF uç noktaları ve hizmetler makinedeki sırasıyla tüketilen davranışı öğeleri tanımlar. Tanımlanan davranışları `endpointBehaviors` tanımlanan davranışları ve istemcilere yalnızca uygulanan `serviceBehaviors` yalnızca Hizmetleri için uygulanır. Bir davranış ikisi de tanımlanmışsa `commonBehaviors` ve `behaviors` bölümlerinde, davranış `behaviors` bölümü tercih verilen.
