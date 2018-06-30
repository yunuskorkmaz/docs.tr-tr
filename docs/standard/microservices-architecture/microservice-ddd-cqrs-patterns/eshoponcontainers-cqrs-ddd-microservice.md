---
title: DDD mikro hizmet eShopOnContainers içinde uygulanan CQRS ve CQS yaklaşımlar
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | DDD mikro hizmet eShopOnContainers içinde uygulanan CQRS ve CQS yaklaşımlar
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: fdca8d38157d5c5b62bd077e5d715ca22ac9780f
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106755"
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>DDD mikro hizmet eShopOnContainers içinde uygulanan CQRS ve CQS yaklaşımlar

Sıralama mikro hizmet eShopOnContainers başvuru uygulama tasarımını CQRS kurallara göre temel alır. Ancak, yalnızca sorguları komutları ayırmak ve hem eylemleri için aynı veritabanını kullanarak basit bir yaklaşım kullanır.

Bu düzenlere ve burada önemli olan nokta sorguların ıdempotent olduğundan olduğu: bir sistem sorgu kaç kez olsun, bu sistem durumu değişmez. Etki alanı modeli, işlem mantığı "Yazar daha" sıralama mikro aynı veritabanını kullanıyor olsa da hatta farklı "Okuma" veri modelini kullanabilirsiniz. Bu nedenle bu bir Basitleştirilmiş CQRS yaklaşımdır.

Diğer taraftan, işlemleri ve veri güncelleştirmelerini tetiklemek, komutları sistem durumunu değiştirin. Komutları ile ne zaman dikkatli olmanız gerekir. ilgilenme karmaşıklık ve sürekli değişen iş kuralları. Bu yerdir bir daha iyi Modellenen sistem olacak şekilde DDD teknikleri uygulamak istiyor.

Bu kılavuzda sunulan DDD desenleri Evrensel uygulanmamalıdır. Bunlar tasarımınızı kısıtlamalar tanıtır. Bu kısıtlamalar özellikle komutlar ve sistem durumunu değiştiren başka bir kod, zaman içinde daha yüksek kaliteli gibi yararlar sağlar. Ancak, bu kısıtlamalar okuma ve veri sorgulama için daha az avantajları ile karmaşıklık ekleyin.

Bu tür bir desen daha sonraki bölümlerde inceleyeceğiz toplama düzeni ' dir. Kısaca, toplama modelinde, çok sayıda etki alanı nesnelerini ilişkilerini etki alanındaki bir sonucu olarak tek bir birim olarak kabul eder. Her zaman bu deseni sorgularda gelen avantajları elde değil; Sorgu mantığı karmaşıklığını artırabilir. Salt okunur sorgular için birden fazla nesne tek bir toplama değerlendirmesini avantajları elde. Yalnızca karmaşıklığını Al

Şekil 9-2'de gösterildiği gibi bu kılavuzda DDD desenleri (diğer bir deyişle, komutları tarafından tetiklenen gibi) yalnızca, mikro işlem/güncelleştirme alanını kullanarak önerir. Sorguları basit bir yaklaşım takip edebilir ve CQRS yaklaşımı izleyerek komutlarından ayrılmalıdır.

"Sorguları yan" uygulamak için Gelişmiş ORM EF çekirdek, AutoMapper projeksiyonları, saklı yordamlar, görünümler, gerçekleştirilmiş görünümler veya mikro ORM gibi gelen birçok yaklaşım arasından seçim yapabilirsiniz.

Bu kılavuz ve seçtik bir mikro kullanarak düz sorguları uygulamak için eShopOnContainers (özellikle sıralama mikro) ORM ister [Dapper](https://github.com/StackExchange/dapper-dot-net). Bu bir açık çerçeve çok az ek yük sayesinde en iyi performansı elde için SQL deyimleri göre herhangi bir sorgu uygulamanıza olanak sağlar.

Bu yaklaşım kullandığınızda, varlıklar bir SQL veritabanına nasıl kalıcı etkileyen herhangi bir güncelleştirme modelinizi de Dapper veya sorgulamak için tüm diğer ayrı (EF olmayan) yaklaşımlar tarafından kullanılan SQL sorguları için ayrı güncelleştirmeler gerektiğini unutmayın.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS ve DDD desenleri en üst düzey mimari değildir

Bu CQRS ve çoğu DDD desenleri (DDD Katmanlar veya toplamalar olan bir etki alanı modeli gibi) anlamak önemlidir, olmayan mimari stiller, ancak yalnızca mimarisi desenleri. Mikro, SOA ve olay denetimli mimarisi (EDA) mimari stilleri gösterilebilir. Bunlar, birçok mikro hizmetler gibi birçok bileşen bir sistem açıklanmaktadır. CQRS ve DDD desenleri bir şey tek sistem veya bileşen içinde açıklar; Bu durumda, bir mikro hizmet içinde bir şey.

Farklı ilişkisindeki bağlamları (BCs) farklı desenleri kullanılacaktır. Farklı sorumlulukları vardır ve farklı çözümler, yol açar. Bu, her yerde hatasına neden olur aynı düzeni zorlama vurgulayan değer olur. CQRS ve DDD desenleri her yerde kullanmayın. Çok sayıda alt sistemleri, BCs veya mikro daha basit ve basit CRUD Hizmetleri daha kolay veya başka bir yaklaşım kullanarak uygulanabilir.

Yalnızca bir uygulama mimarisi vardır: Sistem veya uçtan uca uygulama mimarisi (örneğin, mikro mimarisi) tasarlıyorsunuz. Ancak, her ilişkisindeki bağlamı veya mikro hizmet, uygulama içinde tasarımını kendi dengelerin ve mimari desenleri düzeyinde bir iç tasarım kararları yansıtır. Aynı mimari desenleri CQRS veya bbb gibi her yerde uygulamak çalışmayın.

####  <a name="additional-resources"></a>Ek kaynaklar

-   **Martin Fowler. CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Greg Young. CQS vs. CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)

-   **Greg Young. CQRS belgeleri**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

-   **Greg Young. Uı'lar ve olay kaynak CQRS, görev tabanlı**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)

-   **UDI Dahan. Açıklanan CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Olay kaynak (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)


>[!div class="step-by-step"]
[Önceki](apply-simplified-microservice-cqrs-ddd-patterns.md)
[sonraki](cqrs-microservice-reads.md)
