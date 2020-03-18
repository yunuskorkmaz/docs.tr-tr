---
title: ​.NET Core 2.2’deki yenilikler
description: .NET Core 2.2'de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156588"
---
# <a name="whats-new-in-net-core-22"></a>​.NET Core 2.2’deki yenilikler

.NET Core 2.2 uygulama dağıtımında geliştirmeler, çalışma zamanı hizmetleri için olay işleme, Azure SQL veritabanlarına kimlik doğrulama, `Main` JIT derleyici performansı ve yöntemin yürütülmesinden önce kod enjeksiyonu içerir.

## <a name="new-deployment-mode"></a>Yeni dağıtım modu

.NET Core 2.2 ile başlayarak, **.dll** dosyaları yerine **.exe** dosyaları olan [çerçeveye bağımlı yürütülebilir öğeleri](../deploying/index.md#publish-runtime-dependent)dağıtabilirsiniz. İşlevsel olarak çerçeveye bağımlı dağıtımlara benzer şekilde, çerçeveye bağımlı yürütülebilir (FDE) hala .NET Core'un çalıştırılacak ortak sistem genelindeki sürümünün varlığına güvenir. Uygulamanız yalnızca kodunuzu ve üçüncü taraf bağımlılıklarını içerir. Çerçeveye bağımlı dağıtımların aksine, FD'ler platforma özgüdür.

Bu yeni dağıtım modu, kitaplık yerine çalıştırılabilir bir uygulama oluşturmanın belirgin avantajına sahiptir, bu da uygulamanızı ilk önce aramadan `dotnet` doğrudan çalıştırabileceğiniz anlamına gelir.

## <a name="core"></a>Çekirdek

**Çalışma zamanı hizmetlerinde olayları işleme**

Uygulamanızı nasıl etkilediğini anlamak için uygulamanızın GC, JIT ve ThreadPool gibi çalışma zamanı hizmetlerini kullanımını sık sık izlemek isteyebilirsiniz.Windows sistemlerinde, bu genellikle geçerli işlemin ETW olayları izleyerek yapılır.Bu durum iyi çalışmaya devam etse de, düşük ayrıcalıklı bir ortamda veya Linux veya macOS'ta çalışıyorsanız ETW'yi kullanmak her zaman mümkün değildir.

.NET Core 2.2 ile başlayarak, CoreCLR <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> olayları artık sınıf kullanılarak tüketilebilir. Bu olaylar GC, JIT, ThreadPool ve interop gibi runtime hizmetlerinin davranışını açıklar. Bunlar CoreCLR ETW sağlayıcısının bir parçası olarak ortaya çıkan aynı olaylardır.Bu, uygulamaların bu olayları tüketmesine veya bunları bir telemetri toplama hizmetine göndermek için bir aktarım mekanizması kullanmasına olanak tanır. Aşağıdaki kod örneğinde olaylara nasıl abone olunur görebilirsiniz:

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

Buna ek olarak, .NET Core 2.2, <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> ETW olayları hakkında ek bilgi sağlamak için sınıfa aşağıdaki iki özelliği ekler:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Veriler

**SqlConnection.AccessToken özelliğine sahip Azure SQL veritabanlarına AAD kimlik doğrulaması**

.NET Core 2.2 ile başlayarak, Azure Active Directory tarafından verilen bir erişim belirteci, bir Azure SQL veritabanına kimlik doğrulamak için kullanılabilir. Erişim belirteçlerini desteklemek <xref:System.Data.SqlClient.SqlConnection.AccessToken> için özellik sınıfa <xref:System.Data.SqlClient.SqlConnection> eklendi. AAD kimlik doğrulamadan yararlanmak için System.Data.SqlClient NuGet paketinin 4.6 sürümünü indirin. Özelliği kullanmak için, [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet paketinde yer alan [.NET için Active Directory Authentication Library'yi](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) kullanarak erişim belirteci değerini elde edebilirsiniz.

## <a name="jit-compiler-improvements"></a>JIT derleyici geliştirmeleri

**Katmanlı derleme bir opt-in özelliği olmaya devam ediyor**

.NET Core 2.1'de, JIT derleyicisi yeni bir derleyici teknolojisi uyguladı, *katmanlı derleme*, bir opt-in özelliği olarak. Katmanlı derlemenin amacı geliştirilmiş performanstır. JIT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri kod yürütmeyi en iyi duruma getirmektir. Ancak az kullanılan kod yolları için derleyici, en iyi duruma getirilmemiş kodu yürütme için çalışma süresiharcadığından daha fazla zaman geçirebilir. Katmanlı derleme JIT derlemesinde iki aşama yı tanıtır:

- Kodu mümkün olduğunca çabuk üreten **birinci katman.**

- Sık sık yürütülen bu yöntemler için en iyi duruma getirilmiş kod üreten ikinci bir **katman.** İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.

Katmanlı derlemeden kaynaklanabilecek performans iyileştirmesi hakkında bilgi [için](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/)bkz.

.NET Core 2.2 Preview 2'de katmanlı derleme varsayılan olarak etkinleştirildi. Ancak, varsayılan olarak katmanlı derlemeyi etkinleştirmeye hala hazır olmadığımıza karar verdik. Yani .NET Core 2.2'de katmanlı derleme bir tercih özelliği olmaya devam ediyor. Katmanlı derlemeyi seçme hakkında daha fazla bilgi için [,.NET Core 2.1'deki yeniliklerdeki](dotnet-core-2-1.md) [Jit derleyici geliştirmelerine](dotnet-core-2-1.md#jit-compiler-improvements) bakın.

## <a name="runtime"></a>Çalışma Zamanı

**Ana yöntemi yürütmeden önce kod enjekte etme**

.NET Core 2.2 ile başlayarak, bir uygulamanın Ana yöntemini çalıştırmadan önce kod enjekte etmek için bir başlangıç kancası kullanabilirsiniz. Başlangıç kancaları, bir ana bilgisayar için uygulamayı yeniden derlemeye veya değiştirmeye gerek kalmadan dağıtıldıktan sonra uygulamaların davranışını özelleştirmesini mümkün kılar.

Barındırma sağlayıcılarının, ana giriş noktasının yük davranışını etkileyebilecek davranışlar da dahil olmak üzere <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> özel yapılandırma ve ilke tanımlamasını bekliyoruz. Kanca, izleme veya telemetri enjeksiyonu kurmak, kullanım için geri aramalar ayarlamak veya çevreye bağlı diğer davranışları tanımlamak için kullanılabilir. Kanca giriş noktasından ayrıdır, böylece kullanıcı kodunun değiştirilmesi gerekmez.

Daha fazla bilgi için [Ana Bilgisayar başlatma kancası'na](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [​.NET Core'daki Yenilikler](index.md)
- [ASP.NET Core 2.2'deki yenilikler](/aspnet/core/release-notes/aspnetcore-2.2)
- [EF Core 2.2'deki yeni özellikler](/ef/core/what-is-new/ef-core-2.2)
