---
title: Ortak web uygulaması mimarileri
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | Ortak web uygulama mimarilerini keşfedin
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9a8e9450d81ac2e63a8c8ea54592ed81e646e05
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988134"
---
# <a name="common-web-application-architectures"></a>Ortak web uygulaması mimarileri

> "İyi mimarinin pahalı olduğunu düşünüyorsanız, kötü mimariyi deneyin."  
> _- Brian Foote ve Joseph Yoder_

Geleneksel .NET uygulamalarının çoğu, tek bir IIS appetki alanında çalışan yürütülebilir veya tek bir web uygulamasına karşılık gelen tek birimler olarak dağıtılır. Bu en basit dağıtım modelidir ve birçok iç ve küçük genel uygulamalara çok iyi hizmet vermektedir. Ancak, bu tek dağıtım birimi göz önüne alındığında bile, önemsiz olmayan iş uygulamalarının çoğu birkaç katmana bazı mantıksal ayırmadan yararlanır.

## <a name="what-is-a-monolithic-application"></a>Yekpare uygulama nedir?

Yekpare bir uygulama, davranışı açısından tamamen kendi kendine yeten bir uygulamadır. İşlemlerini gerçekleştirirken diğer hizmetler veya veri depolarıyla etkileşimkurabilir, ancak davranışının özü kendi işlemi içinde çalışır ve uygulamanın tamamı genellikle tek bir birim olarak dağıtılır. Böyle bir uygulamanın yatay olarak ölçeklendirmesi gerekiyorsa, genellikle uygulamanın tamamı birden çok sunucu veya sanal makineler arasında çoğaltılır.

## <a name="all-in-one-applications"></a>Hepsi bir e-bir uygulamalar

Bir uygulama mimarisi için mümkün olan en küçük proje sayısı biridir. Bu mimaride, uygulamanın tüm mantığı tek bir projede bulunur, tek bir derlemeye derlenir ve tek bir birim olarak dağıtılır.

Visual Studio'da veya komut satırından oluşturulan yeni bir ASP.NET Core projesi, basit bir "hepsi bir arada" monolit olarak başlar. Sunu, iş ve veri erişim mantığı da dahil olmak üzere uygulamanın tüm davranışını içerir. Şekil 5-1 tek projeli bir uygulamanın dosya yapısını gösterir.

![Core uygulaması ASP.NET tek bir proje](./media/image5-1.png)

**Şekil 5-1.** Core uygulaması ASP.NET tek bir proje.

Tek bir proje senaryosunda, klasörler aracılığıyla giderme sağlanır. Varsayılan şablon, Modeller, Görünümler ve Denetleyicilerin MVC desen sorumlulukları için ayrı klasörlerin yanı sıra Veri ve Hizmetler için ek klasörler içerir. Bu düzenlemede, sunu ayrıntıları Görünümler klasörüne mümkün olduğunca sınırlandırılmalı ve veri erişimi uygulama ayrıntıları Veri klasöründe tutulan sınıflar ile sınırlandırılmalıdır. İş mantığı, Modeller klasöründeki hizmetlerde ve sınıflarda yer almalıdır.

Basit olmasına rağmen, tek projeye sahip monolitik çözümün bazı dezavantajları vardır. Projenin boyutu ve karmaşıklığı arttıkça, dosya ve klasör sayısı da artmaya devam edecektir. Kullanıcı arabirimi (UI) endişeleri (modeller, görünümler, denetleyiciler) alfabetik olarak gruplandırılmadı birden çok klasörde bulunur. Bu sorun, filtreler veya ModelBinders gibi ek UI düzeyi yapıları kendi klasörlerine eklendiğinde daha da kötüleşir. İş mantığı Modeller ve Hizmetler klasörleri arasında dağılmış durumda dır ve hangi klasörlerin hangi sınıflarda kime bağlı olması gerektiğine dair net bir belirti yoktur. Proje düzeyinde organizasyon bu eksikliği sık sık [spagetti koduna](https://deviq.com/spaghetti-code/)yol açar.

Bu sorunları gidermek için, uygulamalar genellikle her projenin uygulamanın belirli bir _katmanında_ bulunduğu düşünülen çok projeli çözümlere dönüşür.

## <a name="what-are-layers"></a>Mantıksal katman nedir?

Uygulamalar karmaşıklık içinde büyüdükçe, bu karmaşıklığı yönetmenin bir yolu, uygulamanın sorumluluklarını veya endişelerine göre parçalamaktır. Bu, endişelerin ayrılması ilkesini izler ve geliştiricilerin belirli işlevlerin uygulandığı yeri kolayca bulabilmeleri için büyüyen bir kod tabanının düzenli tutulmasına yardımcı olabilir. Katmanlı mimari olsa da, sadece kod organizasyonu ötesinde bir dizi avantaj sunar.

Kodu katmanlar halinde düzenleyerek, ortak alt düzey işlevsellik uygulama boyunca yeniden kullanılabilir. Bu yeniden kullanım yararlıdır, çünkü daha az kod yazılması gerektiği anlamına gelir ve uygulamanın [kendinizi tekrarlama (DRY)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) ilkesini takiben tek bir uygulamada standartlaşmasına izin verebilir.

Katmanlı bir mimariyle, uygulamalar katmanların diğer katmanlarla iletişim kurabileceği kısıtlamaları zorlayabilir. Bu kapsülleme elde etmek için yardımcı olur. Bir katman değiştirildiğinde veya değiştirildiğinde, yalnızca onunla çalışan katmanlar etkilenmelidir. Hangi katmanların diğer katmanlara bağlı olduğunu sınırlayarak, tek bir değişikliğin tüm uygulamayı etkilememesi için değişikliklerin etkisi azaltılabilir.

Katmanlar (ve kapsülleme) uygulama içindeki işlevselliği değiştirmeyi çok daha kolay hale getirir. Örneğin, bir uygulama başlangıçta kalıcılık için kendi SQL Server veritabanını kullanabilir, ancak daha sonra bulut tabanlı kalıcılık stratejisini veya bir web API'sinin arkasındakini kullanmayı seçebilir. Uygulama kalıcılık uygulamasını mantıksal bir katman içinde düzgün bir şekilde kapsüllemişse, sql server özel katmanı aynı ortak arabirimi uygulayan yeni bir katmanla değiştirilebilir.

Gereksinimleri gelecekteki değişikliklere yanıt olarak uygulamaları takas potansiyeline ek olarak, uygulama katmanları da daha kolay test amacıyla uygulamaları takas yapabilirsiniz. Uygulamanın gerçek veri katmanına veya Kullanıcı Arabirimi katmanına karşı çalışan testler yazmak yerine, bu katmanlar test zamanında isteklere bilinen yanıtları sağlayan sahte uygulamalarla değiştirilebilir. Bu genellikle, uygulamanın gerçek altyapısına karşı testleri çalıştırmayla karşılaştırıldığında, testlerin yazılması çok daha kolay ve çalıştırılması çok daha hızlı hale getirir.

Mantıksal katmanlama, kurumsal yazılım uygulamalarında kod organizasyonunu geliştirmek için yaygın bir tekniktir ve kodun katmanlar halinde düzenlenebileceği çeşitli yöntemler vardır.

> [!NOTE]
 > _Katmanlar_ uygulama içinde mantıksal ayırmayı temsil ediyor. Uygulama mantığının ayrı sunuculara veya işlemlere fiziksel olarak dağıtılması durumunda, bu ayrı fiziksel dağıtım hedefleri _katmanlar_olarak adlandırılır. Tek bir katmana dağıtılan bir N-Layer uygulamasına sahip olmak mümkündür ve oldukça yaygındır.

## <a name="traditional-n-layer-architecture-applications"></a>Geleneksel "N-Layer" mimari uygulamaları

Uygulama mantığının katmanlar halinde en yaygın organizasyonu Şekil 5-2'de gösterilmiştir.

![Tipik uygulama katmanları](./media/image5-2.png)

**Şekil 5-2.** Tipik uygulama katmanları.

Bu katmanlar genellikle UI, BLL (Business Logic Layer) ve DAL (Data Access Layer) olarak kısaltılır. Bu mimariyi kullanarak, kullanıcılar yalnızca BLL ile etkileşime giren Kullanıcı Arası Tümcülleri katmanı aracılığıyla istekte bulunun. BLL, buna karşılık, veri erişim istekleri için DAL'yi arayabilir. UI katmanı DAL'a doğrudan herhangi bir istekte bulunamaz ve diğer yollarla kalıcılıkla doğrudan etkileşime girmemelidir. Aynı şekilde, BLL sadece DAL geçerek sebat ile etkileşim gerekir. Bu şekilde, her katmanın kendi bilinen sorumluluğu vardır.

Bu geleneksel katmanlama yaklaşımının bir dezavantajı derleme zaman bağımlılıkları yukarıdan aşağıya doğru çalıştırmak olduğunu. Diğer bir de, UI katmanı DAL'a bağlı olan BLL'ye bağlıdır. Bu, genellikle uygulamada en önemli mantığı tutan BLL'nin veri erişimi uygulama ayrıntılarına (ve genellikle bir veritabanının varlığına) bağlı olduğu anlamına gelir. Böyle bir mimaride iş mantığını sınamak genellikle zordur ve bir test veritabanı gerektirir. Bağımlılık ters çevirme ilkesi, bir sonraki bölümde göreceğiniz gibi, bu sorunu gidermek için kullanılabilir.

Şekil 5-3, uygulamayı sorumluluk (veya katman) ile üç projeye ayırarak örnek bir çözüm gösterir.

![Üç projeile basit bir monolitik uygulama](./media/image5-3.png)

**Şekil 5-3.** Üç projeile basit bir monolitik uygulama.

Bu uygulama kuruluş amaçları için çeşitli projeler kullansa da, yine de tek bir birim olarak dağıtılır ve istemcileri tek bir web uygulaması olarak bu uygulamayla etkileşime girecektir. Bu çok basit dağıtım işlemi sağlar. Şekil 5-4, böyle bir uygulamanın Azure kullanılarak nasıl barındırılan olabileceğini gösterir.

![Azure Web Uygulamasının basit dağıtımı](./media/image5-4.png)

**Şekil 5-4.** Azure Web Uygulamasının basit dağıtımı

Uygulama gereksinimleri arttıkça, daha karmaşık ve sağlam dağıtım çözümleri gerekebilir. Şekil 5-5, ek yetenekleri destekleyen daha karmaşık bir dağıtım planı nın bir örneğini gösterir.

![Bir Azure Uygulama Hizmetine web uygulaması dağıtma](./media/image5-5.png)

**Şekil 5-5.** Bir Azure Uygulama Hizmetine web uygulaması dağıtma

Dahili olarak, bu projenin sorumluluk temel alınarak birden fazla projeye dönüştürülmesi, uygulamanın sürdürülebilirliğini artırır.

Bu birim, bulut tabanlı isteğe bağlı ölçeklenebilirlik avantajlarından yararlanmak için ölçeklendirilebilir veya çıkarılabilir. Ölçekleme, uygulamanızı barındıran sunucuya ek CPU, bellek, disk alanı veya başka kaynaklar eklemek anlamına gelir. Ölçekleme, ister fiziksel sunucular, ister sanal makineler veya kapsayıcılar olsun, bu tür sunucuların ek örnekleri eklemek anlamına gelir. Uygulamanız birden çok örnekte barındırıldığında, tek tek uygulama örneklerine istek atamak için bir yük dengeleyicisi kullanılır.

Azure'da bir web uygulamasını ölçeklemenin en basit yaklaşımı, uygulamanın Uygulama Hizmet Planı'nda ölçekleme işlemlerini el ile yapılandırmaktır. Şekil 5-6, bir uygulamaya kaç örnek sunulur yapılandırmak için uygun Azure pano ekranını gösterir.

![Azure'da Uygulama Hizmet Planı ölçekleme](./media/image5-6.png)

**Şekil 5-6.** Azure'da Uygulama Hizmet Planı ölçekleme.

## <a name="clean-architecture"></a>Temiz mimari

Bağımlılık Inversion İlke'sinin yanı sıra Etki Alanı Odaklı Tasarım (DDD) ilkelerini izleyen uygulamalar da benzer bir mimariye ulaşma eğilimindedir. Bu mimari yıllar içinde birçok isim le gitti. İlk isimlerden biri Altıgen Mimari, onu Ports-and-Adapters izledi. Daha yakın zamanda, [Soğan Mimarisi](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) veya [Temiz Mimari](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)olarak belirtilmiştir. İkinci adı, Temiz Mimari, bu e-kitapta bu mimari için ad olarak kullanılır.

eShopOnWeb başvuru uygulaması, kodlarını projelere dönüştürmede Temiz Mimari yaklaşımını kullanır. [Ardalis/cleanarchitecture](https://github.com/ardalis/cleanarchitecture) GitHub deposunda kendi ASP.NET Core'unuz için başlangıç noktası olarak kullanabileceğiniz bir çözüm şablonu bulabilirsiniz.

Temiz mimari, iş mantığını ve uygulama modelini uygulamanın merkezine yerletir. İş mantığının veri erişimine veya diğer altyapı kaygılarına bağlı olması yerine, bu bağımlılık tersine çevrilmiş tir: altyapı ve uygulama ayrıntıları Uygulama Çekirdeğine bağlıdır. Bu, Uygulama Çekirdeği'nde, altyapı katmanında tanımlanan türler tarafından uygulanan soyutlamaları veya arabirimleri tanımlayarak elde edilir. Bu mimarigörselleştirme ortak bir yolu, bir soğan benzer eşmerkezli daireler bir dizi kullanmaktır. Şekil 5-7 mimari temsil bu stilin bir örnek gösterir.

![Temiz Mimari; soğan görünümü](./media/image5-7.png)

**Şekil 5-7.** Temiz Mimari; soğan görünümü

Bu diyagramda, bağımlılıklar en içteki daireye doğru akar. Uygulama Çekirdeği adını bu diyagramın merkezindeki konumundan alır. Ve diyagramda Uygulama Çekirdeğinin diğer uygulama katmanlarına hiçbir bağımlılığı olmadığını görebilirsiniz. Uygulamanın varlıkları ve arayüzleri tam merkezdedir. Yalnızca dışarıda, ancak yine de Uygulama Çekirdeği'nde, genellikle iç dairede tanımlanan arabirimleri uygulayan etki alanı hizmetleri bulunur. Uygulama Çekirdeği dışında, hem Kullanıcı UI hem de Altyapı katmanları Uygulama Çekirdeğine bağlıdır, ancak birbirlerine (mutlaka) bağlı değildir.

Şekil 5-8, UI ve diğer katmanlar arasındaki bağımlılığı daha iyi yansıtan daha geleneksel bir yatay katman diyagramı gösterir.

![Temiz Mimari; yatay katman görünümü](./media/image5-8.png)

**Şekil 5-8.** Temiz Mimari; yatay katman görünümü

Düz okların derleme zamanı bağımlılıklarını temsil ettiğini, kesikli ok ise yalnızca çalışma zamanı bağımlılığını temsil ettiğini unutmayın. Temiz mimari ile, Kullanıcı Arabirimi katmanı derleme zamanında Uygulama Çekirdeği'nde tanımlanan arabirimlerle çalışır ve ideal olarak Altyapı katmanında tanımlanan uygulama türleri hakkında bilgi olmamalıdır. Ancak çalışma zamanında, bu uygulama türlerinin uygulamanın yürütülmesi için gerekli olduğundan, bağımlılık enjeksiyonu yoluyla Uygulama Çekirdeği arabirimlerine bağlı olmaları gerekir.

Şekil 5-9, bu önerilere göre üretildiğinde ASP.NET Core uygulamasının mimarisinin daha ayrıntılı bir görünümünü gösterir.

![Temiz Mimari'yi takip eden ASP.NET Temel mimari diyagramı](./media/image5-9.png)

**Şekil 5-9.** Temiz Mimari'yi izleyen ASP.NET Çekirdek mimari diyagramı.

Uygulama Çekirdeği Altyapıya bağlı olmadığından, bu katman için otomatik birim testleri yazmak çok kolaydır. 5-10 ve 5-11 rakamları testlerin bu mimariye nasıl uyduğunu göstermektedir.

![UnitTestCore](./media/image5-10.png)

**Şekil 5-10.** Ünite test Uygulama Çekirdeği izole.

![Entegrasyon Testleri](./media/image5-11.png)

**Şekil 5-11.** Dış bağımlılıklarla altyapı uygulamalarını tümleştirme testi.

Kullanıcı Bira Bilgisi katmanı altyapı projesinde tanımlanan türlere doğrudan bağımlılık taşımadığından, testleri kolaylaştırmak veya değişen uygulama gereksinimlerine yanıt olarak uygulamaları değiştirmek de çok kolaydır. ASP.NET Core'un bağımlılık enjeksiyonu için yerleşik kullanımı ve desteği, bu mimariyi önemsiz olmayan monolitik uygulamaları yapılandırmanın en uygun yolu haline getirir.

Yekpare uygulamalar için Uygulama Çekirdeği, Altyapı ve Kullanıcı Arabirimi projelerinin tümü tek bir uygulama olarak çalıştırılır. Çalışma zamanı uygulama mimarisi Şekil 5-12 gibi görünebilir.

![ASP.NET Temel Mimari 2](./media/image5-12.png)

**Şekil 5-12.** Core uygulamasının çalışma zamanı mimarisiASP.NET bir örnek.

### <a name="organizing-code-in-clean-architecture"></a>Temiz Mimaride Kodu Düzenleme

Temiz Mimari çözümünde, her projenin net sorumlulukları vardır. Bu nedenle, belirli türler her projeye aittir ve sık sık uygun projede bu türlere karşılık gelen klasörler bulacaksınız.

Uygulama Çekirdeği, varlıkları, hizmetleri ve arabirimleri içeren iş modelini tutar. Bu arabirimler, veri erişimi, dosya sistemi erişimi, ağ aramaları gibi Altyapı kullanılarak gerçekleştirilecek işlemler için soyutlamalar içerir. Bazen bu katmanda tanımlanan hizmetlerin veya arabirimlerin, UI veya Altyapı'ya bağımlı olmayan varlık türleri ile çalışması gerekir. Bunlar basit Veri Aktarım Nesneleri (DTOs) olarak tanımlanabilir.

### <a name="application-core-types"></a>Uygulama Çekirdek türleri

- Varlıklar (kalıcı olan iş modeli sınıfları)
- Arabirimler
- Hizmetler
- DTO'lar

Altyapı projesi genellikle veri erişim uygulamalarını içerir. Tipik bir ASP.NET Core web uygulamasında, bu uygulamalar Varlık Çerçevesi (EF) `Migration` DbContext, tanımlanmış tüm EF Core nesneleri ve veri erişimi uygulama sınıflarını içerir. Soyut veri erişim uygulama kodu için en yaygın yolu [Deposu tasarım deseni](https://deviq.com/repository-pattern/)kullanımı ile.

Veri erişim uygulamalarına ek olarak, Altyapı projesi altyapı sorunlarıyla etkileşimde olması gereken hizmetlerin uygulamalarını içermelidir. Bu hizmetler, Uygulama Çekirdeği'nde tanımlanan arabirimleri uygulamalı ve altyapının Uygulama Çekirdeği projesine bir başvurusu olmalıdır.

### <a name="infrastructure-types"></a>Altyapı tipleri

- EF Çekirdek`DbContext`tipleri `Migration`( , )
- Veri erişimi uygulama türleri (Depositories)
- Altyapıya özel hizmetler (örneğin, `FileLogger` veya) `SmtpNotifier`

ASP.NET Core MVC uygulamasındaki kullanıcı arabirimi katmanı, uygulamanın giriş noktasıdır. Bu proje, Uygulama Çekirdeği projesine başvurmalı ve türleri uygulama çekirdeğinde tanımlanan arabirimler aracılığıyla altyapıyla etkileşime girmelidir. UI katmanında Altyapı katmanı türlerine doğrudan anlık veya statik çağrılara izin verilmemelidir.

### <a name="ui-layer-types"></a>UI katman türleri

- Denetleyiciler
- Filtreler
- Görünümler
- Modelleri Görüntüle
- Başlangıç

Başlangıç sınıfı, uygulamayı yapılandırmaktan ve uygulama türlerini arabirimlere kablolamaktan ve bağımlılık enjeksiyonunun çalışma zamanında düzgün çalışmasına izin vermekten sorumludur.

> [!NOTE]
> Yapılandırılan Hizmetlerdeki bağımlılık enjeksiyonunun UI projesinin Startup.cs dosyasına iletebilmesi için, projenin Altyapı projesine başvurması gerekebilir. Bu bağımlılık, en kolay özel bir DI kapsayıcı kullanılarak ortadan kaldırılabilir. Bu örneğin amaçları için, en basit yaklaşım UI projesinin Altyapı projesine başvurmasına izin vermektir.

## <a name="monolithic-applications-and-containers"></a>Monolitik uygulamalar ve kaplar

Tek ve yekpare dağıtım tabanlı Web Uygulaması veya Hizmeti oluşturabilir ve kapsayıcı olarak dağıtabilirsiniz. Uygulama içinde, yekpare olmayabilir, ancak çeşitli kitaplıklar, bileşenler veya katmanlar halinde organize edilebilir. Harici olarak, tek bir işlem, tek bir web uygulaması veya tek bir hizmet gibi tek bir kapsayıcı.

Bu modeli yönetmek için, uygulamayı temsil etmek için tek bir kapsayıcı dağıtın. Ölçeklendirmek için, önünüzde bir yük dengeleyicisi olan ek kopyalar eklemeniz gerekiyor. Basitlik, tek bir kapsayıcıda veya VM'de tek bir dağıtımın yönetilmesinden gelir.

![Şekil 5-13](./media/image5-13.png)

Şekil 5-13'te gösterildiği gibi, her kapsayıcıya birden çok bileşen/kitaplık veya dahili katman ekleyebilirsiniz. Ama, _"bir konteyner bir şey yapar ve tek bir süreç içinde yapar"_ konteyner prensibini izleyerek, yekpare desen bir çatışma olabilir.

Bu yaklaşımın dezavantajı, uygulama büyüyünce ölçeklendirmesini gerektiren bir yaklaşım la gelir. Tüm uygulama ölçekler, gerçekten bir sorun değil. Ancak, çoğu durumda, uygulamanın birkaç bölümü ölçekleme gerektiren boğma noktalarıdır, diğer bileşenler ise daha az kullanılır.

Tipik e-ticaret örneğini kullanarak, ölçeklendirmeniz gereken şey ürün bilgileri bileşenidir. Çok daha fazla müşteri satın almaktan çok ürünlere göz atar. Sepetlerini ödeme ardışık hattını kullanmaktan daha fazla müşteri kullanır. Daha az müşteri yorum ekler veya satın alma geçmişini görüntüleyin. Ve büyük olasılıkla yalnızca tek bir bölgede, içerik ve pazarlama kampanyalarını yönetmesi gereken bir avuç çalışana sahip sinizdir. Yekpare tasarımı ölçeklendirerek, tüm kod birden çok kez dağıtılır.

"Her şeyi ölçeklendir" sorununa ek olarak, tek bir bileşendeki değişiklikler tüm uygulamanın tam olarak yeniden test edilmesini ve tüm örneklerin tam olarak yeniden dağıtılmasını gerektirir.

Yekpare yaklaşım yaygındır ve birçok kuruluş bu mimari yaklaşımla gelişmektedir. Pek çoğu yeterince iyi sonuçlar alırken, diğerleri sınırları zorluyor. Araçlar ve altyapı hizmet odaklı mimariler (SOA) oluşturmak çok zor olduğu için birçok kişi uygulamalarını bu modelde tasarladı ve uygulama büyüyene kadar bu ihtiyacı görmediler. Yekpare yaklaşımın sınırlarını zorlarsanız, uygulamanın kaplardan ve mikro hizmetlerden daha iyi yararlanmasını sağlamak için uygulamayı parçalamak bir sonraki mantıklı adım olabilir.

![Şekil 5-14](./media/image5-14.png)

Microsoft Azure'da yekpare uygulamaları dağıtmak her örnek için özel VM'ler kullanılarak elde edilebilir. [Azure Sanal Makine Ölçek Kümelerini](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)kullanarak, Sanal Makineler'i kolayca ölçeklendirebilirsiniz. [Azure Uygulama Hizmetleri,](https://azure.microsoft.com/services/app-service/) VM'leri yönetmek zorunda kalmadan yekpare uygulamalar çalıştırabilir ve örnekleri kolayca ölçeklendirebilir. Azure Uygulama Hizmetleri, dağıtımı basitleştirerek docker kapsayıcılarının tek örneklerini de çalıştırabilir. Docker'ı kullanarak, docker ana bilgisayar olarak tek bir VM dağıtabilir ve birden çok örnek çalıştırabilirsiniz. Şekil 5-14'te gösterildiği gibi Azure dengeleyicisini kullanarak ölçeklemayı yönetebilirsiniz.

Çeşitli ana bilgisayarlara dağıtım geleneksel dağıtım teknikleri ile yönetilebilir. Docker ana bilgisayarları, docker **run** gibi komutlarla el ile çalıştırılabilir veya Sürekli Teslimat (CD) ardışık hatları gibi otomasyon yoluyla yönetilebilir.

### <a name="monolithic-application-deployed-as-a-container"></a>Konteyner olarak dağıtılan monolitik uygulama

Yekpare uygulama dağıtımlarını yönetmek için kapsayıcıları kullanmanın yararları vardır. Kapsayıcı örneklerini ölçekleme, ek VM'leri dağıtmaktan çok daha hızlı ve kolaydır. Sanal makine ölçek kümelerini VM'leri ölçeklendirmek için kullanırken bile, örneğin ilerler. Uygulama örnekleri olarak dağıtıldığında, uygulamanın yapılandırması VM'nin bir parçası olarak yönetilir.

Docker görüntüleri olarak güncellemeleri dağıtmak çok daha hızlı ve ağ verimlidir. Docker Images genellikle saniyeler içinde başlar ve hızlı bir şekilde piyasaya çıkar. Docker örneğini yıkmak, genellikle bir saniyeden kısa sürede tamamlayan bir `docker stop` komut vermek kadar kolaydır.

Kapsayıcılar doğuştan tasarım alabildiği için bozuk VM'ler hakkında endişelenmenize gerek yoktur, ancak güncelleştirme komut dosyaları diskte bırakılan belirli bir yapılandırma yı veya dosyayı hesaba kaçıklamayı unutabilir.

Daha basit web uygulamalarının yekpare dağıtımı için Docker kapsayıcılarını kullanabilirsiniz. Bu, sürekli tümleştirme ve sürekli dağıtım ardışık hatlarını geliştirir ve dağıtımdan üretime başarı elde etmeye yardımcı olur. Artık "Makinemde çalışıyor, neden üretimde çalışmıyor?"

Mikro hizmetler tabanlı bir mimarinin birçok faydası vardır, ancak bu avantajlar karmaşıklığın artmasının bir bedeli dir. Bazı durumlarda, maliyetler avantajlardan daha ağır bastığından, tek bir kapsayıcıda veya yalnızca birkaç kapsayıcıda çalışan yekpare bir dağıtım uygulaması daha iyi bir seçenektir.

Yekpare bir uygulama, iyi ayrılmış mikro hizmetlere kolayca ayrıştırılamaz. Mikro hizmetler daha esnek bir uygulama sağlamak için birbirinden bağımsız çalışmalıdır. Uygulamanın bağımsız özellik dilimlerini teslim edemezseniz, onu ayırmak yalnızca karmaşıklık ekler.

Bir uygulamanın özellikleri bağımsız olarak ölçeklendirmesi gerekmeyebilir. Birçok uygulama, tek bir örneğin ötesine ölçeklendirmek gerektiğinde, bunu tüm örneği klonlama nın nispeten basit bir işlemi yle yapabilir. Uygulamanın tam örneklerini ölçekleme basit ve uygun maliyetli olduğunda, uygulamayı ayrı ayrı hizmetlere ayırmak için yapılan ek çalışma en az fayda sağlar.

Bir uygulamanın geliştirilmesinin başlarında, doğal işlevsel sınırların nerede olduğu hakkında net bir fikriniz olmayabilir. Minimum uygulanabilir bir ürün geliştirdikçe, doğal ayrım henüz ortaya çıkmış olmayabilir. Bu koşullardan bazıları geçici olabilir. Yekpare bir uygulama oluşturarak başlayabilir ve daha sonra geliştirilecek ve mikro hizmetler olarak dağıtılacak bazı özellikleri ayırabilirsiniz. Diğer koşullar, uygulamanın sorun alanı için gerekli olabilir, bu da uygulamanın hiçbir zaman birden çok mikro hizmete bölünmeyeceği anlamına gelir.

Bir uygulamayı birçok ayrı işlemle ayırmak da ek yükü ortaya çıkarmaz. Özellikleri farklı işlemlere ayırmada daha karmaşıklık vardır. İletişim protokolleri daha karmaşık hale gelir. Yöntem çağrıları yerine, hizmetler arasında eşzamanlı iletişim kullanmanız gerekir. Mikro hizmetler mimarisine geçerken, eShopOnContainers uygulamasının mikrohizmetler sürümünde uygulanan yapı taşlarının çoğunu eklemeniz gerekir: olay veri otobüsü kullanımı, ileti esnekliği ve yeniden denemeleri, nihai tutarlılık ve daha fazlası.

Çok daha basit [eShopOnWeb referans uygulaması](https://github.com/dotnet-architecture/eShopOnWeb) tek konteyner monolitik konteyner kullanımını destekler. Uygulama geleneksel MVC görünümleri, web API'leri ve Razor Pages içeren bir web uygulaması içerir. Bu uygulama çözüm kökünden `docker-compose build` ve `docker-compose up` komutları kullanılarak başlatılabilir. Bu komut, web projesinin kökünde `Dockerfile` bulunanı kullanarak web örneği için bir kapsayıcıyı yapılandırır ve kapsayıcıyı belirtilen bir bağlantı noktasında çalıştırır. Bu uygulamanın kaynağını GitHub'dan indirebilir ve yerel olarak çalıştırabilirsiniz. Bu yekpare uygulama bile bir kapsayıcı ortamında dağıtılmaktan yararlanır.

İlk olarak, kapsayıcı dağıtım, uygulamanın her örneğinin aynı ortamda çalıştığı anlamına gelir. Bu, erken test ve geliştirmenin gerçekleştiği geliştirici ortamını içerir. Geliştirme ekibi, uygulamayı üretim ortamıyla eşleşen kapsayıcı bir ortamda çalıştırabilir.

Buna ek olarak, konteyner uygulamaları daha düşük maliyetle ölçeklendirilir. Kapsayıcı ortamının kullanılması, geleneksel VM ortamlarından daha fazla kaynak paylaşımı sağlar.

Son olarak, uygulama kapsayıcı iş mantığı ve depolama sunucusu arasında bir ayrım zorlar. Uygulama ölçeklendikçe, birden çok kapsayıcının tümü tek bir fiziksel depolama ortamına güvenir. Bu depolama ortamı genellikle BIR SQL Server veritabanı çalıştıran yüksek kullanılabilirlikli bir sunucu olacaktır.

## <a name="docker-support"></a>Docker desteği

Proje `eShopOnWeb` .NET Core üzerinde çalışır. Bu nedenle, Linux tabanlı veya Windows tabanlı kapsayıcılarda çalıştırılabilir. Docker dağıtımı için SQL Server için aynı ana bilgisayar türünü kullanmak istediğinizi unutmayın. Linux tabanlı kaplar daha küçük bir ayak izi sağlar ve tercih edilir.

Visual Studio 2017 veya sonraki **durumlarda, Solution Explorer'daki** bir projeye sağ tıklayarak ve**Docker Desteği** **Ekle'yi** > seçerek mevcut bir uygulamaya Docker desteği ekleyebilirsiniz. Bu, gerekli dosyaları ekler ve bunları kullanmak için projeyi değiştirir. Geçerli `eShopOnWeb` örnekte bu dosyalar zaten yerinde.

Çözüm düzeyindeki `docker-compose.yml` dosya, hangi görüntülerin oluşturulması ve hangi kapsayıcıların başlatılaması hakkında bilgi içerir. Dosya, aynı anda `docker-compose` birden çok uygulama başlatmak için komutu kullanmanıza olanak sağlar. Bu durumda, yalnızca Web projesini başlatıyor. Ayrı bir veritabanı kapsayıcısı gibi bağımlılıkları yapılandırmak için de kullanabilirsiniz.

```yml
version: '3'

services:
  eshopwebmvc:
    image: eshopwebmvc
    build:
      context: .
      dockerfile: src/Web/Dockerfile
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    ports:
      - "5106:5106"

networks:
  default:
    external:
      name: nat
```

Dosya, `docker-compose.yml` `Dockerfile` projedekine `Web` başvurur. Hangi `Dockerfile` temel kapsayıcının kullanılacağını ve uygulamanın üzerinde nasıl yapılandırılacağını belirtmek için kullanılır. ' `Web` `Dockerfile`( ) :

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY *.sln .
COPY . .
WORKDIR /app/src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/src/Web/out ./

ENTRYPOINT ["dotnet", "Web.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Sorun giderme Docker sorunları

Kapsayıcı lı uygulamayı çalıştırdıktan sonra, siz durduruna kadar çalıştırmaya devam ediyor. `docker ps` Komutla hangi kapsayıcıların çalıştığını görüntüleyebilirsiniz. Komutu `docker stop` kullanarak ve kapsayıcı kimliğini belirterek çalışan bir kapsayıcıyı durdurabilirsiniz.

Docker kapsayıcılarını çalıştırmak, geliştirme ortamınızda kullanmayı deneyeceğiniz bağlantı noktalarına bağlı olabilir. Çalışan Docker kapsayıcısı ile aynı bağlantı noktasını kullanarak bir uygulamayı çalıştırmaya veya hata ayıklamaya çalışırsanız, sunucunun bu bağlantı noktasına bağlanamamasını belirten bir hata alırsınız. Bir kez daha, kapsayıcıdurdurma sorunu çözmek gerekir.

Visual Studio'yu kullanarak uygulamanız için Docker desteği eklemek istiyorsanız, bunu yaparken Docker Desktop'ın çalıştığını unutmayın. Sihirbazı çalıştırdığınızda Docker Desktop çalışmıyorsa sihirbaz düzgün çalışmaz. Ayrıca sihirbaz, doğru Docker desteğini eklemek için geçerli kapsayıcı seçiminizi inceler. Windows Kapsayıcıları için destek eklemek istiyorsanız, Windows Kapsayıcıları yapılandırılmış docker masaüstü çalışırken sihirbazı çalıştırmanız gerekir. Linux kapsayıcıları için destek eklemek istiyorsanız, Docker Linux kapsayıcıları yapılandırılmış çalıştırırken sihirbazı çalıştırın.

### <a name="references--common-web-architectures"></a>Referanslar – Ortak web mimarileri

- **Temiz Mimari**  
  <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
- **Soğan Mimarisi**  
  <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
- **Depo Deseni**  
  <https://deviq.com/repository-pattern/>
- **Temiz Mimari Çözüm Şablonu**  
  <https://github.com/ardalis/cleanarchitecture>
- **Mimarlık Mikrohizmetler e-kitap**  
  <https://aka.ms/MicroservicesEbook>
- **DDD (Etki Alanı Odaklı Tasarım)**  
  <https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/>

>[!div class="step-by-step"]
>[Önceki](architectural-principles.md)
>[Sonraki](common-client-side-web-technologies.md)
