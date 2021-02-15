---
title: ASP.NET MVC ve ASP.NET Core arasındaki günlük farklılıkları
description: ASP.NET MVC ve Web API uygulamaları ile ASP.NET Core uygulamalar arasında nasıl farklı günlüğe kaydedilir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: a364f761699428967b7c7b79d3f9e5103a59da14
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488882"
---
# <a name="logging-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki günlük farklılıkları

Uygulama günlüğü, özellikle üretimde çalışan uygulamalar için önemli tanılama bilgileri sağlar. ASP.NET Core, herhangi bir uygulamaya standartlaştırılmış günlük kaydı eklemek için yeni bir sistem sunar. Mevcut ASP.NET MVC ve Web API Apps, büyük olasılıkla ASP.NET Core ' de desteklenmeye devam eden üçüncü taraf günlük çözümlerini kullanır.

## <a name="aspnet-mvc-logging"></a>ASP.NET MVC günlüğü

ASP.NET MVC ve Web API uygulamalarında yerleşik günlük çözümü yoktur. Bunun yerine, çoğu uygulama [Log4net](https://www.nuget.org/packages/log4net/), [NLog](https://www.nuget.org/packages/NLog/)veya [Serilog](https://www.nuget.org/packages/Serilog)gibi üçüncü taraf günlük çözümlerini kullanır. Birçok ekip, kendi günlük çözümünü almayı da tercih edebilirsiniz. Günlüğe kaydetme çerçeveleri genellikle metin dosyaları, veritabanları veya hatta e-postalar gibi günlük çıktıları için birden çok "havuzları" (veya hedefleri veya uygulama) destekler. Bunlar, sistemin bölümlerinin farklı bir havuza yönlendirildiğini öğrenmek için yapılandırma kullanır. Uygulamanın günlüğe kaydetme işleminin .NET Core 'a nasıl geçirileceğiyle, uygulamanın nasıl gerçekleştirileceğini ve uygulamada nasıl [yapılandırıldığını](configuration-differences.md) gözden geçirin.

## <a name="aspnet-core-logging"></a>Günlüğe kaydetme ASP.NET Core

ASP.NET Core, günlüğe kaydetme, uygulama başladığında yapılandırılabilen ve genişletilebilen [yerleşik bir özelliktir](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) . Yukarıda bahsedilen gibi üçüncü taraf Günlükçüler, işlevselliğini geliştirmek için ASP.NET Core ile tümleştirilebilir.

ASP.NET Core günlüğü, günlüğe kaydedilen ve nasıl olduğunu denetlemek için kategorileri ve düzeyleri kullanır. Sınıflar genellikle `ILogger<T>` , sınıfının genel tür olarak kullanılan türü ile arabirimin örneklerini kullanır `T` . Bu senaryoda, sınıf tam adı kategori olarak kullanılır. Günlükçüler, kullanılarak özel bir kategori ile de oluşturulabilir `ILoggerFactory` . Günlük düzeyleri en ayrıntılı, `Trace` en önemlik, en önemlik aralığıdır `Critical` . Yapılandırma kullanarak, uygulamalar kategori başına en az sayıda günlüğe kaydetme (joker karakter) temelinde ne tür bir günlük ekleneceğini belirtebilir.

Tipik bir günlüğe kaydetme yapılandırması `Information` , varsayılan olarak, yalnızca veya üzeri ön eki `Warning` eklenmiş kategoriler ile bilgileri günlüğe ve yukarıya kaydeder `Microsoft` :

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning"
    }
  }
}
```

ASP.NET Core oturum açma desteği kapsamlı ve esnektir. Daha ayrıntılı bilgi için [belgelere bakın](https://docs.microsoft.com/aspnet/core/fundamentals/logging/).

## <a name="migrate-logging"></a>Günlüğe kaydetmeyi geçir

.NET Framework uygulamanızın günlüğünü .NET Core 'a nasıl geçirebileceğiniz, uygulamanın nasıl günlüğe kaydedilmesine bağlıdır. Üçüncü taraf bir NuGet paketi kullanıyorsa, bu paket için yükseltme belgelerine bakın. Büyük olasılıkla yükseltme yolu oldukça basittir. Kendi günlük çözümünüzü kullanıyorsanız aşağıdaki eylemlerden birini gerçekleştirin:

1. Günlüğe kaydetme çözümünü kendiniz geçirin
1. Üçüncü taraf günlük çözümüne geçiş
1. ASP.NET Core yerleşik günlük desteğini kullanın

`Microsoft.Extensions.Logging`.NET Framework, NuGet 4,3 veya üzeri bir sürümü kullandıkları ve .NET Framework 4.6.1 veya sonraki bir sürümde olduğu sürece pakete başvurabilirsiniz. Uygulamanız bu pakete başvurulduktan sonra, uygulamayı .NET Core 'a geçirmeden önce, günlük deyimlerinizi yeni uzantıları kullanacak şekilde dönüştürebilirsiniz. Bu, uygulama daha yeni uzantılar paketini kullanarak günlüğe kaydetme sırasında .NET Framework çalışmaya devam edebileceği için tam geçişe doğru bir atlama taşı sağlayabilir.

## <a name="references"></a>Başvurular

- [.NET Core ve ASP.NET Core'da günlük](https://docs.microsoft.com/aspnet/core/fundamentals/logging/)
- [Microsoft. Extensions. günlük NuGet paketi](https://www.nuget.org/packages/microsoft.extensions.logging/)

>[!div class="step-by-step"]
>[Önceki](middleware-modules-handlers.md) 
> [Sonraki](routing-differences.md)
