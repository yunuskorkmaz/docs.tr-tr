---
title: ASP.NET Web Forms ve Blazor mimari karşılaştırması
description: ASP.NET Web Forms ve Blazor 'in mimarilerinin nasıl karşılaştırılacağını öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 1137218e1cd99a39240592be415f734223e90b77
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183961"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a>ASP.NET Web Forms ve Blazor mimari karşılaştırması

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms ve Blazor birçok benzer kavramlara sahip olsa da, çalışma yöntemleri arasında farklılıklar vardır. Bu bölümde ASP.NET Web Forms ve Blazor 'in iç işleyişi ve mimarileri incelenmiştir.

## <a name="aspnet-web-forms"></a>ASP.NET Web Forms

ASP.NET Web Forms Framework, sayfa merkezli bir mimariyi temel alır. Uygulamadaki bir konuma yönelik her HTTP isteği, ASP.NET yanıt veren ayrı bir sayfasıdır. Sayfalar istendiğinde, tarayıcının içeriği istenen sayfanın sonuçlarıyla birlikte değişir.

Sayfalar aşağıdaki bileşenlerden oluşur:

* HTML biçimlendirmesi
* C#veya Visual Basic kodu
* Logic ve olay işleme özelliklerini içeren bir arka plan kod sınıfı
* Denetimler

Denetimler, bir sayfada program aracılığıyla yerleştirilebilen ve bunlarla etkileşim içinde yer alan yeniden kullanılabilir Web Kullanıcı arabirimi birimleridir. Sayfalar, biçimlendirme, denetimler ve bazı kod içeren *. aspx* ile biten dosyalardan oluşur. Arka plan kod sınıfları, kullanılan programlama diline bağlı olarak aynı temel ada ve bir *. aspx.cs* ya da *. aspx. vb* uzantısına sahip dosyalardır. Her zaman, Web sunucusu *. aspx* dosyalarının içeriğini Yorumlar ve her değiştiğinde bunları derler. Web sunucusu zaten çalışıyor olsa bile bu yeniden derleme oluşur.

Denetimler, biçimlendirme ile oluşturulup Kullanıcı denetimleri olarak teslim edilebilir. Bir kullanıcı denetimi `UserControl` sınıftan türetilir ve sayfada benzer bir yapıya sahiptir. Kullanıcı denetimleri için biçimlendirme bir *. ascx* dosyasında depolanır. Eşlik eden bir arka plan kod sınıfı, bir *. ascx.cs* veya *. ascx. vb* dosyasında bulunur. Denetimler, `WebControl` ya `CompositeControl` da temel sınıfından devralarak kodla tamamen oluşturulabilir.

Sayfaların Ayrıca kapsamlı bir olay yaşam döngüsü vardır. Her sayfa, ASP.NET çalışma zamanı sayfanın kodunu her istek için yürütürken oluşan başlatma, yükleme, PreRender ve kaldırma olayları için olaylar oluşturur.

Bir sayfadaki denetimler genellikle denetimi sunan aynı sayfaya geri dönerek, bir gizli form alanından `ViewState`bir yük ile birlikte taşır. `ViewState` Alan, oluşturuldukları sırada denetimlerin durumu hakkında bilgiler içerir ve ASP.NET çalışma zamanının sunucuya gönderilen içerikte yapılan değişiklikleri karşılaştırıp tanımlamasına olanak tanır.

## <a name="blazor"></a>Blazor

Blazor, angular veya tepki verme gibi JavaScript ön uç çerçeveleri bakımından benzer bir istemci tarafı Web UI çerçevesidir. Blazor kullanıcı etkileşimlerini işler ve gerekli Kullanıcı arabirimi güncelleştirmelerini işler. Blazor *,* istek-yanıt modelini temel alır. Kullanıcı etkileşimleri, belirli bir HTTP isteği bağlamında olmayan olaylar olarak işlenir.

Blazor uygulamaları, HTML sayfasında işlenen bir veya daha fazla kök bileşenden oluşur.

![HTML 'de Blazor bileşenleri](./media/architecture-comparison/blazor-components-in-html.png)

Kullanıcı, bileşenlerin nerede işleneceğini ve bileşenlerin kullanıcı etkileşimleri için nasıl bağlanacağını, modele özgü bir [barındırma](hosting-models.md) .

Blazor [bileşenleri](components.md) , yeniden KULLANILABILIR bir UI parçasını temsil eden .net sınıflarıdır. Her bileşen kendi durumunu korur ve diğer bileşenleri işlemeyi içerebilen kendi işleme mantığını belirtir. Bileşenler, bileşenin durumunu güncelleştirmek üzere belirli kullanıcı etkileşimleri için olay işleyicilerini belirtir.

Bir bileşen bir olayı işlediğinde, Blazor bileşeni işler ve işlenmiş çıktıda nelerin değiştiğini izler. Bileşenler, Belge Nesne Modeli (DOM) doğrudan işlenmez. Bunun yerine, Blazor 'in değişiklikleri izleyebilmesi için, adlı `RenderTree` Dom 'ın bellek içi gösterimine işlenir. Blazor, yeni işlenmiş çıktıyı daha sonra DOM 'a verimli bir şekilde uyguladığı bir UI farkını hesaplamak için önceki çıktıyla karşılaştırır.

![Blazor DOM etkileşimi](./media/architecture-comparison/blazor-dom-interaction.png)

Bileşenler, olağan dışı bir kullanıcı arabirimi olayının dışına değiştiği takdirde, bunların işlenip işlenmeyeceğini el ile de belirtebilir. Blazor, yürütmenin `SynchronizationContext` tek bir mantıksal iş parçacığını zorlamak için bir kullanır. Bir bileşenin yaşam döngüsü yöntemleri ve Blazor tarafından oluşturulan tüm olay geri çağırmaları bunun `SynchronizationContext`üzerinde yürütülür.

>[!div class="step-by-step"]
>[Önceki](introduction.md)
>[İleri](hosting-models.md)
