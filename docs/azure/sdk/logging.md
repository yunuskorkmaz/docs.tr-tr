---
title: .NET için Azure SDK ile günlüğe kaydetme
description: .NET istemci kitaplıkları için Azure SDK ile günlüğe kaydetmeyi etkinleştirme hakkında bilgi edinin
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

.NET için [Azure SDK](https://azure.microsoft.com/downloads/) istemci kitaplıkları, istemci kitaplığı işlemlerini günlüğe kaydetme özelliğini içerir. Bu, istemci kitaplıklarının Azure hizmetlerinde yapmakta olduğu g/ç isteklerini ve yanıtlarını izlemenize olanak sağlar. Genellikle Günlükler, iletişim sorunlarını ayıklamak veya tanılamak için kullanılır. Bu makalede, .NET için Azure SDK ile günlüğe kaydetmeyi etkinleştirmek için üç yaklaşım açıklanmaktadır:

- Konsol penceresinde günlüğe kaydet
- .NET tanılama izlemelerinde günlüğe kaydet
- Özel günlüğü yapılandırma

> [!IMPORTANT]
> Bu makale, .NET için Azure SDK 'sının en son sürümlerini kullanan istemci kitaplıkları için geçerlidir. Bir kitaplığın desteklenip desteklenmediğini görmek için, [Azure SDK 'sının en son sürümleri](https://azure.github.io/azure-sdk/releases/latest/index.html)listesine bakın. Uygulamanız Azure SDK istemci kitaplıklarının eski bir sürümünü kullanıyorsa, geçerli hizmet belgelerindeki belirli yönergelere bakın.

## <a name="log-information"></a>Günlük bilgileri

SDK, kişisel verileri kaldırmak için aşağıdaki bilgileri günlüğe kaydeder, parametre sorgusunu ve üst bilgi değerlerini temizler.

HTTP istek günlüğü girişi:

- Benzersiz Kimlik
- HTTP yöntemi
- URI
- Giden istek üstbilgileri

HTTP yanıt günlüğü girişi:

- G/ç işleminin süresi (geçen süre)
- İstek Kimliği
- HTTP durum kodu
- HTTP neden tümceciği
- Yanıt üst bilgileri
- Uygun olduğunda hata bilgileri

İstek ve yanıt içeriği için:

- Content-Type üst bilgisine bağlı olarak, metin veya bayt olarak içerik akışı.
     > [! NOTE} Içerik günlüğe kaydetme varsayılan olarak devre dışıdır. Etkinleştirmek için, içinde `Diagnostics.IsLoggingContentEnabled` `true` `ClientOptions`olarak ayarlayın.

Olay günlükleri genellikle şu üç düzeyden birinde çıkış olur:

- İstek ve yanıt olayları için bilgilendirici
- Hatalar için uyarı
- Ayrıntılı iletiler ve içerik günlüğü için ayrıntılı

## <a name="enable-logging-with-built-in-methods"></a>Yerleşik yöntemlerle günlüğe kaydetmeyi etkinleştirme

.NET istemci kitaplıkları için Azure SDK, .NET için tipik olan [ `EventSource` sınıfı](/dotnet/api/system.diagnostics.tracing.eventsource)aracılığıyla Windows için olay izleme 'ye (ETW) yönelik olayları günlüğe kaydeder. Olay kaynakları, uygulama kodunuzda yapılandırılmış günlük oluşturmayı en düşük performans yüküyle kullanmanıza olanak sağlar. Bu olay günlüklerine erişim kazanmak için olay dinleyicilerini kaydetmeniz gerekir.

SDK, .NET uygulamanız `Azure.Core.Diagnostics.AzureEventSourceListener` için kapsamlı günlüğü kolaylaştıran iki statik yöntem içeren sınıfını (Azure. Core NuGet paketinde tanımlanmıştır) içerir: `CreateConsoleLogger` ve. `CreateTraceLogger` Bu yöntemler, günlük düzeyini belirten isteğe bağlı bir parametre alır.

### <a name="log-to-the-console-window"></a>Konsol penceresinde günlüğe kaydet

.NET istemci kitaplıkları için Azure SDK 'sının temel bir temel, kapsamlı günlükleri gerçek zamanlı görüntüleme özelliğini basitleştirmektir. Yöntemi `CreateConsoleLogger` , tek bir kod satırıyla günlükleri konsol penceresine göndermenizi sağlar:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Tanılama izlemelerinde günlüğe kaydet

İzleme dinleyicileri uygularsanız, standart .NET olay izleme mekanizmasına `CreateTraceLogger` ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)) oturum açmak için yöntemini kullanabilirsiniz. .NET 'teki olay izleme hakkında daha fazla bilgi için bkz. [Trace dinleyicileri](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners). Bu örnek, ayrıntılı bir günlük düzeyi belirtir:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Özel günlüğü yapılandırma

Yukarıda belirtildiği gibi, .NET için Azure SDK 'dan günlük iletilerini almak üzere olay dinleyicilerini kaydetmeniz gerekir. Yukarıdaki Basitleştirilmiş yöntemlerden birini kullanarak kapsamlı günlük uygulamak istemiyorsanız, `AzureEventSourceListener` sınıfının bir örneğini oluşturabilir ve yazdığınız bir geri çağırma işlevi geçirebilirsiniz. Bu yöntem, ihtiyacınız olan ancak yapmanız gereken günlük iletilerini alır. Ayrıca, örneği oluşturduğunuzda, dahil edilecek günlük düzeylerini de belirtebilirsiniz.

Aşağıdaki örnek, özel bir iletiyle konsola oturum açan bir olay dinleyicisi oluşturur ve ayrıntı düzeyinde Azure Core olaylarına filtrelenir.

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

- [Azure App Service uygulamalar için tanılama günlüğünü etkinleştirme](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- [Azure Güvenlik günlüğü ve denetim](https://docs.microsoft.com/azure/security/fundamentals/log-audit) seçeneklerini gözden geçirin
- [Azure platform günlükleriyle](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview) nasıl çalışacağınızı öğrenin
- [.NET Core günlüğe kaydetme ve izleme](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing) hakkında daha fazla bilgi edinin
