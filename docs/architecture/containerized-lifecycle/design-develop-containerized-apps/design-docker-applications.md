---
title: Docker uygulamaları tasarlama
description: Bu kılavuzda ayrıntılı olmadığından, mikro hizmetler mimarisine yönelik derinlemesine bir kılavuza yönelik bir başvuru bulabilirsiniz.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295865"
---
# <a name="design-docker-applications"></a>Docker uygulamaları tasarlama

Bölüm 1, kapsayıcılar ve Docker ile ilgili temel kavramları sunmuştur. Bu bilgiler, başlamak için ihtiyacınız olan temel bilgi düzeyidir. Ancak kurumsal uygulamalar, tek bir hizmet veya kapsayıcı yerine karmaşık ve birden çok hizmetten oluşabilir. Bu isteğe bağlı kullanım örnekleri için, hizmet odaklı mimari (SOA) ve daha gelişmiş mikro hizmet kavramları ve kapsayıcı düzenleme kavramları gibi tasarıma yönelik ek yaklaşımlar bilmeniz gerekir. Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak herhangi bir Docker uygulaması yaşam döngüsü için, normal SOA, arka plan görevleri veya işleri ile kapsayıcılar ve Docker 'ı da kullanabileceğiniz veya hatta tek parçalı uygulama dağıtımı yaklaşımının bulunduğu.

**Daha fazla bilgi** Kurumsal uygulamalar ve mikro hizmetler mimarisi hakkında daha fazla bilgi edinmek için ağ mikro Hizmetleri Kılavuzu [' nu okuyun: ](../../microservices/index.md) İçinden<https://aka.ms/MicroservicesEbook>de indirebileceğiniz Kapsayıcılı .NET uygulamaları için mimari.

Bununla birlikte, uygulama yaşam döngüsü ve DevOps 'a girmeden önce, uygulamanızı nasıl tasarlayacağınızı ve tasarlayacağınızı ve tasarım seçimleriniz olduğunu bilmeniz önemlidir.

>[!div class="step-by-step"]
>[Önceki](index.md)İleri
>[](common-container-design-principles.md)
