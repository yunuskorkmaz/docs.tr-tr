---
title: ​.NET Core 2.2’deki yenilikler
description: .NET Core 2,2 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: 656ef9aa2745c935c37b69ae5a54b8d126700e55
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608296"
---
# <a name="whats-new-in-net-core-22"></a>​.NET Core 2.2’deki yenilikler

.NET Core 2,2, uygulama dağıtımında geliştirmeler, çalışma zamanı Hizmetleri için olay işleme, Azure SQL veritabanlarına yönelik kimlik doğrulaması, JıT derleyicisi performansı ve yöntemin yürütülmesinden önce kod ekleme işlemlerini içerir `Main` .

## <a name="new-deployment-mode"></a>Yeni dağıtım modu

.NET Core 2,2 ile başlayarak,. **DLL** dosyaları yerine **. exe** dosyaları olan [çerçeveye bağımlı yürütülebilir](../deploying/index.md#publish-framework-dependent)dosyaları dağıtabilirsiniz. İşleve bağımlı dağıtımlara benzer şekilde, çerçeveye bağımlı yürütülebilir dosyalar (FDE), .NET Core 'un paylaşılan sistem genelindeki bir sürümünün çalışmasına de dayanmaktadır. Uygulamanız yalnızca kendi kodunuzu ve üçüncü taraf bağımlılıklarını içerir. Çerçeveye bağımlı dağıtımlardan farklı olarak, FDEs platforma özgüdür.

Bu yeni dağıtım modu, bir kitaplık yerine yürütülebilir bir dosya oluşturmanın farklı avantajına sahiptir. Bu, uygulamanızı önce çağırmadan doğrudan çalıştırabilmeniz anlamına gelir `dotnet` .

## <a name="core"></a>Çekirdek

**Çalışma zamanı hizmetlerindeki olayları işleme**

Uygulamanızı nasıl etkileyeceğini anlamak için, uygulamanızın GC, JıT ve ThreadPool gibi çalışma zamanı hizmetlerinin kullanımını izlemek isteyebilirsiniz.Windows sistemlerinde, bu genellikle geçerli işlemin ETW olayları izlenerek yapılır.Bu, sorunsuz çalışmaya devam ederken, düşük ayrıcalıklı bir ortamda veya Linux veya macOS 'ta çalışıyorsanız ETW 'yi kullanmak her zaman mümkün değildir.

.NET Core 2,2 ile başlayarak CoreCLR olayları artık sınıfı kullanılarak tüketilebilir <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> . Bu olaylar, bu tür çalışma zamanı hizmetlerinin GC, JıT, ThreadPool ve birlikte çalışma olarak davranışını anlatmaktadır. Bunlar CoreCLR ETW sağlayıcısı 'nın bir parçası olarak sunulan olaylardır.Bu, uygulamaların bu olayları kullanmasına veya bir telemetri toplama hizmetine göndermek için bir taşıma mekanizması kullanmasına izin verir. Aşağıdaki kod örneğinde olaylara nasıl abone olunacağına bakabilirsiniz:

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

Ayrıca, .NET Core 2,2, <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> ETW olayları hakkında ek bilgi sağlamak üzere sınıfına aşağıdaki iki özelliği ekler:

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a>Veriler

**SqlConnection. AccessToken özelliği ile Azure SQL veritabanlarında AAD kimlik doğrulaması**

.NET Core 2,2 ile başlayarak, Azure Active Directory tarafından verilen bir erişim belirteci, bir Azure SQL veritabanında kimlik doğrulaması yapmak için kullanılabilir. Erişim belirteçlerini desteklemek için, <xref:System.Data.SqlClient.SqlConnection.AccessToken> özelliği <xref:System.Data.SqlClient.SqlConnection> sınıfına eklenmiştir. AAD kimlik doğrulamasının avantajlarından yararlanmak için System. Data. SqlClient NuGet paketinin 4,6 sürümünü indirin. Özelliğini kullanabilmeniz için, NuGet paketinde bulunan [.NET için Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) erişim belirteci değerini elde edebilirsiniz [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) .

## <a name="jit-compiler-improvements"></a>JıT derleyicisi geliştirmeleri

**Katmanlı derleme bir katılım özelliği kalır**

.NET Core 2,1 ' de JıT derleyicisi, bir katılım özelliği olarak yeni bir derleyici teknolojisi, *katmanlı derleme*uyguladık. Katmanlı derlemenin amacı performansı artırmaktır. JıT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri, kod yürütmeyi iyileştiriliyor. Ancak, daha az kullanılan kod yolları için, derleyici en iyi duruma getirilmiş kodu yürütme çalışma zamanından daha fazla zaman harcayabilir. Katmanlı derleme JıT derlemesinde iki aşama sunar:

- Mümkün olduğunca hızlı bir şekilde kod üreten **ilk katman**.

- Sık çalıştırılan yöntemler için iyileştirilmiş kod üreten **ikinci bir katman**. İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.

Katmanlı derlemeden kaynaklanan performans iyileştirmesi hakkında daha fazla bilgi için bkz. [.NET Core 2,2 Preview 2 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).

.NET Core 2,2 Preview 2 ' de katmanlı derleme varsayılan olarak etkinleştirilmiştir. Ancak, varsayılan olarak katmanlı derlemeyi etkinleştirmeye hazır olmaya devam ediyoruz. Bu nedenle, .NET Core 2,2 ' de katmanlı derleme bir kabul etme özelliği olmaya devam eder. Katmanlı derleme ile ilgili daha fazla bilgi için bkz. [.NET Core 2,1 'deki](dotnet-core-2-1.md)Yenilikler bölümünde [JIT derleyicisi geliştirmeleri](dotnet-core-2-1.md#jit-compiler-improvements) .

## <a name="runtime"></a>Çalışma Zamanı

**Ana yöntemi yürütmeden önce ekleme kodu**

.NET Core 2,2 ile başlayarak, bir uygulamanın ana metodunu çalıştırmadan önce kodu eklemek için bir başlangıç kancası kullanabilirsiniz. Başlangıç kancaları, bir konağın uygulamayı yeniden derlemenize veya değiştirmeye gerek kalmadan dağıtıldıktan sonra uygulamaların davranışını özelleştirmesini olanaklı kılar.

Barındırma sağlayıcılarının, davranış gibi ana giriş noktasının yükleme davranışını etkileyebilecek ayarlar da dahil olmak üzere, özel yapılandırma ve ilke tanımlamasını bekledik  <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType>   . Kanca, izleme veya telemetri ekleme, işleme için geri çağırmaları ayarlama veya ortama bağlı diğer davranışı tanımlama amacıyla kullanılabilir. Kanca giriş noktasından ayrıdır, bu sayede kullanıcı kodunun değiştirilmesi gerekmez.

Daha fazla bilgi için bkz. [konak başlangıç kancası](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [​.NET Core 3.1’deki yenilikler](dotnet-core-3-1.md)
- [ASP.NET Core 2,2 ' deki yenilikler](/aspnet/core/release-notes/aspnetcore-2.2)
- [EF Core 2,2 ' deki yeni özellikler](/ef/core/what-is-new/ef-core-2.2)
