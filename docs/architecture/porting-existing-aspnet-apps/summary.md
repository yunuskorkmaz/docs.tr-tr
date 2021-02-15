---
title: Özet
description: ASP.NET MVC ve Web API 2 uygulamalarının ASP.NET Core için bir Özet ve temel kilit kümesi.
author: ardalis
ms.date: 12/16/2020
ms.openlocfilehash: 596ab8621008d1cdc16d841e8faede5f4a1fdd16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488942"
---
# <a name="summary"></a>Özet

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu kitapta, kuruluşunuzun ASP.NET Core .NET Framework üzerinde çalışan mevcut ASP.NET uygulamalarının bağlantı noktası için bir anlam verip vermeyeceğine karar vermek için gereken kaynaklar verilmiştir. .NET Core 'a geçiş yapmayı mantıklı hale getiren [önemli konular](migration-considerations.md) hakkında bilgi edindiniz ve uygulamanızın .NET Framework devam etmek için uygun olabileceği durumlar. .NET Core sürümleri ile özellikleri ve bunlarla .NET Framework uyumluluk arasında farklar vardır ve [uygulamanız için .NET Core 'un doğru sürümünü seçme hakkında](choose-net-core-version.md)daha fazla öğrenirsiniz.

Büyük bir uygulamanın taşıma işlemleri genellikle riskli bir risk ve çaba gerektirir. Kısmen geçirilmiş uygulamaları üretimde çalışan bir veya daha fazla [geliştirme stratejisiyle](deployment-strategies.md) birlikte bir veya daha fazla [artımlı geçiş stratejisi](incremental-migration-strategies.md) kullanarak bu riski hafifletmek için bilgi edindiniz.

[ASP.net ve ASP.NET Core arasında birçok mimari fark](architectural-differences.md)vardır. Bölüm 2 ' de, bu farklılıkların birçoğu ve bunların uygulamanızın geçişi ile ilgisi hakkında bilgi edindiniz. Bu bölümde, [uygulama başlatma](app-startup-differences.md) ve düşük düzeyli [Ara yazılım](middleware-modules-handlers.md) , yüksek düzey [Denetleyici](controller-differences.md) ve [Web API 'si farklılıklarına](webapi-differences.md) ve yeni özelliklere [çok daha iyi test senaryolarına](testing-differences.md)olanak tanıyan her şey ele alınmıştır.

Büyük uygulamalar genellikle birçok projeden ve paketten oluşur ve bağımlılıklar, daha kolay veya zor geçişin ne olabileceğini belirlemede büyük bir rol oynatabilir. [Bölüm 3](migrate-large-solutions.md) [, projelerin geçirileceği](identify-migration-sequence.md) ve [uygulamanızın bağımlılıklarını anlama ve güncelleştirme](understand-update-dependencies.md)sırasını tanımlamanızı sağlar. Ayrıca [, uygulamaları üretimde çalışırken geçirmeye yönelik daha](strategies-migrating-in-production.md)ayrıntılı ek stratejiler de vardır.

[Bölüm 4 ' te, gerçek bir ASP.NET MVC başvuru uygulamasının ASP.NET Core nasıl geçirildiğini gördünüz](example-migration-eshop.md). Bu bölümde, mevcut uygulamayı almak için gereken tüm değişikliklerin ayrıntılı bir dökümü ve ASP.NET Core çalıştırmak için üzerine bağlantı noktası eklenmiştir. Taşıma işlemi ve daha ayrıntılı ayrıntılarının bazıları hakkında belirli sorularınız varsa, bu işleme geri bakın.

Son olarak, [Bölüm 5 ' ın IIS 'e odaklanan ayrıntılı belirli dağıtım senaryoları](deployment-scenarios.md). Uygulamanızın genel URL 'Lerinin tutarlı tutulması sırasında ASP.NET Core sırada olan uygulamanızın parçalarını barındırmak için mevcut IIS Web sunucunuzu nasıl kullanabileceğinizi gördünüz. IIS, URL yeniden yazma ve istek yönlendirme için harika destek içerir ve bu sayede, uygulamanın sunduğu herkese açık URL 'Lerde hiçbir değişiklik yapmadan sitenizin birden fazla sürümünü farklı sunucularda barındırarak veya hatta farklı sunucularda barındırmalarını sağlar.

>[!div class="step-by-step"]
>[Önceki](deployment-scenarios.md)
