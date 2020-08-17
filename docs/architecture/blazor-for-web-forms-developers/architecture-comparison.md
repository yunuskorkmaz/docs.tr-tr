---
title: ASP.NET Web Forms ve mimari karşılaştırması Blazor
description: ASP.NET 'in mimarilerinin nasıl Web Forms ve Blazor karşılaştırılacağını öğrenin.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 9a8e78338aff53002647a10ed9007296e4682b5a
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267717"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-no-locblazor"></a>ASP.NET Web Forms ve mimari karşılaştırması Blazor

ASP.NET Web Forms ve Blazor birçok benzer kavramlara sahip olmakla birlikte, nasıl çalıştıkları konusunda farklılıklar vardır. Bu bölümde, ASP.NET Web Forms ve ve mimarilerinin iç işleyişi ve mimarileri incelenmiştir Blazor .

## <a name="aspnet-web-forms"></a>ASP.NET Web Forms

ASP.NET Web Forms Framework, sayfa merkezli bir mimariyi temel alır. Uygulamadaki bir konuma yönelik her HTTP isteği, ASP.NET yanıt veren ayrı bir sayfasıdır. Sayfalar istendiğinde, tarayıcının içeriği istenen sayfanın sonuçlarıyla birlikte değişir.

Sayfalar aşağıdaki bileşenlerden oluşur:

- HTML biçimlendirmesi
- C# veya Visual Basic kodu
- Logic ve olay işleme özelliklerini içeren bir arka plan kod sınıfı
- Denetimler

Denetimler, bir sayfada program aracılığıyla yerleştirilebilen ve bunlarla etkileşim içinde yer alan yeniden kullanılabilir Web Kullanıcı arabirimi birimleridir. Sayfalar, biçimlendirme, denetimler ve bazı kod içeren *. aspx* ile biten dosyalardan oluşur. Arka plan kod sınıfları, kullanılan programlama diline bağlı olarak aynı temel ada ve bir *. aspx.cs* ya da *. aspx. vb* uzantısına sahip dosyalardır. Her zaman, Web sunucusu *. aspx* dosyalarının içeriğini Yorumlar ve her değiştiğinde bunları derler. Web sunucusu zaten çalışıyor olsa bile bu yeniden derleme oluşur.

Denetimler, biçimlendirme ile oluşturulup Kullanıcı denetimleri olarak teslim edilebilir. Bir kullanıcı denetimi `UserControl` sınıftan türetilir ve sayfada benzer bir yapıya sahiptir. Kullanıcı denetimleri için biçimlendirme bir *. ascx* dosyasında depolanır. Eşlik eden bir arka plan kod sınıfı, bir *. ascx.cs* veya *. ascx. vb* dosyasında bulunur. Denetimler, ya da temel sınıfından devralarak kodla tamamen oluşturulabilir `WebControl` `CompositeControl` .

Sayfaların Ayrıca kapsamlı bir olay yaşam döngüsü vardır. Her sayfa, ASP.NET çalışma zamanı sayfanın kodunu her istek için yürütürken oluşan başlatma, yükleme, PreRender ve kaldırma olayları için olaylar oluşturur.

Bir sayfadaki denetimler genellikle denetimi sunan aynı sayfaya geri dönerek, bir gizli form alanından bir yük ile birlikte taşır `ViewState` . `ViewState`Alan, oluşturuldukları sırada denetimlerin durumu hakkında bilgiler içerir ve ASP.NET çalışma zamanının sunucuya gönderilen içerikte yapılan değişiklikleri karşılaştırıp tanımlamasına olanak tanır.

## Blazor

Blazor , angular veya tepki verme gibi JavaScript ön uç çerçevelerinin doğası gereği benzer bir istemci tarafı Web UI çerçevesidir. Blazor Kullanıcı etkileşimlerini işler ve gerekli Kullanıcı arabirimi güncelleştirmelerini işler. Blazoristek-yanıt modeli tabanlı *değil* . Kullanıcı etkileşimleri, belirli bir HTTP isteği bağlamında olmayan olaylar olarak işlenir.

Blazor uygulamalar, HTML sayfasında işlenen bir veya daha fazla kök bileşenden oluşur.

![::: No-Loc (Blazor)::: HTML 'deki bileşenler](./media/architecture-comparison/blazor-components-in-html.png)

Kullanıcı, bileşenlerin nerede işleneceğini ve bileşenlerin kullanıcı etkileşimleri için nasıl bağlanacağını, modele özgü bir [barındırma](hosting-models.md) .

Blazor[Bileşenler](components.md) , yeniden KULLANILABILIR bir UI parçasını temsil eden .net sınıflarıdır. Her bileşen kendi durumunu korur ve diğer bileşenleri işlemeyi içerebilen kendi işleme mantığını belirtir. Bileşenler, bileşenin durumunu güncelleştirmek üzere belirli kullanıcı etkileşimleri için olay işleyicilerini belirtir.

Bir bileşen bir olayı işlediğinde, Blazor bileşeni işler ve işlenmiş çıktıda nelerin değiştiğini izler. Bileşenler, Belge Nesne Modeli (DOM) doğrudan işlenmez. Bunun yerine `RenderTree` , değişiklikleri izleyebilmek için ADLı Dom 'ın bellek içi temsili olarak işlenir Blazor . Blazor Yeni işlenmiş çıktıyı, daha sonra DOM 'a verimli bir şekilde uyguladığı bir UI farkını hesaplamak için önceki çıktıyla karşılaştırır.

![::: No-Loc (Blazor)::: DOM etkileşimi](./media/architecture-comparison/blazor-dom-interaction.png)

Bileşenler, olağan dışı bir kullanıcı arabirimi olayının dışına değiştiği takdirde, bunların işlenip işlenmeyeceğini el ile de belirtebilir. Blazor`SynchronizationContext`yürütmenin tek bir mantıksal iş parçacığını zorlamak için bir kullanır. Bir bileşenin yaşam döngüsü yöntemleri ve tarafından oluşturulan tüm olay geri çağırmaları Blazor bunun üzerinde yürütülür `SynchronizationContext` .

>[!div class="step-by-step"]
>[Önceki](introduction.md) 
> [Sonraki](hosting-models.md)
