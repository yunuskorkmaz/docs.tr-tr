---
title: Blazoruygulama barındırma modelleri
description: BlazorSunucusunda veya sunucusundaki tarayıcıya dahil olmak üzere bir uygulamayı barındırmak için farklı yollar edinin WebAssembly .
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: a0d37392a65cfcbff9642476d9fdb1e5c662e66a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173269"
---
# <a name="blazor-app-hosting-models"></a>Blazoruygulama barındırma modelleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Blazoruygulamalar, ASP.NET Web Forms uygulamalar gibi IIS 'de barındırılabilir. Blazoruygulamalar, aşağıdaki yollarla da barındırılabilir:

- Üzerinde tarayıcıda istemci tarafı WebAssembly .
- ASP.NET Core uygulamasında sunucu tarafı.

## <a name="blazor-webassembly-apps"></a>BlazorWebAssemblyuygulamalar

BlazorWebAssemblyuygulamalar doğrudan tarayıcıda bir WebAssembly tabanlı .NET çalışma zamanı üzerinde yürütülür. BlazorWebAssemblyuygulamalar, angular veya tepki verme gibi ön uç JavaScript çerçeveleri için benzer bir şekilde çalışır. Bununla birlikte, JavaScript yazmak yerine C# yazın. .NET çalışma zamanı, uygulama derlemesi ve gerekli bağımlılıklarla birlikte uygulamayla birlikte indirilir. Tarayıcı eklentileri veya uzantıları gerekli değildir.

İndirilen derlemeler, diğer herhangi bir .NET uygulamasında kullanacağınız gibi normal .NET derlemelerdir. Çalışma zamanı .NET Standard desteklediğinden, mevcut .NET Standard kitaplıklarını uygulamanızla birlikte kullanabilirsiniz Blazor WebAssembly . Ancak, bu derlemeler hala tarayıcı güvenlik korumalı alanında yürütülür. Bazı işlevler <xref:System.PlatformNotSupportedException> , dosya sistemine erişmeye veya rastgele ağ bağlantılarını açmaya çalışırken bir oluşturabilir.

Uygulama yüklendiğinde, .NET çalışma zamanı başlatılır ve uygulama derlemesine işaret edilir. Uygulama başlangıç mantığı çalışır ve kök bileşenleri işlenir. Blazorbileşenlerden oluşturulan çıktıyı temel alan UI güncelleştirmelerini hesaplar. DOM güncelleştirmeleri uygulanır.

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

BlazorWebAssemblyuygulamalar yalnızca istemci tarafında çalışır. Bu tür uygulamalar, GitHub sayfaları veya Azure statik Web sitesi barındırma gibi statik site barındırma çözümlerine dağıtılabilir. .NET sunucuda gerekli değildir. Uygulamanın bölümlerine derin bağlama genellikle sunucuda bir yönlendirme çözümü gerektirir. Yönlendirme çözümü, istekleri uygulamanın köküne yönlendirir. Örneğin, bu yeniden yönlendirme IIS 'de URL yeniden yazma kuralları kullanılarak işlenebilir.

BlazorVe tam yığın .NET Web geliştirme avantajlarından yararlanmak için Blazor WebAssembly uygulamanızı ASP.NET Core barındırın. Hem istemci hem de sunucuda .NET kullanarak, tutarlı bir dil, çerçeve ve araç kümesi kullanarak kodu kolayca paylaşabilir ve uygulamanızı oluşturabilirsiniz. Blazorhem Blazor uygulama hem de ASP.NET Core bir konak projesi içeren bir çözüm ayarlamak için uygun şablonlar sağlar WebAssembly . Çözüm yapılandırıldığında, uygulamadaki oluşturulan statik dosyalar, Blazor geri dönüş yönlendirme zaten kurulumuyla ASP.NET Core uygulama tarafından barındırılır.

## <a name="blazor-server-apps"></a>BlazorSunucu uygulamaları

[ Blazor ](architecture-comparison.md#blazor) Blazor Bileşenlerin çıktılarını, a adlı bir ara soyutlamada işlemesini sağlayan mimari tartışmadan geri çekin `RenderTree` . Daha Blazor sonra Framework, daha önce işlenmiş olan nelerin işlenmiş olduğunu karşılaştırır. Farklar DOM 'a uygulanır. Blazorbileşenler, işlenen çıktısının uygulanma işleminden ayrılır. Sonuç olarak, bileşenlerin kendisi Kullanıcı arabirimini güncelleştiren işlemle aynı işlemde çalışmak zorunda değildir. Aslında, aynı makinede çalışması bile gerekmez.

BlazorSunucu uygulamalarında, bileşenler tarayıcıda istemci tarafı yerine sunucuda çalışır. Tarayıcıda gerçekleşen Kullanıcı arabirimi olayları, gerçek zamanlı bir bağlantı üzerinden sunucuya gönderilir. Olaylar doğru bileşen örneklerine gönderilir. Bileşenler işlenir ve hesaplanmış Kullanıcı arabirimi farkı, DOM 'a uygulandığı yerde serileştirilir ve tarayıcıya gönderilir.

![BlazorServer](media/hosting-models/blazor-server.png)

BlazorASP.NET AJAX ve denetimini kullandıysanız sunucu barındırma modeli tanıdık gelebilir <xref:System.Web.UI.UpdatePanel> . `UpdatePanel`Denetim, sayfadaki olayları tetiklemeye yönelik kısmi sayfa güncelleştirmelerini uygulamayı işler. Tetiklendiğinde, `UpdatePanel` kısmen bir güncelleştirme ister ve sonra sayfayı yenilemeye gerek kalmadan uygulamayı uygular. Kullanıcı arabiriminin durumu kullanılarak yönetilir `ViewState` . BlazorSunucu uygulamaları, uygulamanın istemciyle etkin bir bağlantı gerektirdiğinden biraz farklıdır. Ayrıca, tüm Kullanıcı arabirimi durumu sunucuda tutulur. Bu farklılıklardan ayrı olarak, iki model kavramsal olarak benzerdir.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Doğru Blazor barındırma modelini seçme

[ Blazor Barındırma modeli belgeleri](/aspnet/core/blazor/hosting-models)bölümünde açıklandığı gibi, farklı Blazor barındırma modellerinin farklı avantajları vardır.

Blazor WebAssembly Barındırma modeli aşağıdaki avantajlara sahiptir:

- .NET sunucu tarafı bağımlılığı yoktur. Uygulama, istemciye indirildikten sonra tamamen çalışır.
- İstemci kaynakları ve yetenekleri tamamen yararlanılabilir.
- İş sunucudan istemciye boşaltılır.
- Uygulamayı barındırmak için bir ASP.NET Core Web sunucusu gerekli değildir. Sunucusuz dağıtım senaryoları mümkündür (örneğin, bir CDN 'den uygulama sunma).

Blazor WebAssembly Barındırma modelinin aşağı yönleri şunlardır:

- Tarayıcı yetenekleri uygulamayı kısıtlar.
- Uyumlu istemci donanımı ve yazılımı (örneğin, WebAssembly destek) gereklidir.
- İndirme boyutu daha büyüktür ve uygulamaların yüklenmesi daha uzun sürer.
- .NET çalışma zamanı ve araç desteği daha az olgun. Örneğin, [.NET Standard](../../standard/net-standard.md) desteğinin ve hata ayıklamada sınırlamalar vardır.

Buna karşılık, Blazor sunucu barındırma modeli aşağıdaki avantajları sunar:

- İndirme boyutu bir istemci tarafı uygulamadan çok daha küçüktür ve uygulama çok daha hızlı yüklenir.
- Uygulama, .NET Core ile uyumlu API 'lerin kullanımı dahil olmak üzere sunucu olanaklarından tam olarak yararlanır.
- Sunucuda .NET Core, uygulamayı çalıştırmak için kullanılır, bu nedenle hata ayıklama gibi mevcut .NET araçları beklendiği gibi çalışır.
- Ölçülü istemciler desteklenir. Örneğin, sunucu tarafı uygulamalar, WebAssembly kaynak sınırlamalı cihazlarda ve desteklemeyen tarayıcılarla çalışır.
- Uygulamanın bileşen kodu da dahil olmak üzere, uygulamanın .NET/C# kod tabanı istemcilere sunulmuyor.

BlazorSunucu barındırma modelinin aşağı yönleri şunlardır:

- Daha yüksek UI gecikmesi. Her Kullanıcı etkileşimi bir ağ atmasını içerir.
- Çevrimdışı destek yoktur. İstemci bağlantısı başarısız olursa, uygulama çalışmayı durduruyor.
- Ölçeklenebilirlik, çok sayıda kullanıcısı olan uygulamalar için zorlayıcı bir uygulamalardır. Sunucunun birden çok istemci bağlantısını yönetmesi ve istemci durumunu işlemesi gerekir.
- Uygulamayı çalıştırmak için bir ASP.NET Core sunucusu gerekir. Sunucusuz dağıtım senaryoları mümkün değildir. Örneğin, uygulamayı bir CDN 'den çalıştıramazsınız.

Yukarıdaki, önde gelen denge listesi başlatılamayabilir, ancak barındırma modeliniz daha sonra değiştirilebilir. BlazorSeçili barındırma modelinden bağımsız olarak, bileşen modeli *aynı*olur. Prensibi, aynı bileşenler barındırma modeliyle birlikte kullanılabilir. Uygulama kodunuz değişmez; Ancak, bileşenlerinizin model belirsiz bir şekilde barındırılması için soyutlamalar tanıtmak iyi bir uygulamadır. Soyutlamalar, uygulamanızın farklı bir barındırma modelini daha kolay benimsemesini sağlar.

## <a name="deploy-your-app"></a>Uygulamanızı dağıtın

ASP.NET Web Forms uygulamalar genellikle bir Windows Server makinesi veya kümesi üzerinde IIS üzerinde barındırılır. Blazoruygulamalar da şunları yapabilir:

- Statik dosyalar olarak veya ASP.NET Core bir uygulama olarak IIS 'de barındırılmalıdır.
- ASP.NET Core, çeşitli platformlarda ve sunucu altyapılarında barındırılmak için esnekliğinden yararlanın. Örneğin, Blazor Linux 'Ta [NGINX](/aspnet/core/host-and-deploy/linux-nginx) veya [Apache](/aspnet/core/host-and-deploy/linux-apache) kullanarak bir uygulamayı barındırabilirsiniz. Uygulamaları yayımlama ve dağıtma hakkında daha fazla bilgi için Blazor Blazor [barındırma ve dağıtım](/aspnet/core/host-and-deploy/blazor/) belgelerine bakın.

Sonraki bölümde, projelerinin Blazor WebAssembly ve Blazor sunucu uygulamalarının nasıl ayarlanacağını inceleyeceğiz.

>[!div class="step-by-step"]
>[Önceki](architecture-comparison.md) 
> [Sonraki](project-structure.md)
