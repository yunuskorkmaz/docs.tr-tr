---
title: SOA uygulamaları
description: Ayrıca kapsayıcının SOA uygulamaları için yararlı bir dağıtım seçeneği olabileceğini göz önünde bulundurun.
ms.date: 08/06/2020
ms.openlocfilehash: 5cc616eaf3be31ae704320df6ec54deed9529989
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915255"
---
# <a name="service-oriented-applications"></a>Hizmet odaklı uygulamalar

Hizmet odaklı mimari (SOA), farklı kişilere çok sayıda farklı şeyler sunan aşırı kullanılan bir terimdir. Ancak, ortak paydalar olarak, SOA, alt sistemler gibi farklı türlerde sınıflandırılabilen çeşitli hizmetlere (genellikle HTTP Hizmetleri) veya başka durumlarda Katmanlar olarak sınıflandırılabilen uygulamanızın mimarisini yapılandırabilmeniz anlamına gelir.

Bugün, bu hizmetleri, dağıtım ile ilgili sorunları çözerek, tüm bağımlılıkların kapsayıcı görüntüsüne dahil olduğu için bu hizmetleri Docker Kapsayıcıları olarak dağıtabilirsiniz. Ancak, SOAs 'yi ölçeklendirmeniz gerektiğinde, tek örneklere dayalı dağıtım yapıyorsanız sorunlarla karşılaşabilirsiniz. Bu zorluk, Docker kümeleme yazılımı veya Orchestrator kullanılarak işlenebilir. Mikro hizmet yaklaşımlarını araştırdığınızda, sonraki bölümde bulunan düzenlemeleri daha ayrıntılı bir şekilde gözden geçirin.

Docker Kapsayıcıları hem geleneksel hizmet yönelimli mimariler hem de daha gelişmiş mikro hizmet mimarileri için yararlıdır (ancak gerekli değildir).

Günün sonunda, kapsayıcı kümeleme çözümleri hem geleneksel bir SOA mimarisi hem de her bir mikro hizmetin veri modeline sahip olduğu daha gelişmiş bir mikro hizmet mimarisi için yararlıdır. Ayrıca, birden çok veritabanı sayesinde, SOA Hizmetleri tarafından paylaşılan tek parçalı veritabanları ile çalışmak yerine veri katmanını da genişletebilirsiniz. Bununla birlikte, verileri bölmek hakkında tartışma yalnızca mimari ve tasarım ile ilgilidir.

>[!div class="step-by-step"]
>[Önceki](state-and-data-in-docker-applications.md) 
> [Sonraki](orchestrate-high-scalability-availability.md)
