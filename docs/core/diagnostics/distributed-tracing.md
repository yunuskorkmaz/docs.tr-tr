---
title: Dağıtılmış izleme-.NET
description: .NET dağıtılmış izleme 'ye giriş.
ms.date: 03/15/2021
ms.openlocfilehash: 274a058bf9daf096958813575901e83a3976a3a4
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111120"
---
# <a name="net-distributed-tracing"></a>.NET dağıtılmış Izleme

Dağıtılmış izleme, özellikle birden çok makineye veya işleme dağılmış olabilecek uygulamalarda hataları ve performans sorunlarını yerelleştirebilmenizi sağlayan bir tanılama tekniğidir. Bu teknik, farklı uygulama bileşenleri tarafından yapılan bir uygulamayla bir araya geçen ve başka bir iş tarafından, uygulamanın eşzamanlı istekler için yapmakta olabileceği diğer çalışmalardan ayıran istekleri izler. Örneğin, tipik bir Web hizmeti isteği ilk olarak bir yük dengeleyici tarafından alınıp daha sonra bir veritabanına birkaç sorgu yapan bir Web sunucusu işlemine iletilebilirler. Dağıtılmış izlemenin kullanılması, mühendislerin herhangi birinin başarısız olup olmadığını, her adımın ne kadar sürdüğünü ve çalıştırıldığdaki her bir adımla üretilen iletileri günlüğe kaydetmeyi ayırt etmesine olanak tanır.

## <a name="getting-started-for-net-app-developers"></a>.NET uygulama geliştiricileri için Başlarken

Anahtar .NET kitaplıkları, dağıtılmış izleme bilgilerini otomatik olarak oluşturmak üzere işaretlenir, ancak daha sonra gözden geçirilmek üzere kullanılabilmesi için bu bilgilerin toplanması ve depolanması gerekir.
Genellikle uygulama geliştiricileri, bu izleme bilgilerini depolayan bir telemetri hizmeti seçer ve ardından dağıtılmış izleme telemetrisini seçili hizmetine aktarmak için karşılık gelen bir kitaplığı kullanır. [Opentelemetri](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/docs/trace/getting-started/README.md) , Microsoft tarafından sunulan tam özellikli bir hizmettir [Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/distributed-tracing) , Microsoft tarafından sunulan tam özellikli bir hizmettir ve tümleşik .NET çözümleri sunan çok sayıda yüksek kaliteli üçüncü taraf APM satıcısı vardır.

- [Dağıtılmış izleme kavramlarını anlama](distributed-tracing-concepts.md)
- Guides
  - [Application Insights ile dağıtılmış izlemeler toplayın](distributed-tracing-collection-walkthroughs.md#collect-traces-using-application-insights)
  - [Opentelemetri ile dağıtılmış izlemeler toplayın](distributed-tracing-collection-walkthroughs.md#collect-traces-using-opentelemetry)
  - [Özel mantık ile dağıtılmış izlemeler toplayın](distributed-tracing-collection-walkthroughs.md#collect-traces-using-custom-logic)
  - [Özel dağıtılmış izleme araçları ekleme](distributed-tracing-instrumentation-walkthroughs.md)

3. taraf telemetri toplama Hizmetleri için satıcı tarafından sunulan kurulum yönergelerini izleyin.

## <a name="getting-started-for-net-library-developers"></a>.NET kitaplığı geliştiricileri için Başlarken

.NET kitaplıklarının, yalnızca nasıl üretileleceği ile ilgili telemetri sonunda nasıl toplandığı konusunda endişe duymasına gerek yoktur. Kitaplığınızı kullanan .NET uygulama geliştiricilerinin, dağıtılmış bir izlemede ayrıntılı bir şekilde çalıştığını düşündüğünü düşünüyorsanız, bunu desteklemek için dağıtılmış izleme araçları eklemeniz gerekir.

- [Dağıtılmış izleme kavramlarını anlama](distributed-tracing-concepts.md)
- Guides
  - [Özel dağıtılmış izleme araçları ekleme](distributed-tracing-instrumentation-walkthroughs.md)
