---
title: .NET için Azure SDK ile günlüğe kaydetme
description: .NET istemci kitaplıkları için Azure SDK ile oturum açmayı nasıl etkinleştirmenizi öğrenin
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071992"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>.NET için Azure SDK ile günlüğe kaydetme

.NET istemci kitaplıkları için [Azure SDK](https://azure.microsoft.com/downloads/) istemci kitaplığı işlemlerini günlüğe kaydetme özelliğini içerir. Bu, istemci kitaplıklarının Azure hizmetlerine yaptığı G/Ç isteklerini ve yanıtlarını izlemenize olanak tanır. Genellikle, günlükleri hata ayıklamak veya iletişim sorunları tanılamak için kullanılır. Bu makalede, .NET için Azure SDK ile günlüğe kaydetmeyi etkinleştirmek için üç yaklaşım açıklanmaktadır:

- Konsol penceresine giriş yap
- .NET tanılama izlemelerine giriş yapın
- Özel günlüğe kaydetmeyi yapılandır

> [!IMPORTANT]
> Bu makale, .NET için Azure SDK'nın en son sürümlerini kullanan istemci kitaplıkları için geçerlidir. Kitaplığın desteklenip desteklenmeyip desteklenmeylistesini görmek için [Azure SDK'nın son sürümleri](https://azure.github.io/azure-sdk/releases/latest/index.html)listesine bakın. Uygulamanız Azure SDK istemci kitaplıklarının eski bir sürümünü kullanıyorsa, ilgili hizmet belgelerindeki belirli talimatlara bakın.

## <a name="log-information"></a>Günlük bilgileri

SDK, kişisel verileri kaldırmak için parametre sorgusunu ve üstbilgi değerlerini temizleyerek aşağıdaki bilgileri kaydeder.

HTTP istek günlüğü girişi:

- Benzersiz Kimlik
- HTTP yöntemi
- URI
- Giden istek üstbilgi

HTTP yanıt günlüğü girişi:

- G/Ç çalışma süresi (geçen süre)
- İstek Kimliği
- HTTP durum kodu
- HTTP neden cümlesi
- Yanıt üst bilgileri
- Varsa hata bilgileri

İstek ve yanıt içeriği için:

- İçerik, İçerik Türü üstbilgisine bağlı olarak metin veya bayt olarak akış.
     > [! NOT} İçerik günlüğe kaydetme varsayılan olarak devre dışı bırakılır. Etkinleştirmek için, `Diagnostics.IsLoggingContentEnabled` `true` 'de `ClientOptions`ayarlayın.

Olay günlükleri genellikle şu üç düzeyden birinde çıkar:

- İstek ve yanıt olayları için bilgilendirme
- Hatalar için uyarı
- Ayrıntılı mesajlar ve içerik günlüğü için ayrıntılı bilgi

## <a name="enable-logging-with-built-in-methods"></a>Yerleşik yöntemlerle günlüğe kaydetmeyi etkinleştirme

.NET istemci kitaplıkları için Azure SDK, olayları .NET için tipik olan [ `EventSource` sınıf](/dotnet/api/system.diagnostics.tracing.eventsource)üzerinden Windows için Olay İzleme (ETW) olarak günlüğe kaydeder. Olay kaynakları, uygulama kodunuzda en az performans yüküyle yapılandırılmış günlüğe kaydetme yi kullanmanıza olanak sağlar. Bu etkinlik günlüklerine erişmek için etkinlik dinleyicilerini kaydetmeniz gerekir.

SDK, .NET uygulamanız için kapsamlı günlüğe kaydetmeyi basitleştiren iki statik yöntem içeren `Azure.Core.Diagnostics.AzureEventSourceListener` `CreateConsoleLogger` sınıfı `CreateTraceLogger`(Azure.Core NuGet paketinde tanımlanan) içerir: ve. Bu yöntemler, günlük düzeyini belirten isteğe bağlı bir parametre alır.

### <a name="log-to-the-console-window"></a>Konsol penceresine giriş yap

.NET istemci kitaplıkları için Azure SDK'nın temel ilkelerinden biri, kapsamlı günlükleri gerçek zamanlı olarak görüntüleme olanağını basitleştirmektir. Yöntem, `CreateConsoleLogger` tek bir kod satırı yla konsol penceresine günlük göndermenize olanak tanır:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Tanılama izlerine günlük

İzleme dinleyicileri uygularsanız, `CreateTraceLogger` standart .NET olay izleme mekanizmasına ( ).[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing) .NET'te etkinlik izleme hakkında daha fazla bilgi için [Bkz.](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners) Bu örnekte bir günlük verbose düzeyi belirtilir:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Özel günlüğe kaydetmeyi yapılandır

Yukarıda belirtildiği gibi, .NET için Azure SDK'dan günlük iletileri almak için etkinlik dinleyicilerini kaydetmeniz gerekir. Yukarıdaki basitleştirilmiş yöntemlerden birini kullanarak kapsamlı günlüğe kaydetme uygulamak istemiyorsanız, `AzureEventSourceListener` sınıfın bir örneğini oluşturup yazdığınız bir geri arama işlevini geçirebilirsiniz. Bu yöntem, istediğiniz şekilde işleyebilir günlük iletileri alır. Buna ek olarak, örneği oluştursanız, içerecek günlük düzeylerini belirtebilirsiniz.

Aşağıdaki örnek, özel bir iletiyle konsola giriş yapan ve düzey ayrıntılı Azure temel olaylarına filtrelenen bir olay dinleyicisi oluşturur.

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a>Sonraki adımlar

- [Azure Uygulama Hizmeti'ndeki uygulamalar için tanılama günlüğe kaydetmeyi etkinleştirme](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- [Azure güvenlik günlüğe kaydetme ve denetleme](https://docs.microsoft.com/azure/security/fundamentals/log-audit) seçeneklerini gözden geçirme
- [Azure platform günlükleriyle](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview) nasıl çalışacağınızı öğrenin
- [.NET Core günlük ve izleme](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing) hakkında daha fazla bilgi edinin
