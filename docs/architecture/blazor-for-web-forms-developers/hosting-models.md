---
title: Blazor uygulama barındırma modelleri
description: WebAssembly'deki tarayıcı da dahil olmak üzere bir Blazor uygulamasını barındırmanın farklı yollarını öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 77a022b01efba01038790c9601ea03f315a28fdf
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607938"
---
# <a name="blazor-app-hosting-models"></a>Blazor uygulama barındırma modelleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Blazor uygulamaları, tıpkı ASP.NET Web Forms uygulamaları gibi IIS'de barındırılabilir. Blazor uygulamaları da aşağıdaki yollardan biriyle barındırılabilir:

- WebAssembly'deki tarayıcıda istemci tarafı.
- ASP.NET Core uygulamasında sunucu tarafı.

## <a name="blazor-webassembly-apps"></a>Blazor WebAssembly uygulamaları

Blazor WebAssembly uygulamaları doğrudan tarayıcıda WebAssembly tabanlı .NET çalışma zamanında yürütülür. Blazor WebAssembly uygulamaları, Açısal veya React gibi ön uç JavaScript çerçevelerine benzer şekilde çalışır. Ancak, JavaScript yazmak yerine C# yazarsınız. .NET çalışma süresi uygulama derlemesi ve gerekli bağımlılıklarla birlikte uygulamayla birlikte indirilir. Tarayıcı eklentileri veya uzantıları gerekmez.

İndirilen derlemeler, diğer .NET uygulamasında kullanacağınız gibi normal .NET derlemeleridir. Çalışma zamanı .NET Standard'ı desteklediği için, Blazor WebAssembly uygulamanızla varolan .NET Standart kitaplıklarını kullanabilirsiniz. Ancak, bu derlemeler yine de tarayıcı güvenlik sandbox yürütülecektir. Bazı işlevler, <xref:System.PlatformNotSupportedException>dosya sistemine erişmeye çalışmak veya rasgele ağ bağlantılarını açmak gibi bir şey atabilir.

Uygulama yüklendiğinde ,NET çalışma süresi başlatılır ve uygulama derlemesi işaret edilir. Uygulama başlatma mantığı çalışır ve kök bileşenleri işlenir. Blazor, bileşenlerden işlenen çıktıyı temel alan UI güncelleştirmelerini hesaplar. DOM güncelleştirmeleri daha sonra uygulanır.

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

Blazor WebAssembly uygulamaları tamamen istemci tarafından çalışır. Bu tür uygulamalar, GitHub Sayfaları veya Azure Statik Web Sitesi Barındırma gibi statik site barındırma çözümlerine dağıtılabilir. .NET sunucuda hiç gerekli değildir. Uygulamanın bazı bölümlerine derin bağlantı genellikle sunucuda bir yönlendirme çözümü gerektirir. Yönlendirme çözümü istekleri uygulamanın köküne yönlendirir. Örneğin, bu yeniden yönlendirme IIS'de URL yeniden yazma kuralları kullanılarak işlenebilir.

Blazor'un tüm avantajlarından ve .NET web geliştirmenin tüm avantajlarından yararlanmak için Blazor WebAssembly uygulamanızı ASP.NET Core ile barındırın. .NET'i hem istemcide hem de sunucuda kullanarak, kodu kolayca paylaşabilir ve tutarlı bir dil, çerçeve ve araç kümesi ni kullanarak uygulamanızı oluşturabilirsiniz. Blazor, hem Blazor WebAssembly uygulaması hem de ASP.NET Core ana bilgisayar projesi içeren bir çözüm ayarlamak için kullanışlı şablonlar sağlar. Çözüm oluşturulduğunda, Blazor uygulamasından yerleşik statik dosyalar, geri dönüş yönlendirmesi zaten kurulumu olan ASP.NET Core uygulaması tarafından barındırılır.

## <a name="blazor-server-apps"></a>Blazor Server uygulamaları

[Blazor mimarisi](architecture-comparison.md#blazor) tartışmasından, Blazor bileşenlerinin çıktılarını bir `RenderTree`. Blazor çerçevesi daha sonra daha önce işlenen ile işlenen ne karşılaştırır. Farklar DOM'a uygulanır. Blazor bileşenleri, işlenen çıktılarının nasıl uygulandığından ayrıştırılır. Sonuç olarak, bileşenlerin ui'yi güncelleştirme işlemiyle aynı işlemde çalışması gerekmez. Aslında, aynı makinede koşmalarına bile gerek yok.

Blazor Server uygulamalarında bileşenler tarayıcıda istemci tarafı yerine sunucuda çalışır. Tarayıcıda oluşan u-u-i olayları sunucuya gerçek zamanlı bağlantı üzerinden gönderilir. Olaylar doğru bileşen örneklerine gönderilir. Bileşenler işlenir ve hesaplanan UI diff seri hale getirilir ve DOM'a uygulandığı tarayıcıya gönderilir.

![Blazor Server](media/hosting-models/blazor-server.png)

Blazor Server barındırma modeli, AJAX ve <xref:System.Web.UI.UpdatePanel> denetim ASP.NET kullandıysanız tanıdık gelebilir. Denetim, `UpdatePanel` sayfadaki olayları tetiklemek için kısmi sayfa güncelleştirmeleri uygulayarak işler. Tetiklendiğinde, kısmi `UpdatePanel` bir güncelleştirme ister ve sayfayı yenilemeye gerek kalmadan uygular. UI'nin durumu kullanılarak `ViewState`yönetilir. Blazor Server uygulamaları, uygulamanın istemciyle etkin bir bağlantı gerektirmesi açısından biraz farklıdır. Ayrıca, tüm UI durumu sunucuda korunur. Bu farklılıkların yanı sıra, iki model kavramsal olarak benzerdir.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Nasıl doğru Blazor hosting modeli seçmek için

[Blazor hosting modeli dokümanlarda](/aspnet/core/blazor/hosting-models)açıklandığı gibi, farklı Blazor barındırma modelleri farklı tradeoffs var.

Blazor WebAssembly barındırma modeli aşağıdaki avantajlara sahiptir:

- .NET sunucu tarafı bağımlılığı yoktur. Uygulama istemciye indirildikten sonra tam olarak çalışır.
- İstemci kaynakları ve yetenekleri tamamen kaldıraçlı.
- Çalışma sunucudan istemciye boşaltılır.
- Uygulamayı barındırmak için ASP.NET Core web sunucusu gerekmez. Sunucusuz dağıtım senaryoları mümkündür (örneğin, uygulamaya bir CDN'den hizmet vermektedir).

Blazor WebAssembly barındırma modelinin dezavantajları şunlardır:

- Tarayıcı özellikleri uygulamayı kısıtlar.
- Yetenekli istemci donanımı ve yazılımı (örneğin, WebAssembly desteği) gereklidir.
- İndirme boyutu daha büyüktür ve uygulamaların yüklenmesi daha uzun sürer.
- .NET çalışma süresi ve takım desteği daha az olgundur. Örneğin, [.NET Standart](../../standard/net-standard.md) desteği ve hata ayıklama sınırlamaları vardır.

Tam tersine, Blazor Server barındırma modeli aşağıdaki avantajları sunar:

- İndirme boyutu istemci tarafındaki bir uygulamadan çok daha küçüktür ve uygulama çok daha hızlı yüklenir.
- Uygulama, .NET Core uyumlu API'lerin kullanımı da dahil olmak üzere sunucu özelliklerinden tam olarak yararlanır.
- Sunucudaki .NET Core uygulamayı çalıştırmak için kullanılır, bu nedenle hata ayıklama gibi varolan .NET araç kullanımı beklendiği gibi çalışır.
- İnce istemciler desteklenir. Örneğin, sunucu tarafındaki uygulamalar WebAssembly'i desteklemeyen tarayıcılarla ve kaynak kısıtlamalı aygıtlarla çalışır.
- Uygulamanın bileşen kodu da dahil olmak üzere .NET/C# kod tabanı istemcilere sunulmaz.

Blazor Server barındırma modelinin dezavantajları şunlardır:

- Yüksek UI gecikmesi. Her kullanıcı etkileşimi bir ağ atlama içerir.
- Çevrimdışı destek yok. İstemci bağlantısı başarısız olursa, uygulama çalışmayı durdurur.
- Ölçeklenebilirlik, birçok kullanıcısı olan uygulamalar için zordur. Sunucu, birden çok istemci bağlantısını yönetmeli ve istemci durumunu işlemelidir.
- Uygulamaya hizmet vermek için ASP.NET Core sunucusu gereklidir. Sunucusuz dağıtım senaryoları mümkün değildir. Örneğin, uygulamaya bir CDN'den hizmet veremezsiniz.

Önceki trade-off listesi korkutucu olabilir, ancak barındırma modeli daha sonra değiştirilebilir. Seçilen Blazor barındırma modeli ne olursa olsun, bileşen modeli *aynıdır.* Prensip olarak, aynı bileşenler barındırma modeli ile de kullanılabilir. Uygulama kodunuz değişmez; ancak, bileşenlerinizin model-agnostik barındırma kalmak böylece soyutlamalar tanıtmak için iyi bir uygulamadır. Soyutlamalar, uygulamanızın farklı bir barındırma modelini daha kolay benimsemesini sağlar.

## <a name="deploy-your-app"></a>Uygulamanızı dağıtma

ASP.NET Web Forms uygulamaları genellikle IIS'de bir Windows Server makinesinde veya kümede barındırılır. Blazor uygulamaları da şunları yapabilir:

- Statik dosyalar olarak veya ASP.NET Core uygulaması olarak IIS'de barındırılı olun.
- ASP.NET Core'un çeşitli platformlarda ve sunucu altyapılarında barındırılmak üzere esnekliğini kaldırın. Örneğin, Linux'ta [Nginx](/aspnet/core/host-and-deploy/linux-nginx) veya [Apache](/aspnet/core/host-and-deploy/linux-apache) kullanarak bir Blazor Uygulaması barındırabilirsiniz. Blazor uygulamalarının nasıl yayınlanıp dağıtılanması hakkında daha fazla bilgi için Blazor [Barındırma ve dağıtım](/aspnet/core/host-and-deploy/blazor/) belgelerine bakın.

Bir sonraki bölümde, Blazor WebAssembly ve Blazor Server uygulamaları için projelerin nasıl kurulduğuna bakacağız.

>[!div class="step-by-step"]
>[Önceki](architecture-comparison.md)
>[Sonraki](project-structure.md)
