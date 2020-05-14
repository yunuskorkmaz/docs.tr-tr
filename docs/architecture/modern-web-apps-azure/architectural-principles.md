---
title: Mimari ilkeleri
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın Mimari ilkeler
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: a3444071abae89780304a9687e486f3842283a33
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396240"
---
# <a name="architectural-principles"></a>Mimari ilkeleri

> "Oluşturucular, programcıların programlar yazdığı şekilde bina gerçekleştirmişse, birlikte gelen ilk Woodpecker, Civil 'ı yok eder."  
> _\-Gerald Weinberg_

Bakım yaparken yazılım çözümlerini mimariyle mimarın ve tasarlayabilmelisiniz. Bu bölümde özetlenen ilkeler, temiz ve sürdürülebilir uygulamalara yol açacak mimari kararlara kılavuzluk etmenize yardımcı olabilir. Genellikle, bu ilkeler, uygulamanızın diğer bölümlerine sıkı bir şekilde bağlı olmayan, ancak açık arabirimler veya mesajlaşma sistemleri aracılığıyla iletişim kuran ayrık bileşenlerden uygulamalar oluşturmaya nasıl kılavuzluk eder.

## <a name="common-design-principles"></a>Ortak tasarım ilkeleri

### <a name="separation-of-concerns"></a>Kaygıları ayırma

Geliştirme, **kaygılara ayrımı**olduğunda bir temel ilke. Bu ilke, yazılımın gerçekleştirdiği iş türlerine göre ayrılması gerektiğini onaylar. Örneğin, kullanıcıya görüntülenecek önemli öğeleri tanımlamaya yönelik mantığı ve bu tür öğeleri daha dikkat çekici hale getirmek için belirli bir şekilde biçimlendiren bu uygulamayı düşünün. Bu davranışlar yalnızca birbirleriyle ilişkili olan ayrı sorunlar olduğundan, hangi öğelerin biçimlendirileceğini seçmekten sorumlu davranış, öğelerin biçimlendirmesinden sorumlu olan davranışlardan ayrı tutulmalıdır.

Mimari türsel uygulamalar, temel iş davranışını altyapı ve Kullanıcı arabirimi mantığından ayırarak bu ilkeyi izlemek üzere mantıksal olarak derlenebilir. İdeal olarak, iş kuralları ve Logic, uygulamadaki diğer projelere bağlı olmaması gereken ayrı bir projede yer almalıdır. Bu ayrım, iş modelinin test etmek kolay olduğundan ve alt düzey uygulama ayrıntılarına sıkı bir şekilde ayrılmadan gelişebilmenizi sağlamaya yardımcı olur. Kaygıları ayrımı, uygulama mimarilerinde katmanların kullanımı arkasında önemli bir noktadır.

### <a name="encapsulation"></a>Kapsül

Uygulamanın farklı bölümlerinin uygulamanın diğer bölümlerinden yalıtılmış olması için **kapsülleme** kullanması gerekir. Dış sözleşmelerin ihlal olmaması koşuluyla, uygulama bileşenleri ve katmanları, kendi ortak bileşenlerini bozmadan iç uygulamasını ayarlayabilmelidir. Doğru kapsülleme kullanımı, nesne ve paketlerin farklı uygulamalarla değiştirilmesini sağlamak için uygulama tasarımlarında gevşek Pave modülerlik sağlamaya yardımcı olur.

Sınıflarda, sınıfın iç durumuna erişimi dışarıdan kısıtlamak için kapsülleme elde edilir. Bir dış aktör nesnenin durumunu işlemek istiyorsa, nesnenin özel durumuna doğrudan erişim sağlamak yerine iyi tanımlanmış bir işlev (veya özellik ayarlayıcısı) aracılığıyla bunu yapması gerekir. Benzer şekilde, uygulama bileşenlerinin ve uygulamaların kendisi, durumunun doğrudan değiştirilmesine izin vermek yerine, kendi ortak çalışanları için iyi tanımlanmış arabirimler kullanıma sunmalıdır. Bu, uygulamanın dahili tasarımını zaman içinde geliştikçe, genel sözleşmelerin bakımını yaptığı sürece iş çalışanları kesintiye uğratır.

### <a name="dependency-inversion"></a>Bağımlılık Inversion

Uygulamanın içindeki bağımlılığın yönü, uygulama ayrıntıları değil soyutlama yönünde olmalıdır. Çoğu uygulama, derleme zamanı bağımlılık akışları çalışma zamanı yürütme yönünde yazılır ve doğrudan bağımlılık grafiği üretir. Diğer bir deyişle, A modülü C modülünde bir işlevi çağıran Modül B 'de bir işlev çağırırsa, sonra da şekil 4-1 ' de gösterildiği gibi C 'ye bağlı olan B 'ye bağlı olur.

![Doğrudan bağımlılık grafiği](./media/image4-1.png)

**Şekil 4-1.** Doğrudan bağımlılık grafiği.

Bağımlılık Inversion ilkesini uygulamak, bir soyutlamalarda b 'nin uyguladığı bir soyutlama üzerinde Yöntemler çağırmasının yanı, bir A 'nın çalışma zamanında B çağrısı yapmasını olanaklı hale getirir, ancak B için derleme zamanında bir tarafından denetlenen arabirime bağımlı olur (Bu nedenle, tipik derleme zamanı bağımlılığını *tersine çevirme* ). Çalışma zamanında, program yürütme akışı değişmeden kalır, ancak arabirimlerin tanıtımı bu arabirimlerin farklı uygulamalarının kolayca takılmasına yol açabilir.

![Ters bağımlılık grafiği](./media/image4-2.png)

**Şekil 4-2.** Ters bağımlılık grafiği.

**Bağımlılık Inversion** , gevşek olarak bağlanmış uygulamalar oluşturmanın önemli bir parçasıdır. bu sayede uygulama ayrıntıları, diğer bir yöntem yerine daha yüksek düzeyli soyutlamalar uygulamak üzere yazılabilir. Elde edilen uygulamalar daha kararlı, modüler ve sonuç olarak sürdürülebilir. Bağımlılık/sürüm prensibi ile *bağımlılık ekleme* yöntemi mümkündür.

### <a name="explicit-dependencies"></a>Açık bağımlılıklar

**Yöntemler ve sınıflar, doğru çalışması için ihtiyaç duydukları tüm işbirliği nesneleri açıkça gerektirmelidir.** Sınıf oluşturucular, sınıfların geçerli bir durumda olması ve düzgün çalışması için ihtiyaç duydukları şeyleri belirlemesine yönelik bir fırsat sağlar. Oluşturulabilecek ve çağrılabilen sınıflar tanımlarsanız ancak bu, yalnızca belirli küresel veya altyapı bileşenleri mevcutsa düzgün şekilde çalışır, ancak bu sınıflar *istemcilerle birlikte kabul* edilir. Oluşturucu sözleşmesi, istemciye yalnızca belirtilen şeyleri (sınıf parametresiz bir Oluşturucu kullanıyorsa Nothing) ister, daha sonra çalışma zamanında nesneyi, başka bir şeye ihtiyaç duyması durumunda olduğunu bildiriyor.

Açık bağımlılıklar ilkesini izleyerek, sınıflarınız ve yöntemleriniz, işlevleri çalışması için ihtiyaç duydukları gibi istemcilerle birlikte kullanılır. İlkeyi takip etmek, kodunuzun daha kolay belgelenme ve kodlamanızı daha kolay bir şekilde sunduğundan, kullanıcılar Yöntem veya Oluşturucu parametreleri biçiminde gerekli olanları sağladıklarında, birlikte çalıştıkları nesneler çalışma zamanında doğru şekilde davranır.

### <a name="single-responsibility"></a>Tek sorumluluk

Tek sorumluluk ilkesi, nesne odaklı tasarım için geçerlidir, ancak sorunların ayrılılmasına benzer bir mimari prensibi olarak da düşünülebilir. Nesnelerin yalnızca bir sorumluluğu olması gerektiğini ve yalnızca bir sorumluluğun olması gerektiğini belirtir. Özellikle, nesnenin değiştirilmesi gereken tek durum, bir sorumluluğu tek bir sorumluluğu gerçekleştirmelidir. Bu prensibi, daha gevşek bir şekilde bağlanmış ve modüler sistemler oluşturulmasına yardımcı olur, çünkü birçok yeni davranış, mevcut sınıflara ek sorumluluk eklemek yerine yeni sınıflar olarak uygulanırlar. Yeni sınıflar eklemek, hiçbir kod henüz yeni sınıflara bağlı olmadığından, her zaman var olan sınıfları değiştirmekle daha güvenlidir.

Tek parçalı bir uygulamada, tek sorumluluk ilkesini uygulamadaki katmanlara yüksek düzeyde uygulayabiliriz. Sunum sorumluluğu, veri erişimi sorumluluğunun bir altyapı projesi içinde tutulması gerektiği sırada, Kullanıcı arabirimi projesinde kalmalıdır. İş mantığı, kolayca test edileceği ve diğer sorumluluklardan bağımsız olarak gelişebilecekleri uygulama çekirdeği projesinde tutulmalıdır.

Bu ilke uygulama mimarisine uygulandığında ve mantıksal uç noktasına götürülürsünüz, mikro hizmetleri alırsınız. Belirli bir mikro hizmet tek bir sorumluluğa sahip olmalıdır. Bir sistemin davranışını genişletmenize ihtiyacınız varsa, var olan bir sorumluluğu eklemek yerine daha fazla mikro hizmet ekleyerek bunu yapmak genellikle daha iyidir.

[Mikro hizmet mimarisi hakkında daha fazla bilgi edinin](https://aka.ms/MicroservicesEbook)

### <a name="dont-repeat-yourself-dry"></a>Kendinizi yinelemeyin (kuru)

Uygulama, sık karşılaşılan hataların bir kaynağı olduğundan, birden çok yerde belirli bir kavram ile ilgili davranışları belirtmekten kaçınmalıdır. Bir noktada, gereksinimlerde bir değişiklik bu davranışın değiştirilmesini gerektirir. Büyük olasılıkla davranışın en az bir örneği güncelleştirilemeyebilir ve sistem tutarsız şekilde davranır.

Mantığı çoğaltmak yerine bir programlama yapısında kapsülleyebilirsiniz. Bu davranış üzerinde tek bir yetki oluşturun ve uygulamanın bu davranışı gerektiren başka bir bölümü yeni yapıyı kullanın.

> [!NOTE]
> Yalnızca tesadüfen yinelenen bir davranışı bağlamaktan kaçının. Örneğin, yalnızca iki farklı sabit değerin aynı değere sahip olması nedeniyle, kavramsal olarak farklı şeylere başvurduklarında yalnızca bir sabit değeri olması gerekir.

### <a name="persistence-ignorance"></a>Kalıcılık Ignorance

**Kalıcılık Ignorance** (PI), kalıcı olması gereken türlere başvurur, ancak kodu Kalıcılık teknolojisi seçimi tarafından etkilenmemiştir. .NET 'teki bu tür türler, belirli bir temel sınıftan devralması veya belirli bir arabirim uygulamak zorunda olmadıkları için bazen düz eski CLR nesneleri (POCOs) olarak adlandırılır. Aynı iş modelinin birden çok şekilde kalıcı olmasını sağladığından, uygulama için ek esneklik sunarak Kalıcılık kalıcılığı önem taşır. Kalıcılık seçimleri zaman içinde, bir veritabanı teknolojisinden diğerine değişebilir ya da uygulamanın başladığı her şeyi (örneğin, bir Redsıs önbelleği veya bir ilişkisel veritabanına ek olarak Azure Cosmos DB) ek olarak başka Kalıcılık biçimleri de gerekebilir.

Bu ilkeye yönelik ihlallere örnek olarak şunlar verilebilir:

- Gerekli bir temel sınıf.

- Gerekli bir arabirim uygulamasıdır.

- Kendilerini kaydetmekten sorumlu sınıflar (örneğin, etkin kayıt deseninin).

- Parametresiz Oluşturucu gerekli.

- Sanal anahtar sözcük gerektiren özellikler.

- Kalıcılığa özgü gerekli öznitelikler.

Sınıfların yukarıdaki özelliklerden veya davranışların herhangi birine sahip olması, kalıcı hale getirilmesi gereken türler ve kalıcılık teknolojileri seçimi arasında bir kuponu ekleyerek yeni veri erişim stratejilerini daha da benimsemeyi daha kolay hale getirir.

### <a name="bounded-contexts"></a>Sınırlanmış bağlamlar

**Sınırlanmış bağlamlar** , etki alanı odaklı tasarımda merkezi bir modeldir. Bu kişiler, büyük uygulamalarda veya kuruluşlarda, farklı kavramsal modüllere kadar bölmek için bir yol sağlar. Her kavramsal modül daha sonra diğer bağlamlardan ayrılan (Bu nedenle, sınırlı) bir bağlamı temsil eder ve bağımsız olarak gelişebilirler. Her sınırlanmış bağlam, içindeki kavramlar için kendi adlarını seçmek üzere ideal olmalıdır ve kendi kalıcılık deposuna özel erişime sahip olmalıdır.

En azından, bireysel Web uygulamaları, bir veritabanını diğer uygulamalarla paylaşmak yerine kendi iş modeliyle ilgili kendi Kalıcılık depolarıyla birlikte kendi sınırlı bağlamlarına sahip olmaya devam etmelidir. Sınırlanmış bağlamlar arasındaki iletişim, paylaşılan bir veritabanı yerine, iş mantığı ve olayların gerçekleşen değişikliklere yanıt olarak gerçekleşmesini sağlayan, paylaşılan bir veritabanı yerine programlı arabirimler aracılığıyla oluşur. Sınırlanmış bağlamlar, mikro hizmetlere yakın bir şekilde eşlenir ve ayrıca kendi kendine sınırlanmış bağlamlar olarak ideal şekilde uygulanır.

## <a name="additional-resources"></a>Ek kaynaklar

- [JAVA tasarım desenleri: Ilkeler](https://java-design-patterns.com/principles/)
- [Sınırlanmış bağlam](https://martinfowler.com/bliki/BoundedContext.html)

>[!div class="step-by-step"]
>[Önceki](choose-between-traditional-web-and-single-page-apps.md) 
> [Sonraki](common-web-application-architectures.md)
