---
title: .NET Core 2.2 içinde yenilikler nelerdir?
description: .NET Core 2.2 içinde bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 12/04/2018
ms.openlocfilehash: 49a65dd44159e9800f7cf50a1edaa3d9e9b82e47
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677272"
---
# <a name="whats-new-in-net-core-22"></a>.NET Core 2.2 içinde yenilikler nelerdir?

.NET core 2.2 uygulama dağıtımı, çalışma zamanı Hizmetleri için olay işleme, Azure SQL veritabanları, JIT Derleyici performans ve kod ekleme yürütülmeden önce kimlik doğrulaması geliştirmeleri içerir `Main` yöntemi.

## <a name="new-deployment-mode"></a>Yeni bir dağıtım modu

Dağıtabileceğiniz .NET Core 2.2 ile başlayarak, [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde), hangi **.exe** yerine dosyaları **.dll** dosyaları. Framework bağımlı dağıtımları, framework bağımlı işlevsel olarak benzer yürütülebilir dosyalar (FDE), yine de bir paylaşılan sistem genelinde sürümünü çalıştırmak için .NET Core varlığını temel kullanır. Uygulamanızı, yalnızca kodunuzu ve üçüncü taraf bağımlılıkları içerir. Framework bağımlı dağıtımları FDEs platforma özgüdür.

Bu yeni bir dağıtım modu doğrudan çağırmadan uygulamanızı çalıştırabilir anlamına gelir. bir kitaplık yerine bir yürütülebilir dosya oluşturma, farklı avantajına sahiptir `dotnet` ilk.

## <a name="core"></a>Çekirdek

**Çalışma zamanı Hizmetleri olayları işleme**

Genellikle, GC, JIT ve iş parçacığı havuzu, bunların uygulamanızı nasıl etkilediği anlamak için gibi çalışma zamanı Hizmetleri, uygulamanızın kullanımını izlemek isteyebilirsiniz. Windows sistemlerde, bu genellikle geçerli işlem ETW olaylarını izleme tarafından gerçekleştirilir. Bu da çalışmaya devam ederken, her zaman düşük ayrıcalıklı bir ortamda veya Linux veya macOS üzerinde çalıştırıyorsanız, ETW kullanmak mümkün değildir. 

.NET Core 2.2 ile başlayarak, CoreCLR olayları artık kullanarak tüketilebilir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> sınıfı. Bu olaylar, GC, JIT, iş parçacığı havuzu ve birlikte çalışabilirlik gibi çalışma zamanı Hizmetleri davranışını açıklar. Bunlar CoreCLR ETW sağlayıcısı bir parçası olarak sunulan aynı olaylardır.  Bu olayları kullanan veya bir telemetri toplama hizmete göndermek aktarım mekanizması kullanmak uygulamalara izin verir. Aşağıdaki kod örneği olaylara abone olma görebilirsiniz:

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

Ayrıca, aşağıdaki iki özelliği .NET Core 2.2 ekler <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> ETW olayları hakkında ek bilgi sağlamak için sınıfı:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Veri

**Azure SQL veritabanlarına SqlConnection.AccessToken özelliği ile AAD kimlik doğrulaması**

.NET Core 2.2 ile başlayarak, Azure Active Directory tarafından verilen bir erişim belirteci bir Azure SQL veritabanında kimlik doğrulaması için kullanılabilir. Erişim belirteçleri desteklemek için <xref:System.Data.SqlClient.SqlConnection.AccessToken> özelliği eklendi <xref:System.Data.SqlClient.SqlConnection> sınıfı. AAD kimlik doğrulaması yararlanmak için 4.6 sürümünü System.Data.SqlClient NuGet paketini indirin. Bu özelliği kullanmak için erişim belirteci değerini kullanarak elde edebilirsiniz [.NET için Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) bulunan [ `Microsoft.IdentityModel.Clients.ActiveDirectory` ](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet paketi.

## <a name="jit-compiler-improvements"></a>JIT Derleyici iyileştirmeleri

**Katmanlı derleme Tercihli özellik kalır.**

.NET Core 2.1 içinde yeni bir derleyici teknoloji JIT derleyicisi uygulanan *katmanlı derleme*, katılım özelliği olarak. Katmanlı derleme performansı hedeftir. JIT derleyicisi tarafından gerçekleştirilen önemli görevlerinden birini ve kod yürütme en iyi duruma getiriyor. Az kullanılan kodu yolları için ancak derleyici kodu çalışma zamanı iyileştirilmemiş kod yürütmek için harcadığı daha iyileştirme daha fazla zaman harcayabilir. Katmanlı bir derleme JIT derlemesi iki aşamada sunar:

- A **ilk katman**, mümkün olan en kısa sürede kod oluşturduğu.

- A **ikinci katman**, oluşturduğu kodu sık yürütülen bu yöntemleri için en iyi duruma getirilmiş. Derleme, ikinci katman, Gelişmiş performans için paralel gerçekleştirilir.

Katmanlı derlemeden sonuçlanabilir performans geliştirmesi hakkında daha fazla bilgi için bkz: [.NET Core 2.2 Önizleme 2 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

.NET Core 2.2 Preview 2'deki katmanlı derleme varsayılan olarak etkinleştirildi. Ancak biz katmanlı derleme varsayılan olarak etkinleştirmek hala hazır değil duyuyoruz karar verdiniz. Bu nedenle .NET Core 2.2 içinde katmanlı derleme Tercihli özellik olmaya devam eder. Seçim için katmanlı derleme hakkında daha fazla bilgi için bkz: [JIT Derleyici iyileştirmeleri](dotnet-core-2-1.md#jit-compiler-improvements) içinde [.NET Core 2.1 yenilikler](dotnet-core-2-1.md).

## <a name="runtime"></a>Çalışma zamanı

**Main yöntemine yürütmeden önce kod ekleme**

.NET Core 2.2 ile başlayarak, bir uygulamanın ana yöntemi çalıştırılmadan önce kod için bir başlangıç kanca kullanabilirsiniz. Başlangıç kancaları yeniden derleyin veya uygulama dağıtmaya gerek kalmadan dağıtıldıktan sonra uygulamalarının davranışını özelleştirmek bir konak olun.

Özel yapılandırma ve potansiyel olarak gibi uygulamanın ana girdi noktası yükleme davranışını etkileyen ayarları dahil olmak üzere ilke tanımlamak için barındırma sağlayıcılarının bekliyoruz <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> davranışı. Kanca geri çağırmaları işlemek için ayarlama veya tanımlamak diğer ortam ayara bağlı davranışı için izleme veya telemetri ekleme ayarlamak için kullanılabilir. Kanca giriş noktasından ayrı, böylelikle kullanıcı kodunun değiştirilmesi gerekmez.

Bkz: [konak başlangıç kanca](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) daha fazla bilgi için.

## <a name="see-also"></a>Ayrıca bkz.

- [​.NET Core'daki Yenilikler](index.md)
- [ASP.NET Core 2.2 içinde yenilikler nelerdir?](/aspnet/core/release-notes/aspnetcore-2.2)
- [EF Core 2.2 yeni özellikler](/ef/core/what-is-new/ef-core-2.2)
