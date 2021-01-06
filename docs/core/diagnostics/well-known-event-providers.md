---
title: .NET 'teki iyi bilinen olay sağlayıcıları
description: .NET çalışma zamanı ve kitaplıkları tarafından yayımlanan sağlayıcıları ve olayları gözden geçirin.
ms.topic: reference
ms.date: 12/21/2020
ms.openlocfilehash: 03d505f33e300b094958676bb768fb542d828aeb
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97738206"
---
# <a name="well-known-event-providers-in-net"></a>.NET 'teki iyi bilinen olay sağlayıcıları

.NET çalışma zamanı ve kitaplıkları, çeşitli farklı olay sağlayıcıları aracılığıyla tanılama olayları yazar. Tanılama gereksinimlerinize bağlı olarak, etkinleştirilecek uygun sağlayıcıları seçebilirsiniz. Bu makalede, .NET çalışma zamanı ve kitaplıklarında en yaygın olarak kullanılan olay sağlayıcılarının bazıları açıklanmaktadır.

## <a name="coreclr"></a>CoreCLR

### <a name="microsoft-windows-dotnetruntime-provider"></a>"Microsoft-Windows-DotNETRuntime" sağlayıcısı

Bu sağlayıcı, .NET çalışma zamanının GC, yükleyici, JıT, özel durum ve diğer olaylar gibi çeşitli olaylarını yayar. [Çalışma zamanı sağlayıcısı olayları listesinde](../../fundamentals/diagnostics/runtime-events.md)Bu sağlayıcıdan her olay hakkında daha fazla bilgi edinin.

### <a name="microsoft-dotnetcore-sampleprofiler-provider"></a>"Microsoft-DotNETCore-SampleProfiler" sağlayıcısı

Bu sağlayıcı, yönetilen çağrı yığınları için CPU örnekleme için kullanılan bir .NET çalışma zamanı olay sağlayıcısıdır. Etkinleştirildiğinde, her bir iş parçacığının yönetilen çağrı yığınının bir anlık görüntüsünü her 10 milisaniyede yakalar. Bu yakalamayı etkinleştirmek için bir <xref:System.Diagnostics.Tracing.EventLevel> `Informational` veya daha fazla belirtmeniz gerekir.

## <a name="framework-libraries"></a>Framework kitaplıkları

### <a name="microsoft-extensions-dependencyinjection-provider"></a>"Microsoft-Extensions-Dependencyınjection" sağlayıcısı

Bu sağlayıcı, Dependencyınjection 'tan bilgileri günlüğe kaydeder. Aşağıdaki tabloda sağlayıcı tarafından günlüğe kaydedilen olaylar gösterilmektedir `Microsoft-Extensions-DependencyInjection` :

|Olay adı|Level|Açıklama|
|----------|-----|-----------|
|`CallSiteBuilt`|Verbose (5)|Bir çağrı sitesi oluşturuldu.|
|`ServiceResolved`|Verbose (5)|Bir hizmet çözümlendi.|
|`ExpressionTreeGenerated`|Verbose (5)|İfade ağacı oluşturuldu.|
|`DynamicMethodBuilt`|Verbose (5)|Bir oluşturuldu <xref:System.Reflection.Emit.DynamicMethod> .|

### <a name="systembuffersarraypooleventsource-provider"></a>"System. buffers. ArrayPoolEventSource" sağlayıcısı

Bu sağlayıcı, ArrayPool 'dan bilgileri günlüğe kaydeder. Aşağıdaki tabloda tarafından günlüğe kaydedilen olaylar gösterilmektedir `ArrayPoolEventSource` :

|Olay adı|Level|Açıklama|
|----------|-----|-----------|
|`BufferRented`|Verbose (5)|Bir arabellek başarıyla yeniden oluşturuldu.|
|`BufferAllocated`|Bilgilendirici (4)|Havuz tarafından bir arabellek ayrılır.|
|`BufferReturned`|Verbose (5)|Havuza bir arabellek döndürülür.|
|`BufferTrimmed`|Bilgilendirici (4)|Bellek baskısı veya eylemsizlik nedeniyle bir arabellek serbest yapılmaya çalışıldı.|
|`BufferTrimPoll`|Bilgilendirici (4)|Kırpma arabelleklerine bir denetim yapılıyor.|

### <a name="systemnethttp-provider"></a>"System .net. http" sağlayıcısı

Bu sağlayıcı, HTTP yığınından bilgileri günlüğe kaydeder. Aşağıdaki tabloda sağlayıcı tarafından günlüğe kaydedilen olaylar gösterilmektedir `System.Net.Http` :

|Olay adı|Level|Açıklama|
|----------|-----|-----------|
|RequestStart|Bilgilendirici (4)|Bir HTTP isteği başlatıldı.|
|RequestStop|Bilgilendirici (4)|Bir HTTP isteği bitti.|
|RequestFailed|Hata (2)|Bir HTTP isteği başarısız oldu.|
|Bağlantı oluşturuldu|Bilgilendirici (4)|HTTP bağlantısı oluşturuldu.|
|ConnectionClosed|Bilgilendirici (4)|Bir HTTP bağlantısı kapatıldı.|
|RequestLeftQueue|Bilgilendirici (4)|Bir HTTP isteği istek kuyruğunu bıraktı.|
|RequestHeadersStart|Bilgilendirici (4)|Üst bilgi için HTTP isteği başlatıldı.|
|RequestHeaderStop|Bilgilendirici (4)|Üst bilgi için HTTP isteği bitti.|
|RequestContentStart|Bilgilendirici (4)|İçerik için bir HTTP isteği başlatıldı.|
|RequestContentStop|Bilgilendirici (4)|İçerik için bir HTTP isteği bitti.|
|ResponseHeadersStart|Bilgilendirici (4)|Üst bilgi için HTTP yanıtı başlatıldı.|
|ResponseHeaderStop|Bilgilendirici (4)|Üst bilgi için HTTP yanıtı bitti.|
|ResponseContentStart|Bilgilendirici (4)|İçerik için bir HTTP yanıtı başlatıldı.|
|ResponseContentStop|Bilgilendirici (4)|İçerik için bir HTTP yanıtı bitti.|

### <a name="systemnetnameresolution-provider"></a>"System .net. NameResolution" sağlayıcısı

Bu sağlayıcı, etki alanı adı çözümüyle ilgili bilgileri günlüğe kaydeder. Aşağıdaki tabloda tarafından günlüğe kaydedilen olaylar gösterilmektedir `System.Net.NameResolution` :

|Olay adı|Level|Açıklama|
|----------|-----|-----------|
|`ResolutionStart`|Bilgilendirici (4)|Etki alanı adı çözümlemesi başlatıldı.|
|`ResolutionStop`|Bilgilendirici (4)|Etki alanı adı çözümlemesi bitti.|
|`ResolutionFailed`|Bilgilendirici (4)|Etki alanı adı çözümlemesi başarısız oldu.|

### <a name="systemnetsockets-provider"></a>"System .net. Sockets" sağlayıcısı

Bu sağlayıcı bilgileri öğesinden günlüğe kaydeder <xref:System.Net.Sockets.Socket> . Aşağıdaki tabloda sağlayıcı tarafından günlüğe kaydedilen olaylar gösterilmektedir `System.Net.Sockets` :

|Olay adı|Level|Açıklama|
|----------|-----|-----------|
|`ConnectStart`|Bilgilendirici (4)|Yuva bağlantısı başlatma denemesi başlatıldı.|
|`ConnectStop`|Bilgilendirici (4)|Yuva bağlantısı başlatma girişimi bitti.|
|`ConnectFailed`|Bilgilendirici (4)|Yuva bağlantısı başlatma girişimi başarısız oldu.|
|`AcceptStart`|Bilgilendirici (4)|Yuva bağlantısını kabul etme girişimi başlatıldı.|
|`AcceptStop`|Bilgilendirici (4)|Yuva bağlantısını kabul etme girişimi tamamlandı.|
|`AcceptFailed`|Bilgilendirici (4)|Yuva bağlantısını kabul etme girişimi başarısız oldu.|

### <a name="systemthreadingtaskstpleventsource-provider"></a>"System. Threading. Tasks. Tpliventsource" sağlayıcısı

Bu sağlayıcı, Görev Zamanlayıcı olayları gibi [görev paralel kitaplığı](../../standard/parallel-programming/task-parallel-library-tpl.md)üzerinde bilgileri günlüğe kaydeder. Aşağıdaki tabloda tarafından günlüğe kaydedilen olaylar gösterilmektedir `TplEventSource` :

|Olay adı|Sözcükle|Level|Açıklama|
|----------|-------|-----|-----------|
|`TaskScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|Bilgilendirici (4)|, <xref:System.Threading.Tasks.Task> Görev Zamanlayıcısına sıraya alınır.|
|`TaskStarted`|`Tasks`(`0x2`)|Bilgilendirici (4)|Bir <xref:System.Threading.Tasks.Task> yürütülmeye başlandı.|
|`TaskCompleted`|`TaskStops`(`0x40`)|Bilgilendirici (4)|Bir <xref:System.Threading.Tasks.Task> yürütme işlemi tamamlandı.|
|`TaskWaitBegin`|`TaskTransfer`(`0x1`)<br /><br />`TaskWait`(`0x2`)|Bilgilendirici (4)|Bir tamamlandığında örtük veya açık bir bekleme <xref:System.Threading.Tasks.Task> başladığında tetiklenir.|
|`TaskWaitEnd`|`Tasks`(`0x2`)|Verbose (5)|Bir tamamlama için bekleme döndüğünde harekete geçirilir <xref:System.Threading.Tasks.Task> .|
|`TaskWaitContinuationStarted`|`Tasks`(`0x2`)|Verbose (5)|İle ilişkili iş (Yöntem) `TaskWaitEnd` başlatıldığında tetiklenir.|
|`TaskWaitContinuationCompleted`|`TaskStops`(`0x40`)|Verbose (5)|İle ilişkili iş (Yöntem) tamamlandığında harekete geçirilir `TaskWaitEnd` .|
|`AwaitTaskContinuationScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|Bilgilendirici (4)|İçin zaman uyumsuz bir devamlılığı <xref:System.Threading.Tasks.Task> zamanlandığında tetiklenir.|

## <a name="aspnet-core"></a>ASP.NET Core

ASP.NET Core Ayrıca, ASP.NET Core yığınındaki sorunları tanılamanıza yardımcı olacak çeşitli olaylar sağlar.

ASP.NET Core olaylar ve bunların nasıl kullanılacağı hakkında daha fazla bilgi edinmek için bkz. [.NET Core 'Da günlüğe kaydetme ve ASP.NET Core](/aspnet/core/fundamentals/logging/).
