---
title: ASP.NET MVC ve ASP.NET Core arasındaki test seçeneklerini karşılaştırma
description: Test ASP.NET MVC uygulamaları ve ASP.NET Core uygulamaları arasında farklılık gösterir mi?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 2821f97cf51fa5450c0cfae1287e845b6e19712d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488940"
---
# <a name="compare-testing-options-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki test seçeneklerini karşılaştırma

ASP.NET MVC Apps, denetleyicilerin birim testlerini destekler, ancak bu yaklaşım genellikle Yönlendirme, yetkilendirme, model bağlama, model doğrulama, filtreler ve daha fazlası gibi birçok MVC özelliğini atlar. Bu MVC özelliklerini denetleyici eyleminin içindeki mantığa ek olarak test etmek için, genellikle uygulamanın dağıtılması ve ardından Selenium gibi bir araçla test olması gerekir. Bu testler önemli ölçüde daha pahalı, daha Brittle ve tüm uygulamayı barındırmak ve çalıştırmak zorunda kalmadan çalıştırılabilen tipik birim testlerinden daha yavaştır.

[ASP.NET Core denetleyicileri](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing) , TıPKı ASP.NET MVC denetleyicileri gibi, ancak aynı sınırlamalara sahip birim test edilebilir. Ancak, [ASP.NET Core hızlı, kolay yazarı tümleştirme testlerini de destekler](https://docs.microsoft.com/aspnet/core/test/integration-tests) . Tümleştirme testleri bir sınıf tarafından barındırılır `TestHost` ve tipik olarak, `WebApplicationFactory` uygulama bağımlılıklarını geçersiz kılabileceğiniz veya değiştiren özel olarak yapılandırılır. Örneğin, genellikle tümleştirme testi sırasında uygulama farklı bir veri kaynağını hedefleyecek ve sahte veya sahte uygulamalarla e-posta gönderen Hizmetleri değiştirebilir.

ASP.NET MVC ve Web API ASP.NET Core ' de bulunan tümleştirme testi senaryolarına benzer bir şeyi desteklemez. Herhangi bir geçiş çabasında, beklendiği gibi çalıştığından emin olmak için yeni geçirilen sisteminiz için bazı tümleştirme testlerini yazmak üzere zaman ayırmanız gerekir ve devam edin. Taşıma işleminden önce Web uygulaması mantığınızın testlerini yazmasanız bile, ASP.NET Core ' a taşırken kesinlikle bunu yapmanız gerekir.

## <a name="references"></a>Başvurular

- [ASP.NET MVC Uygulamaları için Birim Testleri Oluşturma](https://docs.microsoft.com/aspnet/mvc/overview/older-versions-1/unit-testing/creating-unit-tests-for-asp-net-mvc-applications-cs)
- [ASP.NET Core 'de birim test denetleyicisi mantığı](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)
- [ASP.NET Core tümleştirme testleri](https://docs.microsoft.com/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
>[Önceki](signalr-differences.md) 
> [Sonraki](migrate-large-solutions.md)
