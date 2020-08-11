---
title: Durum yönetimi
description: ASP.NET Web Forms ve Blazor ' de durum yönetimi için farklı yaklaşımlar öğrenin.
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: bac2f00330113725f09259ca31bdf857a8769f24
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062347"
---
# <a name="state-management"></a>Durum yönetimi

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Durum yönetimi, Görünüm durumu, oturum durumu, uygulama durumu ve geri gönderme özellikleri aracılığıyla kolaylaştırlanan Web Forms uygulamalar temel kavramıdır. Framework 'ün durum bilgisi olan bu özellikleri, bir uygulama için gereken durum yönetimini gizlemeyi ve uygulama geliştiricilerinin işlevlerini sunmaya odaklanmasını sağlar. ASP.NET Core ve Blazor ile bu özelliklerden bazıları yeniden konumlandırıldı ve bazıları tamamen kaldırılmıştır. Bu bölümde, Blazor sürümündeki yeni özelliklerle durumu koruma ve aynı işlevselliği sunma hakkında inceleme yapılır.

## <a name="request-state-management-with-viewstate"></a>ViewState ile durum yönetimi isteme

Web Forms uygulamasında durum yönetimi tartışırken birçok geliştirici, ViewState 'in hemen önünde bulunduracaktır. Web Forms, ViewState, tarayıcıda büyük bir kodlanmış metin bloğu göndererek HTTP istekleri arasındaki içeriğin durumunu yönetir. Görünüm durumu alanı, büyük olasılıkla çok sayıda öğe içeren bir sayfadan içerik ile fazla olabilir, bu da boyutu çok fazla olacak şekilde genişletiliyor.

Blazor sunucusu ile, Uygulama sunucuyla devam eden bir bağlantı sağlar. Bağlantı etkin kabul edildiğinde uygulamanın, *devre*olarak adlandırılan durumu sunucu belleğinde tutulur. Durum yalnızca Kullanıcı uygulamadan veya uygulamadaki belirli bir sayfadan uzaklaştığında bırakılacak. Etkin bileşenlerin tüm üyeleri, sunucusuyla etkileşimler arasında kullanılabilir.

Bu özelliğin çeşitli avantajları vardır:

- Bileşen durumu hazır ve etkileşimler arasında yeniden derlenmiyor.
- Durum tarayıcıya aktarılmaz.

Ancak, bellek içi bileşen durumu kalıcılığının farkında olması için bazı dezavantajları vardır:

- Sunucu istek arasında yeniden başlatılırsa durum kaybedilir.
- Uygulama Web sunucusu yük dengeleme çözümünüz aynı tarayıcıdan gelen tüm isteklerin aynı sunucuya dönmesini sağlamak için yapışkan oturumlar içermelidir. Bir istek farklı bir sunucuya gittiğinde, durum kaybedilir.
- Sunucu üzerindeki bileşen durumunun kalıcılığı Web sunucusunda bellek baskısı oluşmasına neden olabilir.

Önceki nedenlerden dolayı, sunucuda bellek içi olarak bulunan yalnızca bileşenin durumuna güvenmeyin. Uygulamanız Ayrıca istekler arasında veri için bazı yedekleme veri depolama alanı içermelidir. Bu stratejinin bazı basit örnekleri:

- Bir alışveriş sepeti uygulamasında, bir veritabanı kaydındaki sepete eklenen yeni öğelerin içeriğini kalıcı hale getirin. Sunucu üzerindeki durum kaybolursa, bunu veritabanı kayıtlarından edilmeyen yapabilirsiniz.
- Çok parçalı bir Web formunda kullanıcılarınız, uygulamanızın her istek arasındaki değerleri anımsamasını bekler. Birden çok parçalı form tamamlandığında son form yanıt yapısına getirilmeleri ve bunları birleştirmek için bir veri deposuna her bir Kullanıcı gönderilerinin her biri arasındaki verileri yazın.

Blazor uygulamalarında durumu yönetme hakkında daha fazla bilgi için bkz. [ASP.NET Core Blazor State Management](/aspnet/core/blazor/state-management).

## <a name="maintain-state-with-session"></a>Oturumla durumu koru

Web Forms geliştiriciler, şu anda sözlük nesnesi ile hareket eden kullanıcı hakkındaki bilgileri koruyabilir <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> . Öğesine dize anahtarı olan bir nesne eklemek çok kolay `Session` ve bu nesne, kullanıcının uygulamayla etkileşimi sırasında daha sonra kullanılabilir hale gelir. HTTP ile etkileşim kurmayı ortadan kaldırmaya çalıştığınızda, `Session` nesne durumu korumayı kolay hale yaptı.

.NET Framework nesnesinin imzası, `Session` ASP.NET Core nesnesiyle aynı değil `Session` . Yeni oturum durumu özelliğini geçirmeye ve kullanmaya karar vermeden önce [yeni ASP.NET Core oturumunun belgelerini](/dotnet/api/microsoft.aspnetcore.http.isession) göz önünde bulundurun.

Oturum ASP.NET Core ve Blazor Server 'da kullanılabilir, ancak veri deposundaki verileri uygun şekilde depolamanın kullanılması önerilmez. Ziyaretçiler gizlilik kaygıları nedeniyle uygulamanızda HTTP tanımlama bilgilerini kullan ' ın reddetmesi durumunda oturum durumu da işlevsel değildir.

ASP.NET Core ve oturum durumu yapılandırması, [ASP.NET Core makalesinde oturum ve durum yönetimi](/aspnet/core/fundamentals/app-state#session-state)' nde kullanılabilir.

## <a name="application-state"></a>Uygulama durumu

`Application`Web Forms çerçevesindeki nesne, uygulama kapsamı yapılandırması ve durumuyla etkileşim kurmak için büyük ve çapraz istek içeren bir depo sağlar. Uygulama durumu, isteği yapan Kullanıcı ne olursa olsun, tüm istekler tarafından başvurulacak çeşitli uygulama yapılandırma özelliklerini depolamak için ideal bir yerdir. Nesneyle ilgili sorun, `Application` verilerin birden çok sunucu arasında kalıcı olmadığı oldu. Uygulama nesnesinin durumu, yeniden başlatmalar arasında kayboldu.

' De olduğu gibi `Session` , verilerin birden çok sunucu örneği tarafından erişilebilen kalıcı bir yedekleme deposuna taşınması önerilir. İstekler ve kullanıcılara erişebilmek istediğiniz geçici veriler varsa, bu bilgileri veya etkileşimi gerektiren bileşenlere eklenebilen bir tek hizmette kolayca depolama alanı oluşturabilirsiniz.

Uygulama durumunu ve tüketimini korumak için bir nesne oluşturma aşağıdaki uygulamaya benzeyebilir:

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

`MyApplicationState`Nesnesi sunucuda yalnızca bir kez oluşturulur ve değer `VisitorCounter` getirilir ve bileşen etiketinde çıktı olur. `VisitorCounter`Değerin kalıcı olması ve dayanıklılık ve ölçeklenebilirlik için bir yedekleme veri deposundan alınması gerekir.

## <a name="in-the-browser"></a>Tarayıcıda

Uygulama verileri, daha sonra kullanılabilir olması için kullanıcının cihazında istemci tarafı da depolanabilir. Kullanıcı tarayıcısının farklı kapsamlarında verilerin kalıcılığına izin veren iki tarayıcı özelliği vardır:

- `localStorage`-kullanıcının tüm tarayıcı kapsamı. Sayfa yeniden yüklendiğinde, tarayıcı kapatılıp yeniden açılır veya aynı URL ile başka bir sekme açılırsa aynı şekilde `localStorage` tarayıcı tarafından sağlanır
- `sessionStorage`-kullanıcının geçerli tarayıcı sekmesi kapsamı. Sekme yeniden yüklendiğinde durum devam ettirir. Ancak, Kullanıcı uygulamanıza başka bir sekme açarsa veya tarayıcıyı kapatıp yeniden açarsa durum kaybedilir.

Bu özelliklerle etkileşim kurmak için bazı özel JavaScript kodu yazabilir veya bu işlevselliği sağlamak için kullanabileceğiniz çeşitli NuGet paketleri bulabilirsiniz. Bu tür bir paket [Microsoft. AspNetCore. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage)' dır.

Ve ile etkileşime geçmek üzere bu paketin kullanılmasıyla ilgili yönergeler için `localStorage` `sessionStorage` [Blazor durum yönetimi](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) makalesine bakın.

>[!div class="step-by-step"]
>[Önceki](pages-routing-layouts.md) 
> [Sonraki](forms-validation.md)
