---
title: Mimari ilkeleri
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | Mimari ilkeleri
author: ardalis
ms.author: wiwagn
ms.date: 02/16/2019
ms.openlocfilehash: 7d127476e37b9eefa9ddc13d26991145b6245b45
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442990"
---
# <a name="architectural-principles"></a>Mimari ilkeleri

> "Oluşturucular binalar oluşturulduysa şekilde programcılar programları yazdığı ve sonra gelen boyunca ilk woodpecker civilization yok etmek."  
> _\- Gerald Weinberg_

Mimari ve yazılım çözümlerini unutmayın yaşatılabilirlik tasarımımız gerekir. Bu bölümde açıklanan ilkeleri temiz ve sürdürülebilir uygulamalarda neden olabilecek mimari kararları doğru yol yardımcı olabilir. Genellikle, bu ilkeler, uygulamanızın diğer kısımlarına sıkı şekilde bağlı değildir, ancak bunun yerine açık arabirim ile iletişim kurmak ayrı bileşenler dışında uygulamalar oluşturmak veya Mesajlaşma sistemleri doğru size yol gösterir.

## <a name="common-design-principles"></a>Ortak tasarım ilkeleri

### <a name="separation-of-concerns"></a>Görev ayrımı nettir

Geliştirirken bir yol gösterici ilkesidir **ayrımı, ile ilgili sorunlar**. Bu ilke, yazılım ayrılmalıdır gerçekleştirdiği iş türlerine göre onaylar. Örneğin, kullanıcıya görüntülenecek önemli öğeleri tanımlamak için mantığı içeren ve hangi gibi öğeleri daha belirgin hale getirmek için belirli bir şekilde biçimlendiren bir uygulamayı düşünün. Biçimlendirmek için hangi öğe seçmek için sorumlu davranışı, davranış öğeleri biçimlendirme bunlar yalnızca tesadüfen birbirleriyle ilişkili ayrı endişeleriniz olduğu için sorumlu ayrı tutulmalıdır.

Bu mimari, uygulama altyapısı ve kullanıcı arabirimi mantığının çekirdek iş davranışı ayırarak Bu ilkeyi izlemek için mantıksal olarak oluşturulabilir. İdeal olarak, iş kuralları ve mantıksal uygulamanın diğer projelerde bağlı olmamalıdır ayrı bir proje içinde bulunmalıdır. Bu iş modeli kolay olduğundan emin olun yardımcı olur. test ve alt düzey uygulama ayrıntıları sıkıca olmadan geliştirebilirsiniz. Görev ayrımı nettir bir anahtar kullanımı arkasındaki uygulama mimarileri katmanlarında, noktadır.

### <a name="encapsulation"></a>Kapsülleme

Bir uygulamanın farklı kısımlarını kullanması gereken **kapsülleme** bunları uygulamanın diğer kısımlarından sorunlardan uzak tutmak için. Uygulama bileşenleri ve Katmanlar dış sözleşmeleri ihlal değil sürece kendi ortak çalışanlar bozmadan kendi iç uygulama ayarlayabilmeniz için olmalıdır. Kapsülleme kullanımını nesneleri ve paketleri aynı arabirimi korunur sürece diğer uygulamaları ile değiştirilebilir beri gevşek eşleştirme ve modülerlik uygulama tasarımlarında elde etmenize yardımcı olur.

Sınıflarda, kapsülleme dışında sınıfın iç durumu erişimi kısıtlayarak elde edilir. Nesne durumunu işlemek bir dış aktör isterse, bunu bir iyi tanımlanmış işlevi (veya özellik ayarlayıcısı), doğrudan erişim nesnenin özel durumu yerine bunu. Benzer şekilde, uygulama bileşenlerini ve uygulamaların kendileri için kendi ortak çalışanlarla durumlarına doğrudan değiştirilmesine izin verme yerine kullanmak iyi tanımlanmış arabirimlere sunmalıdır. Bu uygulamanın ortak sözleşmeleri korunur sürece bunu yapmak, ortak çalışanlar, bu nedenle kesintiye uğrar endişelenmeden zamanla gelişmesinin iç tasarım serbest bırakır.

### <a name="dependency-inversion"></a>Bağımlılık tersine çevirme

Uygulama Bağımlılık yönünü soyutlama, uygulama ayrıntıları yönü olması gerekir. Çoğu uygulama, derleme zamanı bağımlılık çalışma zamanı yürütme yönde aktığını şekilde yazılır. Bu, doğrudan bir bağımlılık grafiği oluşturur. Diğer bir deyişle, C modülü ve ardından derleme zamanı A, bir işlev çağıran modülü bir çağrıları işlevi B, modüldeki bir C, Şekil 4-1'de gösterildiği gibi bağlıdır B bağlıdır.

![](./media/image4-1.png)

**Şekil 4-1.** Doğrudan bir bağımlılık grafiği.

Bağımlılık tersine çevirme ilkesinin uygulanması için çalışma zamanında, B çağrısına çözmelerine B uygulayan bir Özet yöntemleri çağırmak bir ancak bir arabirimde bağımlı b tarafından bir derleme zamanında denetlenen (Bu nedenle, *ters çevirme* Tipik derleme zamanı bağımlılık). Çalışma zamanında, program yürütmenin akışını değişmeden kalır, ancak bu arabirimin farklı uygulamalarını kolayca uygulamalarınıza, arabirimleri kullanıma sunulması anlamına gelir.

![](./media/image4-2.png)

**Şekil 4-2.** Ters bağımlılık grafiği.

**Bağımlılık tersine çevirme** bağlıdır ve geçici olarak başka bir şekilde yerine daha yüksek düzey soyutlamalar uygulamak için uygulama ayrıntılarını yazılabilir olduğundan zamanı gevşek bağlanmış, uygulamaları oluşturmak, önemli bir parçasıdır. Sonuçta elde edilen sonuç olarak daha fazla test edilebilir, modüler ve sürdürülebilir uygulamalardır. Uygulaması *bağımlılık ekleme* bağımlılık tersine çevirme ilkesi uygulayarak gerçekleştirilir.

### <a name="explicit-dependencies"></a>Özel bağımlılıklar

**Açıkça düzgün çalışması için ihtiyaç duydukları tüm birlikte çalışan nesnelerin yöntemleri ve sınıfları istemeniz gerekir.** Sınıf oluşturucuları, geçerli bir durumda olması ve düzgün şekilde çalışabilmesi için gereksinim duydukları şeyleri tanımlamak sınıflar için bir fırsattır. Sınıflar, kullanılabilir oluşturulur ve çağrılır, ancak, yalnızca çalışır düzgün belirli genel ya da altyapı bileşenlerini bulunmuyorsa tanımlarsanız, bu sınıflar gönderildiğini *yapan dürüst olmayan* istemcileri ile. Yalnızca belirtilen noktalar (muhtemelen hiçbir şey sınıfın varsayılan bir oluşturucu yalnızca kullanıyorsa), ancak ardından nesne kapatır çalışma zamanında gereken istemci gerçekten başka bir şey ihtiyaç duyduklarından Oluşturucu anlaşması söylüyor.

Özel bağımlılıklar ilkesi uygulayarak, sınıflar ve yöntemler çalışabilmesi için gereksinim duydukları şeyleri hakkında istemcileri ile dürüst yükleniyor. Bu, kendi kendine daha fazla tanım kodunuzu sağlar ve kullanıcılara, sağladıkları yöntemi biçiminde gerekli olduğu sürece bu güven için gelir beri kodlamanızı daha kullanıcı dostu sözleşmeleri veya Oluşturucu parametresi, üzerinde çalıştığınız nesneleri farklı mı davranacak doğru çalışma zamanında.

### <a name="single-responsibility"></a>Tek sorumluluk

Tek sorumluluk ilkesini nesne yönelimli tasarım için geçerlidir, ancak ayrımı için benzer bir mimari prensibi olarak düşünülebilir. Bu nesneler yalnızca bir sorumluluk olmalıdır ve değiştirmek için yalnızca bir neden olması gerektiğini belirtir. Özellikle, nesneyi değiştirmek tek bir sorumluluğunu gerçekleştirir şekilde güncelleştirilmelidir durumdur. Bu ilke aşağıdaki daha üretmeye yardımcı zamanı gevşek bağlanmış ve modüler sistemleri, pek çok yeni davranış beri yeni sınıflar olarak yerine varolan sınıflara ek sorumluluk ekleyerek uygulanabilir. Yeni sınıflar ekleyerek her zaman mevcut sınıfları bu yana hiçbir kodunun değiştirilmesi daha güvenlidir, ancak yeni sınıflarında bağlıdır.

Tek parçalı bir uygulamada uygulama katmanlarında size yüksek bir düzeyde tek sorumluluk ilke uygulayabilirsiniz. Sunu sorumluluk UI projede kalmalıdır, sorumluluk veri erişirken bir altyapı projesi içinde tutulmalıdır. İş mantığını burada kolayca sınanabilir ve bağımsız olarak diğer sorumluluklarını geliştirebilirsiniz uygulama core projesinde tutulmalıdır.

Bu ilkeyi uygulama mimarisi için uygulanan ve mantıksal bitim geçen, mikro hizmetler alın. Belirli bir mikro hizmet tek bir sorumluluğa sahip olmalıdır. Bir sistemi davranışını genişletmeniz gerekiyorsa, ek bir mikro hizmetler ekleyerek yerine var olan bir sorumluluğu ekleme yapmak genellikle daha iyidir.

[Mikro hizmet mimarisi hakkında daha fazla bilgi edinin](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Kendiniz (KURU) yineleme

Uygulama, bu hata sık kullanılan bir kaynak olarak belirli bir kavram birden çok yerde ilgili davranışını belirtme kaçınmanız gerekir. Belirli bir noktada bu davranışı ve olasılığını değiştirme gereksinimleri değişikliği gerektirecek davranışı en az bir örneğini güncelleştirilmesi başarısız olur sistemin tutarsız davranışa neden.

Mantıksal çoğaltmak yerine bir programlama yapısı içinde kapsüller. Bu tek yetkilisi bu davranışı oluşturmak ve bu davranışı kullanım yeni yapısı gerektiren bir uygulama, diğer herhangi bir bölümünü sahip olun.

> [!NOTE]
> Yalnızca tesadüfen yinelenen davranışı birbirine bağlayan kaçının. Yalnızca iki farklı sabitleri hem aynı değere sahip olduğundan, kavramsal olarak bunlar için farklı şeyler başvuruyorsanız gibi yalnızca bir sabit olmalıdır anlamına gelmez.

### <a name="persistence-ignorance"></a>Kalıcılık ignorance

**Kalıcılık ignorance** kalıcı gereken, ancak kodu Kalıcılık teknoloji seçimi tarafından etkilenmemesini türleri (PI) ifade eder. Belirli bir taban sınıftan devralın ya da belirli bir arabirim uygulamak gerekmez çünkü. NET'te böyle türleri bazen için düz eski CLR nesneleri (POCOs) denir. Uygulamaya daha fazla esneklik sunan birden çok yolla kalıcı aynı iş modeli izin verdiğinden, Kalıcılık ignorance değerlidir. Kalıcılık seçenekler, başka bir veritabanı teknolojisine zaman içinde değişebilir veya başka biçimlerde Kalıcılık ne olursa olsun uygulama kullanmaya ek olarak gerekli olabilir (örneğin, bir Redis önbelleği veya ek olarak Azure DocumentDb kullanarak bir ilişkisel veritabanı).

Bu ilke ihlallerini bazı örnekleri şunlardır:

- Gerekli bir temel sınıf.

- Bir gerekli arabirim uygulaması.

- Sınıflar (etkin kayıt düzeni gibi) kaydetmek için kendileri sorumludur.

- Gerekli bir varsayılan oluşturucu.

- Sanal anahtar sözcük gerektiren özellikleri.

- Kalıcı özel özniteliklerini gereklidir.

Sınıfları yukarıdaki özellikleri veya davranışlardan birini olma gereksinimini kalıcı için türleri ve gelecekte yeni veri erişim stratejilerini benimseyen daha zor hale getirme, Kalıcılık teknoloji seçimi arasında eşleştirme yapmaktan ekler.

### <a name="bounded-contexts"></a>Sınırlanmış bağlamlar

**Sınırlanmış Bağlamlar** merkezi bir etki alanı Odaklı Tasarım deseninde olan. Bunlar, ayrı kavramsal modüllerine bozucu tarafından kuruluşlarda karmaşıklık büyük uygulamalar veya kuruluşların bir yol sağlar. Kavramsal modüllerin sonra diğer bağlamlarda ayrılmış bir bağlamı temsil eder (Bu nedenle, sınırlanmış) ve bağımsız olarak geliştirebilirsiniz. Sınırlanmış her bağlam ideal içindeki kavramları kendi adları seçebilirsiniz olmalıdır ve özel erişim kendi deposuna sahip olmalıdır.

En azından web uygulamalarının bir veritabanını başka uygulamalarla paylaşma yerine kendi iş modeli için kendi sürdürme deposundan ile kendi sınırlanmış bağlam olması için çaba göstermelisiniz. Sınırlanmış Bağlamlar arasında iletişimi sağlayan iş mantığı için paylaşılan bir veritabanı üzerinden değil, programlama arabirimleri aracılığıyla gerçekleşir ve gerçekleşmesi değişikliklere yanıt olarak gerçekleştirilecek olayları yerleştirin. Ayrıca, kendi ayrı bir sınırlanmış Bağlamlar ideal olarak uygulanan mikro hizmetlere bağlamları harita yakından sınırlanmış.

## <a name="additional-resources"></a>Ek kaynaklar

* [JAVA tasarım desenleri: İlkeleri](https://java-design-patterns.com/principles/)
* [Sınırlanmış bağlam](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Önceki](choose-between-traditional-web-and-single-page-apps.md)
>[İleri](common-web-application-architectures.md)
