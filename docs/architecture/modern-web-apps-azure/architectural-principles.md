---
title: Mimari ilkeleri
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | Mimari ilkeler
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: ffc890bf8cd6b07bd70d8fc7b2b8cfeaf474ae35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450277"
---
# <a name="architectural-principles"></a>Mimari ilkeleri

> "Eğer inşaatçılar programcıların program yazdığı gibi binalar inşa ederlerse, o zaman ortaya çıkan ilk ağaçkakan uygarlığı yok ederdi."  
> _\-Gerald Weinberg_

Yazılım çözümlerini akılda takılmalı ve tasarlamalısınız. Bu bölümde özetlenen ilkeler, temiz ve bakımı yla sonuçlanacak mimari kararlara doğru size rehberlik edebilir. Genel olarak, bu ilkeler, uygulamanızın diğer bölümleriyle sıkı bir şekilde birleşen, ancak açık arabirimler veya ileti sistemleri aracılığıyla iletişim kuramayan ayrı bileşenlerden uygulamalar oluşturmanıza yönelik tir.

## <a name="common-design-principles"></a>Ortak tasarım ilkeleri

### <a name="separation-of-concerns"></a>Endişelerin ayrılması

Geliştirirken yol gösterici bir ilke **Kaygıların Ayrılmasıdır.** Bu ilke, yazılımın gerçekleştirdiği çalışma türlerine göre ayrılması gerektiğini ileri sürmelidir. Örneğin, kayda değer öğeleri kullanıcıya görüntülemek için tanımlama mantığı içeren ve bu tür öğeleri daha belirgin hale getirmek için belirli bir şekilde biçimlendiren bir uygulama düşünün. Biçimlendirilecek öğelerin seçilmesinden sorumlu davranış, öğeleri biçimlendirmekten sorumlu davranıştan ayrı tutulmalıdır, çünkü bunlar yalnızca tesadüfen birbiriyle ilişkili olan ayrı kaygılardır.

Mimari olarak, uygulamalar temel iş davranışını altyapı ve kullanıcı arabirimi mantığından ayırarak bu ilkeyi takip etmek için mantıksal olarak oluşturulabilir. İdeal olarak, iş kuralları ve mantığı, uygulamadaki diğer projelere bağlı olmayan ayrı bir projede yer almalıdır. Bu, iş modelinin test edilmesinin kolay olmasını ve düşük düzeyli uygulama ayrıntılarıyla sıkı bir şekilde birleştirilmeden gelişebilmesini sağlamaya yardımcı olur. Endişelerin ayrılması, uygulama mimarilerinde katmanların kullanımının ardındaki önemli bir husustur.

### <a name="encapsulation"></a>Kapsülleme

Bir uygulamanın farklı bölümleri, uygulamanın diğer bölümlerinden izole etmek için **kapsülleme** kullanmalıdır. Uygulama bileşenleri ve katmanları, dış sözleşmeler ihlal edilmedikçe, işbirlikçilerini bozmadan kendi iç uygulamalarını ayarlayabilmelidir. Nesneler ve paketler aynı arabirim korununca alternatif uygulamalarla değiştirilebildiği için, kapsüllemenin doğru kullanımı uygulama tasarımlarında gevşek bağlantı ve modülerlik elde edilmesine yardımcı olur.

Sınıflarda kapsülleme, sınıfın iç durumuna dışarıdan erişimsınırılarak elde edilir. Dışarıdan bir aktör nesnenin durumunu işlemek istiyorsa, bunu nesnenin özel durumuna doğrudan erişim yerine iyi tanımlanmış bir işlev (veya özellik ayarlayıcısı) aracılığıyla yapmalıdır. Aynı şekilde, uygulama bileşenleri ve uygulamaları kendilerini kendi durumu doğrudan değiştirilmesine izin yerine, kendi ortak kullanmak için iyi tanımlanmış arabirimleri ortaya çıkarmalıdır. Bu, kamu sözleşmeleri sürdürülde kadar, uygulamanın iç tasarımının zaman içinde gelişmesini sağlar.

### <a name="dependency-inversion"></a>Bağımlılık inversiyon

Uygulama içindeki bağımlılık yönü, uygulama ayrıntıları değil, soyutlama yönünde olmalıdır. Çoğu uygulama, çalışma zamanı yürütme yönünde zaman bağımlılık akışlarını derleyen şekilde yazılır. Bu, doğrudan bağımlılık grafiği üretir. Diğer bir deyişle, A modülü B modülünde bir işlev çağırırsa, c modülünde bir işlev çağırırsa, derleme zamanında A, Şekil 4-1'de gösterildiği gibi C'ye bağlı olacak olan B'ye bağlıdır.

![Doğrudan bağımlılık grafiği](./media/image4-1.png)

**Şekil 4-1.** Doğrudan bağımlılık grafiği.

Bağımlılık inversiyon ilkesinin uygulanması, A'nın B'nin uyguladığı bir soyutlama üzerinde metod lar çağırmasına olanak tanır, bu da A'nın çalışma zamanında B'yi aramasını, ancak B'nin derleme zamanında A tarafından denetlenen bir arabirime (böylece tipik derleme zamanı bağımlılığını *tersine çevirme)* bağlı olmasını sağlar. Çalışma zamanında, program yürütme akışı değişmeden kalır, ancak arabirimlerin giriş bu arabirimlerin farklı uygulamaları kolayca takılabilir anlamına gelir.

![Ters bağımlılık grafiği](./media/image4-2.png)

**Şekil 4-2.** Ters bağımlılık grafiği.

**Bağımlılık ters çevirme,** uygulama ayrıntıları başka bir yol yerine, daha üst düzey soyutlamalara bağlı olacak ve uygulayacak şekilde yazılabilir olduğundan, gevşek birleştirilmiş uygulamalar oluşturmanın önemli bir parçasıdır. Ortaya çıkan uygulamalar daha test edilebilir, modüler ve sonuç olarak korunabilir. *Bağımlılık enjeksiyonu* uygulaması bağımlılık inversiyon prensibini izleyerek mümkün kılınır.

### <a name="explicit-dependencies"></a>Açık bağımlılıklar

**Yöntemler ve sınıflar, düzgün çalışabilmek için ihtiyaç duydukları ortak nesneleri açıkça gerektirmelidir.** Sınıf oluşturucuları, sınıfların geçerli bir durumda olmak ve düzgün bir şekilde çalışabilmeleri için ihtiyaç duydukları şeyleri tanımlamaları için bir fırsat sağlar. Oluşturulabilen ve çağrılabilen, ancak yalnızca belirli genel veya altyapı bileşenleri yerindeyse düzgün çalışacak sınıfları tanımlarsanız, bu sınıflar istemcilerine *karşı dürüst olmaktan* değildir. Oluşturucu sözleşme yalnızca belirtilen şeyler (sınıf sadece parametresiz bir yapıcı kullanıyorsa muhtemelen hiçbir şey) ihtiyacı istemci söylüyor, ama sonra çalışma zamanında nesne gerçekten başka bir şey ihtiyacı olduğu ortaya çıkıyor.

Açık bağımlılıklar ilkesini izleyerek, sınıflarınız ve yöntemleriniz, işleyebilmek için ihtiyaç duydukları şey konusunda müşterilerine karşı dürüst oluyorlar. Bu, kodunuzu daha kendi kendine belgeleme ve kodlama sözleşmelerinizi daha kullanıcı dostu hale getirir, çünkü kullanıcılar yöntem veya yapıcı parametreleri şeklinde gerekli olan şeyi sağladıkları sürece, çalıştıkları nesnelerin çalışacağına güvenirler çalışma zamanında doğru bir şekilde.

### <a name="single-responsibility"></a>Tek sorumluluk

Tek sorumluluk ilkesi nesne yönelimli tasarım için geçerlidir, ancak aynı zamanda kaygıların ayrılmasına benzer bir mimari ilke olarak da düşünülebilir. Nesnelerin tek bir sorumluluğu olması gerektiğini ve değişmek için tek bir nedenleri olması gerektiğini belirtir. Özellikle, nesnenin değişmesi gereken tek durum, tek bir sorumluluğu gerçekleştirme biçiminin güncellenmesi gerektiğidir. Bu ilkeyi izleyerek daha gevşek birleştirilmiş ve modüler sistemler üretmek için yardımcı olur, yeni davranış birçok türde yeni sınıflar olarak uygulanabilir, yerine mevcut sınıflara ek sorumluluk ekleyerek. Yeni sınıflar eklemek, henüz yeni sınıflara bağlı olmadığından, varolan sınıfları değiştirmekten her zaman daha güvenlidir.

Yekpare bir uygulamada, uygulamadaki katmanlara yüksek düzeyde tek sorumluluk ilkesini uygulayabiliriz. Sunum sorumluluğu UI projesinde kalırken, veri erişim sorumluluğu bir altyapı projesi içinde tutulmalıdır. İş mantığı, kolayca test edilebildiği ve diğer sorumluluklardan bağımsız olarak gelişebildiği uygulama temel projesinde tutulmalıdır.

Bu ilke uygulama mimarisine uygulandığında ve mantıksal bitiş noktasına alındığında, mikro hizmetler alırsınız. Belirli bir mikro hizmetin tek bir sorumluluğu olmalıdır. Bir sistemin davranışını genişletmeniz gerekiyorsa, varolan bir sisteme sorumluluk eklemek yerine ek mikro hizmetler ekleyerek bunu yapmak genellikle daha iyidir.

[Mikro hizmetler mimarisi hakkında daha fazla bilgi edinin](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Kendinizi tekrar etmeyin (DRY)

Uygulama, sık karşılaşılan bir hata kaynağı olduğundan, belirli bir kavramla ilgili davranışı birden çok yerde belirtmekten kaçınmalıdır. Bir noktada, gereksinimlerde bir değişiklik bu davranışın değiştirilmesini gerektirir ve davranışın en az bir örneğinin güncelleştirileme olasılığı sistemin tutarsız davranışına neden olur.

Mantığı çoğaltmak yerine, bir programlama yapısına dahil edin. Bu yapıyı bu davranış üzerinde tek bir yetki oluşturmayı ve bu davranışı gerektiren uygulamanın başka bir bölümünün yeni yapıyı kullanmasını sağlayabilir.

> [!NOTE]
> Yalnızca tesadüfen yinelenen birlikte davranışı bağlamaktan kaçının. Örneğin, iki farklı sabitin her ikisinin de aynı değere sahip olması, kavramsal olarak farklı şeylere atıfta bulunarak yalnızca bir sabitiniz olması gerektiği anlamına gelmez.

### <a name="persistence-ignorance"></a>Sebat cehalet

**Kalıcılık cehaleti** (PI), kalıcı olması gereken, ancak kodu kalıcılık teknolojisinin seçiminden etkilenmeyen türleri ifade eder. .NET'teki bu tür türler bazen Düz Eski CLR Nesneleri (POCOs) olarak adlandırılır, çünkü belirli bir taban sınıftan devralmaları veya belirli bir arabirim uygulamaları gerekmez. Aynı iş modelinin birden fazla şekilde devam etmesine izin verdiği için kalıcı lık cehaleti değerlidir ve uygulamaya ek esneklik sağlar. Kalıcılık seçenekleri zaman içinde değişebilir, bir veritabanı teknolojisinden diğerine veya uygulamanın başladığı şeye ek olarak ek kalıcılık biçimleri gerekebilir (örneğin, bir Redis önbelleği veya Azure Cosmos DB'si ilişkisel veritabanı).

Bu ilkenin ihlaline örnek olarak şunlar verilebilir:

- Gerekli bir taban sınıf.

- Gerekli bir arayüz uygulaması.

- Kendilerini kaydetmekten sorumlu sınıflar (Etkin Kayıt deseni gibi).

- Gerekli parametresiz yapıcı.

- Sanal anahtar kelime gerektiren özellikler.

- Kalıcılığa özgü gerekli öznitelikler.

Sınıfların yukarıdaki özelliklerden veya davranışlardan herhangi birine sahip olması gereksinimi, kalıcılık teknolojisinin seçimi ile kalıcılık teknolojisinin seçimi arasındaki bağlantıyı ekler ve gelecekte yeni veri erişim stratejilerinin benimsenmesini zorlaştırır.

### <a name="bounded-contexts"></a>Sınırlı bağlamlar

**Sınırlı bağlamlar** Etki Alanı Odaklı Tasarım'da merkezi bir desendir. Büyük uygulamalarda veya kuruluşlarda karmaşıklığı ayrı kavramsal modüllere ayırarak karmaşıklıkla başa çıkmanın bir yolunu sağlarlar. Her kavramsal modül daha sonra diğer bağlamlardan (dolayısıyla sınırlanmış) ayrılan ve bağımsız olarak evrimleşebilen bir bağlamı temsil eder. Her sınırlı bağlam ideal olarak içindeki kavramlar için kendi adlarını seçmekte özgür olmalı ve kendi kalıcılık deposuna özel erişime sahip olmalıdır.

En azından, tek tek web uygulamaları, diğer uygulamalarla bir veritabanı paylaşmak yerine, kendi iş modeli için kendi kalıcılık deposu ile kendi sınırlı bağlamı olmak için çaba göstermelidir. Sınırlı bağlamlar arasındaki iletişim, iş mantığının ve olayların gerçekleşen değişikliklere yanıt olarak gerçekleşmesine olanak tanıyan paylaşılan bir veritabanı yerine programlı arabirimler aracılığıyla gerçekleşir. Sınırlı bağlamlar, ideal olarak kendi bireysel sınırlı bağlamları olarak da uygulanan mikro hizmetlerle yakından eşlenir.

## <a name="additional-resources"></a>Ek kaynaklar

- [JAVA Tasarım Desenleri: İlkeler](https://java-design-patterns.com/principles/)
- [Sınırlı Bağlam](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Önceki](choose-between-traditional-web-and-single-page-apps.md)
>[Sonraki](common-web-application-architectures.md)
