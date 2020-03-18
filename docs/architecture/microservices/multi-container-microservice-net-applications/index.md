---
title: Multi Konteyner ve Microservice Tabanlı .NET Uygulamalarının Tasarımı ve Geliştirilmesi
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Multi Container ve Microservice Based .NET Uygulamaları Tasarlamak ve Geliştirmek için dış mimariyi anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 8c2f828e9913a0efcdf580371124b0f624daeffe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70296628"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Multi-Konteyner ve Microservice Tabanlı .NET Uygulamaları nın Tasarımı ve Geliştirilmesi

*Konteynerleştirilmiş mikrohizmet uygulamaları geliştirmek, çok konteyner uygulamaları geliştirdiğiniz anlamına gelir. Ancak, çok kapsayıcılı bir uygulama da daha basit olabilir (örneğin, üç katmanlı bir uygulama) ve bir microservice mimarisi kullanılarak oluşturulmayabilir.*

Daha önce "Docker bir mikro hizmet mimarisi inşa ederken gerekli mi?" sorusunu gündeme getirdi. Cevap açık bir hayır. Docker bir etkinleştirici ve önemli faydalar sağlayabilir, ancak konteyner ve Docker mikro hizmetler için zor bir gereklilik değildir. Örnek olarak, basit işlemler veya Docker kapsayıcıları gibi çalışan mikro hizmetleri destekleyen Azure Hizmet Kumaşı'nı kullanırken Docker ile veya Docker olmadan mikro hizmet tabanlı bir uygulama oluşturabilirsiniz.

Ancak, Docker kaplarına da dayanan mikrohizmet tabanlı bir uygulamanın nasıl tasarlanıp geliştireceğinibiliyorsanız, diğer, daha basit bir uygulama modelini tasarlayıp geliştirebilirsiniz. Örneğin, çok kapsayıcı lı bir yaklaşım da gerektiren üç katmanlı bir uygulama tasarlaabilirsiniz. Bu nedenle ve mikrohizmet mimarileri konteyner dünyasında önemli bir eğilim olduğundan, bu bölümde Docker kapsayıcıları kullanılarak bir mikrohizmet mimarisi uygulaması üzerinde duruluyor.

>[!div class="step-by-step"]
>[Önceki](../docker-application-development-process/docker-app-development-workflow.md)
>[Sonraki](microservice-application-design.md)
