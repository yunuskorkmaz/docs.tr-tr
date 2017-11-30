---
title: Mimari ilkeleri
description: "ASP.NET Core ve Azure ile modern Web uygulamaları mimari | Mimari ilkeleri"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 20524c8aa0e64fd40a1a4a6811063557f74074d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
#<a name="architectural-principles"></a>Mimari ilkeleri

> "Oluşturucular binalar oluşturulduysa program yolu programcıları yazdı ve ardından gelen boyunca ilk woodpecker civilization yok."  
> _\-Gerald Weinberg_

## <a name="summary"></a>Özet

Mimari ve Bakım aklınızda ile yazılım çözümleri tasarlama gerekir. Bu bölümde özetlendiği ilkeler, temiz, sürdürülebilir uygulamalarda sonuçlanır mimari kararlar doğru yönlendirmeye yardımcı olabilirsiniz. Genellikle, bu ilkeler, uygulamanızın diğer bölümlerine sıkı şekilde bağlı değildir, ancak bunun yerine açık arabirimler aracılığıyla iletişim ayrık bileşenleri dışında uygulamaları oluşturmak veya sistemleri Mesajlaşma doğru size yol gösterecektir.

## <a name="common-design-principles"></a>Ortak tasarım ilkeleri

### <a name="separation-of-concerns"></a>Sorunları ayrılması

Geliştirirken yol gösterici bir ilke olan **ayrımı biri ile ilgili sorunlar**. Bu ilkeyi yazılım ayrılmalıdır gerçekleştirdiği iş türlerini göre onaylar. Örneğin, kullanıcıya görüntülenecek önemli öğeleri tanımlamak için mantığı içeren ve onları daha belirgin hale getirmek için belirli bir şekilde gibi öğeler biçimlendiren bir uygulamayı göz önünde bulundurun. Biçimlendirmek için hangi öğe seçmek için sorumlu davranışı, bunlar yalnızca tesadüfen birbiriyle ilişkili ayrı sorunları olduğundan öğeleri biçimlendirme için sorumlu davranış ayrı tutulmalıdır.

Mimari, uygulamaların bu ilkeyi altyapısı ve kullanıcı arabirimi mantığı çekirdek işletme davranışına ayırarak izlemek için mantıksal olarak oluşturulabilir. İdeal olarak, iş kurallarını ve mantığı uygulamadaki başka projelerde bağımlı olmamalıdır ayrı bir proje bulunmalıdır. Bu iş modeli kolay olduğundan emin olun yardımcı sınamak ve sıkı şekilde alt düzey uygulama ayrıntılarını bağlı olmadan geliştirin. Bir anahtar kullanımı arkasında göz önüne alarak katmanlı uygulama mimarilerindeki sorunları ayrılmasıdır.

### <a name="encapsulation"></a>Kapsülleme

Bir uygulamanın farklı bölümlerini kullanması gereken **kapsülleme** bunları uygulamanın diğer kısımlarından verenlerden için. Uygulama bileşenleri ve Katmanlar, kendi ortak dış sözleşmeleri olmayan ihlal sürece bozmadan kendi iç uygulaması ayarlayabilmeniz için olması gerekir. Kapsülleme doğru kullanımı, nesneleri ve paketleri aynı arabirimi korunur sürece alternatif uygulamaları ile değiştirilebilir beri gevşek bağlantı ve modülerlik uygulama tasarımlarına elde yardımcı olur.

Sınıfları, sınıfın iç durumu erişimi dışında sınırlayarak kapsülleme elde edilir. Nesnenin durumunu denetlemek bir dış aktör istiyorsa, onu bir iyi tanımlanmış işlevi (veya özellik ayarlayıcısı aracılığıyla), nesnenin özel durumu için doğrudan erişim sahibi olmayı yerine bunu. Benzer şekilde, uygulama bileşenlerini ve uygulamaların kendileri kendi ortak çalışanlarla durumlarına doğrudan değiştirilmesine izin vermek yerine kullanmak için iyi tanımlanmış arabirimleri maruz bırakmamalısınız. Bu uygulamanın iç tasarım ortak sözleşmeleri korunur sürece bunu yaparsanız, ortak çalışanlar, böylece kesintiye uğrar endişelenmeden zamanla gelişmesi boşaltır.

### <a name="dependency-inversion"></a>Bağımlılık tersine çevirme

Uygulama içinde bağımlılık yönünü soyutlama, uygulama ayrıntılarını yönde olması gerekir. Derleme zamanı bağımlılık çalışma zamanı yürütme yönde akar şekilde uygulamaların çoğu yazılır. Bu, doğrudan bağımlılık grafiğinin oluşturur. Diğer bir deyişle, bir işlev modülü C ve ardından derleme zamanı A olacaktır, çağıran modülü A çağrıları işlevi modülünde B, a C, Şekil 4-1'de gösterildiği gibi bağlı olan B bağımlı varsa.

![](./media/image4-1.png)

**Şekil 4-1.** Doğrudan bağımlılık grafiğinin.

Bağımlılık ters çevirmeyi ilkesini uygulamak için çalışma zamanında B çağrısına olası kolaylaştırarak B uygulayan bir Özet yöntemleri çağırmak bir verir ancak arabirime bağımlı b A derleme zamanında denetlenen (Bu nedenle, *ters çevirme* genel derleme zamanı bağımlılığı). Çalışma zamanında, program yürütme akışını değişmeden kalır, ancak bu arabirimleri farklı uygulamaları kolayca takılabilen olduğunu arabirimleri giriş anlamına gelir.

![](./media/image4-2.png)

**Şekil 4-2.** Ters bağımlılık grafiğinin.

**Bağımlılık ters çevirmeyi** bağlıdır ve diğer yönden yerine, daha yüksek düzey soyutlamalar uygulamak için uygulama ayrıntılarını yazılabilir bu yana birbirine sıkı şekilde bağlı uygulamaları oluşturmak, önemli bir parçasıdır. Sonuçta elde edilen sonuç olarak daha sınanabilir, modüler ve sürdürülebilir uygulamalardır. Uygulaması *bağımlılık ekleme* bağımlılık ters çevirmeyi ilkesini izleyerek mümkün hale getirilir.

### <a name="explicit-dependencies"></a>Açık bağımlılıkları

**Açıkça yöntemleri ve sınıfları düzgün çalışabilmesi için gereksinim duydukları tüm iş nesnelerini istemeniz gerekir.** Sınıf Oluşturucular, geçerli bir durumda olması için ve düzgün çalışması için gereken noktaları tanımlamak sınıflar için bir fırsattır. Bu sınıfları, kullanılabilir oluşturulan ve çağrılır, ancak hangi yalnızca işlev görecektir düzgün belirli genel veya altyapı bileşenlerini bulunmuyorsa sınıfları tanımlarsanız Yükleniyor *yapan dürüst olmayan* istemcileri ile. Oluşturucu sözleşme, yalnızca belirtilen şeyleri (büyük olasılıkla hiçbir şey sınıfı yalnızca varsayılan bir oluşturucu kullanılıyorsa), ancak sonra bir nesneyi renge çalışma zamanında gereken istemci başka bir şey gerçekten belirtiyor.

Açık bağımlılıkları ilkesini izleyerek, sınıflar ve yöntemler çalışması için istedikleri hakkında istemcileri ile dürüst yükleniyor. Bu, daha çok kendinden belgeli kodunuzu sağlar ve kullanıcılar yöntemi formunda gerekli sağladıkları sürece bu güven için gelecek olduğundan, kodlama daha kullanıcı dostu sözleşmeler veya Oluşturucu parametreleri, birlikte çalıştığınız nesneleri davranacak doğru çalışma zamanında.

### <a name="single-responsibility"></a>Tek sorumluluk

Tek sorumluluk ilkesini nesne odaklı tasarım uygulanır, ancak ayrıca sorunları ayrılması için benzer bir mimari ilkesi olarak düşünülebilir. Nesneleri yalnızca bir sorumluluk olmalıdır ve değiştirmek için yalnızca bir neden olması gerektiğini belirtir. Özellikle, nesne değiştirmeniz gerekir tek bir sorumluluğunu gerçekleştirir şekilde güncelleştirilmesi gerekir, durumdur. Bu ilke aşağıdaki daha üretmeye yardımcı gevşek bağlanmış ve modüler sistemleri, pek çok yeni davranış bu yana yeni sınıflar olarak yerine mevcut sınıflarını ek sorumluluğu ekleyerek uygulanabilir. Yeni sınıflar ekleyerek her zaman bu yana hiçbir kod varolan sınıfları değiştirme daha güvenlidir henüz yeni sınıflarında bağlıdır.

Tek yapılı bir uygulamada, biz uygulama katmanlar için yüksek bir düzeyde tek sorumluluk ilkesini uygulayabilirsiniz. Sunu sorumluluk UI projesinde kalacağı, veri erişirken bir altyapı projesi içinde sorumluluk tutulmalıdır. İş mantığı, burada kolayca sınanabilir ve bağımsız olarak diğer sorumluluklarını gelişmesi uygulama çekirdek projesinde tutulmalıdır.

Bu ilke uygulama mimarisi için uygulanan ve mantıksal kendi uç noktasına gerçekleştirilecek mikro alın. Verilen mikro hizmet tek bir sorumluluk olması gerekir. Bir sistem davranışını genişletmek gerekiyorsa, ek mikro ekleyerek yerine var olan bir sorumluluğu ekleyerek yapmak genellikle daha iyidir.

[Mikro mimarisi hakkında daha fazla bilgi edinin](http://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>(KURU) kendiniz yineleme

Uygulama, bu hata sık sık bir kaynak olarak belirli bir kavram birden çok yerde ilgili davranışını belirtme kaçınmalısınız. Belirli bir noktada bu davranış ve olasılığını değiştirme gereksinimleri değişikliği gerektirecek davranışı en az bir örneğini güncelleştirilmesi başarısız olur sistemin tutarsız davranışlara neden.

Mantığı çoğaltmak yerine bir programlama yapısı kapsüller. Bu davranışı üzerinde tek yetkilisi oluşturmak ve bu davranışı kullanımı yeni yapı gerektiren uygulama, herhangi bir bölümünü sahip olun.

> [!NOTE]
> Yalnızca tesadüfen yinelenen davranışı birbirine bağlayan kaçının. Yalnızca iki farklı sabit hem de aynı değere sahip olduğundan, kavramsal olarak bunlar için farklı işlemler başvuruyorsanız Örneğin, yalnızca bir sabit olmalıdır anlamına gelmez.

### <a name="persistence-ignorance"></a>Kalıcılık kullanmayan

**Kalıcılık kullanmayan** , kalıcı gerekiyor, ancak kodu Kalıcılık teknolojisi seçim tarafından etkilenmemesini türleri için (PI) başvuruyor. Belirli bir taban sınıftan devralın ya da belirli bir arabirim uygulamak gerekmediği için .NET böyle türlerinde bazen için düz eski CLR nesneleri (POCOs) denir. Kalıcılık kullanmayan uygulamaya ek esneklik sunan birden çok yolla kalıcı olmasını aynı iş modeli izin verdiği için faydalıdır. Kalıcılık seçimler başka bir veritabanı teknolojisine zaman içinde değişebilir veya başka biçimlerde Kalıcılık ne olursa olsun uygulamayı kullanmaya ek olarak gerekli olabilir (örneğin, bir Redis önbelleği veya ek olarak Azure DocumentDb kullanarak bir ilişkisel veritabanı).

Bu ilkeyi ihlal bazı örnekleri şunlardır:

-   Gerekli bir taban sınıfı

-   Gerekli arabirim uygulaması

-   Kendilerini (etkin kayıt deseni gibi) kaydetmek için sorumlu sınıfları

-   Gerekli varsayılan oluşturucu

-   Virtual anahtar sözcüğü gerektiren özellikleri

-   Kalıcılık özgü gerekli öznitelikler

Sınıfları yukarıdaki özellikleri veya davranışları hiçbirini sahip gereksinim kalıcı olmasını türleri ve yeni veri erişim stratejileri gelecekte benimsemeyi daha zor hale getirme, Kalıcılık teknolojisi seçimi arasındaki bağlantı ekler.

### <a name="bounded-contexts"></a>Sınırlanmış bağlamları

**Bağlamları ilişkisindeki** Domain-Driven Tasarım Merkezi desende şunlardır. Bunlar büyük uygulamalar ve kuruluşlardaki kuruluşlarda karmaşıklık ayrı kavramsal modüllerine çiğnemekten tarafından sağlarlar. Kavramsal modüllerin ardından diğer bağlamlarda ayrılmış bir bağlamı temsil eder (Bu nedenle, sınırlanmış) ve bağımsız olarak gelişmesi. Sınırlanmış her bağlam ideal kavramları içerdiği için kendi adları seçmek boş olmalıdır ve özel erişim, kendi kalıcı depolama alanına sahip olmalıdır.

En azından, tek tek web uygulamaları kendi sınırlanmış bağlamla bir veritabanını başka uygulamalarla paylaşma yerine kendi iş modeli için kendi Kalıcılık deposu olması olmaya çabalar. Sınırlanmış bağlamları arasındaki iletişim için iş mantığı sağlayan bir paylaşılan veritabanı yerine programlama arabirimleri aracılığıyla oluşur ve gerçekleşmesi değişikliklere yanıt almak için olayları yerleştirir. Bağlamları harita yakından, ayrıca tek tek kendi sınırlanmış bağlamları ideal olarak uygulanan mikro ilişkisindeki.

> ### <a name="references--modern-web-applications"></a>Başvuruları – Modern Web uygulamaları
> - **Sorunları ayrılması**  
> <http://deviq.com/separation-of-concerns/>
> - **Kapsülleme** <http://deviq.com/encapsulation/>
> - **Bağımlılık tersine çevirme ilkesi**  
> <http://deviq.com/Dependency-inversion-Principle/>
> - **Açık bağımlılıkları İlkesi**  
> <http://deviq.com/Explicit-Dependencies-Principle/>
> - **Kendiniz yineleme**  
> <http://deviq.com/Don-t-REPEAT-yourself/>
> - **Kalıcılık kullanmayan**  
> <http://deviq.com/persistence-ignorance/>
> - **Sınırlanmış bağlamı**  
> <https://martinfowler.com/bliki/BoundedContext.HTML>

> [!div class="step-by-step"]
[Önceki] (choose-between-traditional-web-and-single-page-apps.md) [sonraki] (ortak-web-uygulama-architectures.md)
