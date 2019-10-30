---
title: Blazor uygulama barındırma modelleri
description: Blazor uygulamasını, WebAssembly veya sunucu üzerindeki tarayıcıya dahil olmak üzere barındırmak için farklı yollar öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 5bf55fa686691acc25508d3d9a6dfaf8aca321ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088052"
---
# <a name="blazor-app-hosting-models"></a>Blazor uygulama barındırma modelleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Blazor Apps, tıpkı ASP.NET Web Forms Apps gibi IIS 'de barındırılabilir. Blazor uygulamaları, aşağıdaki yollarla da barındırılabilir:

- WebAssembly üzerinde tarayıcıda istemci tarafı.
- ASP.NET Core uygulamasında sunucu tarafı.

## <a name="blazor-webassembly-apps"></a>Blazor WebAssembly uygulamaları

Blazor WebAssembly Apps, bir WebAssembly tabanlı .NET çalışma zamanı üzerinde doğrudan tarayıcıda yürütülür. Blazor WebAssembly Apps işlevini, angular veya tepki verme gibi ön uç JavaScript çerçeveleri için benzer bir şekilde çalışır. Ancak, yazdığınız C#JavaScript yazmak yerine. .NET çalışma zamanı, uygulama derlemesi ve gerekli bağımlılıklarla birlikte uygulamayla birlikte indirilir. Tarayıcı eklentileri veya uzantıları gerekli değildir.

İndirilen derlemeler, diğer herhangi bir .NET uygulamasında kullanacağınız gibi normal .NET derlemelerdir. Çalışma zamanı .NET Standard desteklediğinden, mevcut .NET Standard kitaplıklarını Blazor WebAssembly uygulamanızla birlikte kullanabilirsiniz. Ancak, bu derlemeler hala tarayıcı güvenlik korumalı alanında yürütülür. Bazı işlevler, dosya sistemine erişmeye veya rastgele ağ bağlantılarını açmaya çalışan bir <xref:System.PlatformNotSupportedException> oluşturabilir.

Uygulama yüklendiğinde, .NET çalışma zamanı başlatılır ve uygulama derlemesine işaret edilir. Uygulama başlangıç mantığı çalışır ve kök bileşenleri işlenir. Blazor, Kullanıcı arabirimi güncelleştirmelerini, bileşenlerin işlenen çıktısına göre hesaplar. DOM güncelleştirmeleri uygulanır.

![Blazor WebAssembly](media/hosting-models/blazor-webassembly.png)

Blazor WebAssembly Apps yalnızca istemci tarafında çalışır. Bu tür uygulamalar, GitHub sayfaları veya Azure statik Web sitesi barındırma gibi statik site barındırma çözümlerine dağıtılabilir. .NET sunucuda gerekli değildir. Uygulamanın bölümlerine derin bağlama genellikle sunucuda bir yönlendirme çözümü gerektirir. Yönlendirme çözümü, istekleri uygulamanın köküne yönlendirir. Örneğin, bu yeniden yönlendirme IIS 'de URL yeniden yazma kuralları kullanılarak işlenebilir.

Blazor ve tam yığın .NET Web geliştirmenin avantajlarından yararlanmak için, Blazor WebAssembly uygulamanızı ASP.NET Core barındırın. Hem istemci hem de sunucuda .NET kullanarak, tutarlı bir dil, çerçeve ve araç kümesi kullanarak kodu kolayca paylaşabilir ve uygulamanızı oluşturabilirsiniz. Blazor, hem bir Blazor WebAssembly uygulaması hem de bir ASP.NET Core Host projesi içeren bir çözüm ayarlamaya yönelik uygun şablonlar sağlar. Çözüm yapılandırıldığında, Blazor uygulamasındaki oluşturulan statik dosyalar, geri dönüş yönlendirme zaten kurulumuyla ASP.NET Core uygulama tarafından barındırılır.

## <a name="blazor-server-apps"></a>Blazor sunucusu uygulamaları

Blazor bileşenlerinin çıktılarını `RenderTree` adlı bir ara soyutlamakta işleme [Blazor mimari](architecture-comparison.md#blazor) tartışmadan geri çekin. Daha sonra Blazor Framework, daha önce işlenmiş olan nelerin işlenmiş olduğunu karşılaştırır. Farklar DOM 'a uygulanır. Blazor bileşenleri, işlenen çıktısının nasıl uygulandığını birbirinden ayırır. Sonuç olarak, bileşenlerin kendisi Kullanıcı arabirimini güncelleştiren işlemle aynı işlemde çalışmak zorunda değildir. Aslında, aynı makinede çalışması bile gerekmez.

Blazor sunucu uygulamalarında, bileşenler tarayıcıda istemci tarafı yerine sunucuda çalışır. Tarayıcıda gerçekleşen Kullanıcı arabirimi olayları, gerçek zamanlı bir bağlantı üzerinden sunucuya gönderilir. Olaylar doğru bileşen örneklerine gönderilir. Bileşenler işlenir ve hesaplanmış Kullanıcı arabirimi farkı, DOM 'a uygulandığı yerde serileştirilir ve tarayıcıya gönderilir.

![Blazor Server](media/hosting-models/blazor-server.png)

ASP.NET AJAX ve <xref:System.Web.UI.UpdatePanel> denetimini kullandıysanız Blazor Server barındırma modeli tanıdık gelebilir. `UpdatePanel` denetim, sayfadaki olayları tetiklemeye yönelik kısmi sayfa güncelleştirmelerini uygulamayı işler. Tetiklendiğinde, `UpdatePanel` kısmi bir güncelleştirme ister ve sonra sayfayı yenilemeye gerek kalmadan uygulamayı uygular. Kullanıcı arabiriminin durumu `ViewState` kullanılarak yönetilir. Blazor sunucu uygulamaları, uygulamanın istemciyle etkin bir bağlantı gerektirdiğinden biraz farklıdır. Ayrıca, tüm Kullanıcı arabirimi durumu sunucuda tutulur. Bu farklılıklardan ayrı olarak, iki model kavramsal olarak benzerdir.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Doğru Blazor barındırma modelini seçme

[Blazor barındırma modeli belgeleri](https://docs.microsoft.com/aspnet/core/blazor/hosting-models#server-side)bölümünde açıklandığı gibi, farklı Blazor barındırma modellerinin farklı avantajları vardır.

Blazor WebAssembly barındırma modeli aşağıdaki avantajlara sahiptir:

- .NET sunucu tarafı bağımlılığı yoktur. Uygulama, istemciye indirildikten sonra tamamen çalışır.
- İstemci kaynakları ve yetenekleri tamamen yararlanılabilir.
- İş sunucudan istemciye boşaltılır.
- Uygulamayı barındırmak için bir ASP.NET Core Web sunucusu gerekli değildir. Sunucusuz dağıtım senaryoları mümkündür (örneğin, bir CDN 'den uygulama sunma).

Blazor WebAssembly barındırma modelinin aşağı yönleri şunlardır:

- Tarayıcı yetenekleri uygulamayı kısıtlar.
- Uyumlu istemci donanımı ve yazılımı (örneğin, WebAssembly desteği) gereklidir.
- İndirme boyutu daha büyüktür ve uygulamaların yüklenmesi daha uzun sürer.
- .NET çalışma zamanı ve araç desteği daha az olgun. Örneğin, [.NET Standard](../../standard/net-standard.md) desteğinin ve hata ayıklamada sınırlamalar vardır.

Buna karşılık, Blazor Server barındırma modeli aşağıdaki avantajları sunar:

- İndirme boyutu bir istemci tarafı uygulamadan çok daha küçüktür ve uygulama çok daha hızlı yüklenir.
- Uygulama, .NET Core ile uyumlu API 'lerin kullanımı dahil olmak üzere sunucu olanaklarından tam olarak yararlanır.
- Sunucuda .NET Core, uygulamayı çalıştırmak için kullanılır, bu nedenle hata ayıklama gibi mevcut .NET araçları beklendiği gibi çalışır.
- Ölçülü istemciler desteklenir. Örneğin, sunucu tarafı uygulamalar, WebAssembly ve kaynak kısıtlı cihazlarda bulunan tarayıcılarla çalışır.
- Uygulamanın bileşen kodu da dahilC# olmak üzere, uygulamanın .NET/kod tabanı istemcilere sunulmuyor.

Blazor sunucusu barındırma modelinin aşağı yönleri şunlardır:

- Daha yüksek UI gecikmesi. Her Kullanıcı etkileşimi bir ağ atmasını içerir.
- Çevrimdışı destek yoktur. İstemci bağlantısı başarısız olursa, uygulama çalışmayı durduruyor.
- Ölçeklenebilirlik, çok sayıda kullanıcısı olan uygulamalar için zorlayıcı bir uygulamalardır. Sunucunun birden çok istemci bağlantısını yönetmesi ve istemci durumunu işlemesi gerekir.
- Uygulamayı çalıştırmak için bir ASP.NET Core sunucusu gerekir. Sunucusuz dağıtım senaryoları mümkün değildir. Örneğin, uygulamayı bir CDN 'den çalıştıramazsınız.

Yukarıdaki, önde gelen denge listesi başlatılamayabilir, ancak barındırma modeliniz daha sonra değiştirilebilir. Blazor barındırma modelinden bağımsız olarak, bileşen modeli *aynı*olur. Prensibi, aynı bileşenler barındırma modeliyle birlikte kullanılabilir. Uygulama kodunuz değişmez; Ancak, bileşenlerinizin model belirsiz bir şekilde barındırılması için soyutlamalar tanıtmak iyi bir uygulamadır. Soyutlamalar, uygulamanızın farklı bir barındırma modelini daha kolay benimsemesini sağlar.

## <a name="deploy-your-app"></a>Uygulamanızı dağıtın

ASP.NET Web Forms uygulamalar genellikle bir Windows Server makinesi veya kümesi üzerinde IIS üzerinde barındırılır. Blazor uygulamalar da şunları yapabilir:

- Statik dosyalar olarak veya ASP.NET Core bir uygulama olarak IIS 'de barındırılmalıdır.
- ASP.NET Core, çeşitli platformlarda ve sunucu altyapılarında barındırılmak için esnekliğinden yararlanın. Örneğin, Linux 'ta [NGINX](/aspnet/core/host-and-deploy/linux-nginx) veya [Apache](/aspnet/core/host-and-deploy/linux-apache) kullanarak bir Blazor uygulaması barındırabilirsiniz. Blazor uygulamalarını yayımlama ve dağıtma hakkında daha fazla bilgi için Blazor [barındırma ve dağıtım](/aspnet/core/host-and-deploy/blazor/) belgelerine bakın.

Sonraki bölümde, Blazor WebAssembly ve Blazor Server uygulamaları için projelerin nasıl ayarlantığından bakacağız.

>[!div class="step-by-step"]
>[Önceki](architecture-comparison.md)
>[İleri](project-structure.md)
