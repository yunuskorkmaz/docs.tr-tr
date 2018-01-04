---
title: "Yeniden deneme üstel geri alma ile uygulama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Yeniden deneme üstel geri alma ile uygulama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7ed97b750d6e3f2aa5def72e90e070a49a7c0e63
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-retries-with-exponential-backoff"></a>Yeniden deneme üstel geri alma ile uygulama

[*Üstel geri alma ile yeniden deneme* ](https://docs.microsoft.com/azure/architecture/patterns/retry) bir işlem, en fazla yeniden deneme sayısı üst sınırına kadar bir katlanarak artan bekleme süresi, yeniden deneme girişiminde bir tekniktir ( [üstel geri alma](https://en.wikipedia.org/wiki/Exponential_backoff)). Bu teknik bulut kaynaklarına aralıklı birden fazla birkaç saniye boyunca herhangi bir nedenle kullanılamaz durumda olabilir, olgu çalışır. Örneğin, bir orchestrator bir kapsayıcı Yük Dengeleme için bir kümedeki başka bir düğüme taşınıyor. Bu işlem sırasında bazı istekler başarısız olabilir. Bir veritabanı SQL Azure, burada bir veritabanı başka bir sunucuya Yük Dengeleme, veritabanı neden birkaç saniye kullanılamaz hale gelmesine taşınabilir gibi başka bir örnek olabilir.

Yeniden deneme mantığı üstel geri alma ile uygulamak için birçok yaklaşım vardır.


>[!div class="step-by-step"]
[Önceki] (kısmi-hatası-strategies.md) [sonraki] (implement-resilient-entity-framework-core-sql-connections.md)
