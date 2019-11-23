---
title: SOA uygulamaları
description: Ayrıca kapsayıcının SOA uygulamaları için yararlı bir dağıtım seçeneği olabileceğini göz önünde bulundurun.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295275"
---
# <a name="service-oriented-applications"></a>Hizmet odaklı uygulamalar

Hizmet odaklı mimari (SOA), farklı kişilere çok sayıda farklı şeyler sunan aşırı kullanılan bir terimdir. Ancak, ortak paydalar olarak, SOA, alt sistemler gibi farklı türlerde sınıflandırılabilen çeşitli hizmetlere (genellikle HTTP Hizmetleri) veya başka durumlarda Katmanlar olarak sınıflandırılabilen uygulamanızın mimarisini yapılandırabilmeniz anlamına gelir.

Bugün, bu hizmetleri, dağıtım ile ilgili sorunları çözerek, tüm bağımlılıkların kapsayıcı görüntüsüne dahil olduğu için bu hizmetleri Docker Kapsayıcıları olarak dağıtabilirsiniz. Ancak, SOAs 'yi ölçeklendirmeniz gerektiğinde, tek örneklere dayalı dağıtım yapıyorsanız sorunlarla karşılaşabilirsiniz. Bu zorluk, Docker kümeleme yazılımı veya Orchestrator kullanılarak işlenebilir. Mikro hizmetler yaklaşımlarını araştırtığımızda, sonraki bölümde daha ayrıntılı bir şekilde düzenlemeler yapacağız.

Docker Kapsayıcıları hem geleneksel hizmet yönelimli mimariler hem de daha gelişmiş mikro hizmet mimarileri için yararlıdır (ancak gerekli değildir).

Günün sonunda, kapsayıcı kümeleme çözümleri hem geleneksel bir SOA mimarisi hem de her bir mikro hizmetin veri modeline sahip olduğu daha gelişmiş bir mikro hizmet mimarisi için yararlıdır. Ayrıca, birden çok veritabanı sayesinde, SOA Hizmetleri tarafından paylaşılan tek parçalı veritabanları ile çalışmak yerine veri katmanını da ölçeklendirebilirsiniz. Bununla birlikte, verileri bölmek hakkında tartışma yalnızca mimari ve tasarım ile ilgilidir.

>[!div class="step-by-step"]
>[Önceki](state-and-data-in-docker-applications.md)
>[İleri](orchestrate-high-scalability-availability.md)
