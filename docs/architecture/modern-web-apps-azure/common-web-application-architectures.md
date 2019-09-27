---
title: Ortak web uygulaması mimarileri
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın Ortak Web uygulaması mimarilerini keşfet
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 8985434467346acc360e9a89c052803f495e87d1
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332003"
---
# <a name="common-web-application-architectures"></a>Ortak web uygulaması mimarileri

> "İyi mimari maliyetli düşünüyorsanız, kötü bir mimari deneyin."  
> _-Brian PTE ve Joseph Yoder_

En geleneksel .NET uygulamaları, tek bir IIS AppDomain içinde çalışan bir yürütülebilir dosyaya veya tek bir Web uygulamasına karşılık gelen tek bir birim olarak dağıtılır. Bu en basit dağıtım modelidir ve çok sayıda iç ve daha küçük genel uygulama sunar. Ancak, bu tek dağıtım birimi de verildiğinde, önemsiz olmayan iş uygulamalarının çoğu, bazı mantıksal ayırmalardan birkaç katmana faydalanır.

## <a name="what-is-a-monolithic-application"></a>Tek parçalı uygulama nedir?

Tek parçalı bir uygulama, davranışı bakımından tamamen kendine dahil olan bir uygulamadır. İşlemlerini gerçekleştirme sürecinde diğer hizmetler veya veri depolarıyla etkileşime geçebilir, ancak davranışının çekirdeği kendi sürecinde çalışır ve tüm uygulama genellikle tek bir birim olarak dağıtılır. Bu tür bir uygulamanın yatay olarak ölçeklendirilmesi gerekiyorsa, genellikle uygulamanın tamamı birden çok sunucu veya sanal makine arasında yinelenir.

## <a name="all-in-one-applications"></a>Hepsi bir arada uygulama

Bir uygulama mimarisi için mümkün olan en az sayıda proje vardır. Bu mimaride, uygulamanın bütün mantığı tek bir derlemede bulunur, tek bir derlemeye derlenir ve tek bir birim olarak dağıtılır.

Visual Studio 'da veya komut satırından oluşturulan yeni bir ASP.NET Core projesi, basit bir "hepsi bir arada" monoya olarak başlatılır. Sunu, iş ve veri erişim mantığı dahil olmak üzere uygulamanın tüm davranışlarını içerir. Şekil 5-1, tek projem uygulamanın dosya yapısını gösterir.

![Tek bir proje ASP.NET Core uygulaması](./media/image5-1.png)

**Şekil 5-1.** Tek bir proje ASP.NET Core uygulaması.

Tek bir proje senaryosunda, sorun ayrımı klasörler kullanılarak elde edilir. Varsayılan şablon, modeller, görünümler ve denetleyicilerin MVC model sorumlulukları ve veri ve hizmetlere yönelik ek klasörler için ayrı klasörler içerir. Bu düzenlemede, sunum ayrıntıları görünümler klasörü için mümkün olduğunca sınırlı olmalıdır ve veri erişimi uygulama ayrıntıları veri klasöründe tutulan sınıflarla sınırlı olmalıdır. İş mantığı modeller klasörü içindeki hizmetler ve sınıflarda bulunmalıdır.

Basit olsa da, tek projem tek parçalı çözüm, bazı dezavantajlara sahiptir. Projenin boyutu ve karmaşıklığı büyüdükçe, dosya ve klasör sayısı da büyümeye devam edecektir. Kullanıcı arabirimi (UI) konuları (modeller, görünümler, denetleyiciler), alfabetik olarak Gruplanmayan birden çok klasörde bulunur. Bu sorun, yalnızca filtreler veya Modelciltler gibi ek UI düzeyi yapılar kendi klasörlerine eklendiğinde daha kötü olur. İş mantığı modeller ve hizmetler klasörleri arasında dağınık ve klasörlere hangi sınıfların bağımlı olması gerektiğine dair net bir gösterge yoktur. Proje düzeyindeki bu kuruluş eksikliği genellikle [spaghfeti koduna](https://deviq.com/spaghetti-code/)yol açar.

Uygulamalar, bu sorunları çözmek için genellikle her projenin uygulamanın belirli bir _katmanında_ yer aldığı kabul edildiği çoklu proje çözümlerinde gelişmektedir.

## <a name="what-are-layers"></a>Katmanlar nelerdir?

Uygulamalar karmaşıklıkla büyüdükçe, bu karmaşıklığı yönetmenin bir yolu, uygulamayı sorumluluklara veya kaygılarına göre kesmeniz gerekir. Bu, endişeleri ayırmayı izler ve geliştiricilerin belirli işlevlerin uygulandığı yeri kolayca bulabilmeleri için büyüyen bir kod temelinin düzenlenmesine devam etmenize yardımcı olabilir. Katmanlı mimari, yalnızca kod kuruluşunun ötesinde çok sayıda avantaj sunar, ancak.

Kodu katmanlara düzenleyerek, yaygın alt düzey işlevler uygulama genelinde yeniden kullanılabilir. Bu yeniden kullanım yararlı olur çünkü bu, daha az kodun yazılması ve uygulamanın tek bir uygulamada standartlaştırılmasına izin verebileceğinden, [kendinizi yinelemeyin (kuru)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) prensibi bir uygulamadır.

Katmanlı mimari sayesinde uygulamalar, diğer katmanlarla iletişim kurabildiği katmanların kısıtlamalarını uygulayabilir. Bu, kapsülleme elde etmenize yardımcı olur. Bir katman değiştirildiğinde veya değiştirildiğinde, yalnızca onunla birlikte çalışan katmanların etkilenmesi gerekir. Hangi katmanların diğer katmanlara bağlı olduğunu sınırlayarak, tek bir değişikliğin uygulamanın tamamını etkilememesi için değişikliklerin etkileri azaltılabilir.

Katmanlar (ve Kapsülleme), uygulama içinde işlevselliğin değiştirilmesini çok daha kolay hale getirir. Örneğin, bir uygulama başlangıçta kendi SQL Server veritabanını kalıcılık için kullanabilir, ancak daha sonra bulut tabanlı bir kalıcılık stratejisi veya bir Web API 'sinin arkasında bir tane kullanmayı tercih edebilir. Uygulama, kalıcılık uygulamasını mantıksal bir katmanda doğru şekilde kapsülleniyorsa, bu SQL Server belirli katman aynı ortak arabirimi uygulayan yeni bir katman ile değiştirilebilir.

Uygulama katmanları, gereksinimlerdeki gelecekteki değişikliklere yanıt olarak, uygulamaların takas edilmesine ek olarak, uygulamaları test amacıyla değiştirmeyi de kolaylaştırabilir. Uygulamanın gerçek veri katmanına veya Kullanıcı arabirimi katmanına karşı çalışan testler yazmak yerine, bu katmanlar, isteklere bilinen yanıtlar sağlayan sahte uygulamalarla birlikte test sırasında değiştirilebilir. Bu genellikle testlerin, uygulamanın gerçek altyapısına karşı testleri çalıştırmaya kıyasla daha kolay yazma ve çalışmayı çok daha kolay hale getirir.

Mantıksal katmanlama, kurumsal yazılım uygulamalarında kod organizasyonunu iyileştirmeye yönelik yaygın bir tekniktir ve kodun katmanlara düzenlenebilmesinin birkaç yolu vardır.

> [!NOTE]
 > _Katmanlar_ , uygulama içindeki mantıksal ayrımı temsil eder. Uygulama mantığının fiziksel olarak ayrı sunuculara veya işlemlere dağıtıldığı olayda, bu ayrı fiziksel dağıtım hedeflerine _Katman_olarak başvurulur. Tek bir katmana dağıtılan N katmanlı bir uygulamanın olması mümkündür ve oldukça yaygındır.

## <a name="traditional-n-layer-architecture-applications"></a>Geleneksel "N katmanlı" mimari uygulamaları

En yaygın uygulama mantığı organizasyonu Şekil 5-2 ' de gösterilmiştir.

![Tipik uygulama katmanları](./media/image5-2.png)

**Şekil 5-2.** Tipik uygulama katmanları.

Bu katmanlar genellikle UI, BLL (Iş mantığı katmanı) ve DAL (veri erişim katmanı) olarak kısaltılır. Kullanıcılar, bu mimariyi kullanarak yalnızca BLL ile etkileşime geçen Kullanıcı arabirimi katmanı üzerinden istek yapabilirler. BLL, sırasıyla veri erişim istekleri için DAL çağırabilir. Kullanıcı arabirimi katmanı, doğrudan DAL için herhangi bir istek yapmamalıdır ve doğrudan diğer yollarla kalıcı hale gelmelidir. Benzer şekilde, BLL yalnızca DAL üzerinden gezinerek kalıcılığı ile etkileşime girebilmelidir. Bu şekilde, her katmanın kendi iyi bilinen sorumluluğu vardır.

Bu geleneksel katmanlama yaklaşımının bir dezavantajı, derleme zamanı bağımlılıklarının üstten alta kadar çalıştırılmasıdır. Diğer bir deyişle, Kullanıcı arabirimi katmanı, DAL 'ye bağlı olan BLL 'e bağlıdır. Bu, genellikle uygulamada en önemli mantığı tutan BLL 'in, veri erişimi uygulama ayrıntılarına (ve genellikle bir veritabanının varlığına) bağlı olduğu anlamına gelir. Bu tür bir mimaride iş mantığını test etmek genellikle zordur ve test veritabanı gerektirir. Bu sorunu gidermek için, sonraki bölümde gördüğünüz gibi bağımlılık Inversion ilkesi kullanılabilir.

Şekil 5-3, uygulamayı sorumluluğa (veya katmana) göre üç projeye bölmek için örnek bir çözüm gösterir.

![Üç projeyle oluşan basit bir tek parçalı uygulama](./media/image5-3.png)

**Şekil 5-3.** Üç projeyle oluşan basit bir tek parçalı uygulama.

Bu uygulama, kurumsal amaçlar için birkaç proje kullanmasına karşın, hala tek bir birim olarak dağıtılır ve istemcileri tek bir Web uygulaması olarak onunla etkileşime girecektir. Bu çok basit dağıtım sürecine izin verir. Şekil 5-4, bu tür bir uygulamanın Azure kullanarak nasıl barındırıldığını gösterir.

![Azure Web uygulaması 'nın basit dağıtımı](./media/image5-4.png)

**Şekil 5-4.** Azure Web uygulaması 'nın basit dağıtımı

Uygulamanın büyümesi için daha karmaşık ve güçlü dağıtım çözümleri gerekebilir. Şekil 5-5, ek özellikleri destekleyen daha karmaşık bir dağıtım planına bir örnek gösterir.

![Bir Web uygulamasını Azure App Service dağıtma](./media/image5-5.png)

**Şekil 5-5.** Bir Web uygulamasını Azure App Service dağıtma

Dahili olarak, bu projenin organizasyonu sorumluluğa göre birden çok projeye, uygulamanın bakım durumunu geliştirir.

Bu birim, bulut tabanlı isteğe bağlı ölçeklenebilirlikten faydalanmak için yukarı veya dışarı genişletilebilir. Ölçeği artırma, uygulamanızı barındıran sunucuya ek CPU, bellek, disk alanı veya diğer kaynakları ekleme anlamına gelir. Ölçeği genişletme, bu tür sunucuların fiziksel sunucular, sanal makineler veya kapsayıcılar olup olmadığı gibi ek örnek ekleme anlamına gelir. Uygulamanız birden çok örnek genelinde barındırılıyorsa, tek tek uygulama örneklerine istek atamak için bir yük dengeleyici kullanılır.

Azure 'da bir Web uygulamasını ölçeklendirmeye yönelik en basit yaklaşım, uygulamanın App Service planındaki ölçeklendirmeyi el ile yapılandırmaktır. Şekil 5-6, bir uygulamaya hizmet veren kaç örnek olduğunu yapılandırmak için uygun Azure panosu ekranını gösterir.

![Azure 'da plan ölçeklendirmeyi App Service](./media/image5-6.png)

**Şekil 5-6.** Azure 'da plan ölçeklendirmeyi App Service.

## <a name="clean-architecture"></a>Mimariyi temizle

Bağımlılık Inversion Ilkesini ve etki alanı odaklı tasarım (DDD) ilkelerini izleyen uygulamalar benzer bir mimariye ulaşacak. Bu mimari, yıl boyunca pek çok adla geçmiş. İlk adlardan biri altılık mimariydi ve bağlantı noktaları ve bağdaştırıcılar tarafından izlenir. Daha yakın zamanda, [Çoklu kare mimarisi](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) veya [Temizleme mimarisi](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)olarak alıntı yapılır. İkinci ad, temiz mimari, bu e-kitapta bu mimarinin adı olarak kullanılır.

> [!NOTE]
> Temiz mimari terimi, DDD Ilkeleri kullanılarak oluşturulan uygulamalara ve DDD kullanılarak oluşturulmayan uygulamalara uygulanabilir. Önceki durumda, Bu bileşim "Temizleme DDD mimarisi" olarak adlandırılabilir.

Temizleme mimarisi, iş mantığını ve uygulama modelini uygulamanın ortasına koyar. İş mantığını veri erişimine veya diğer altyapı kaygılarına bağlı olmak yerine, bu bağımlılık tersine çevrilir: altyapı ve uygulama ayrıntıları uygulama çekirdeğinize bağlıdır. Bu, uygulama çekirdeği içinde, daha sonra altyapı katmanında tanımlanan türler tarafından uygulanan soyutlamalar veya arabirimler tanımlayarak elde edilir. Bu mimariyi görselleştirmenin yaygın bir yolu, bir çoklu kare ile benzer bir dizi Eşmerkezli daire kullanmaktır. Şekil 5-7, mimari gösteriminin bu stilinin bir örneğini gösterir.

![Mimariyi Temizleme; soğan görünümü](./media/image5-7.png)

**Şekil 5-7.** Mimariyi Temizleme; soğan görünümü

Bu diyagramda, bağımlılıklar en içteki daireye doğru akar. Uygulama çekirdeği, bu diyagramın üzerindeki konumundan adını alır. Ve diyagramda uygulama çekirdeğinin diğer uygulama katmanlarında hiçbir bağımlılığı olmadığını görebilirsiniz. Uygulamanın varlıkları ve arabirimleri, çok merkezdir. Yalnızca dışarıdaki, ancak hala uygulama çekirdeği 'nde, genellikle iç daire içinde tanımlanan arabirimleri uygulayan etki alanı hizmetlerdir. Uygulama çekirdeği dışında, hem Kullanıcı arabirimi hem de altyapı katmanları uygulama çekirdeğinize bağlıdır, ancak başka bir (her zaman).

Şekil 5-8, UI ve diğer Katmanlar arasındaki bağımlılığı daha iyi yansıtan daha geleneksel bir yatay katman diyagramını gösterir.

![Mimariyi Temizleme; Yatay katman görünümü](./media/image5-8.png)

**Şekil 5-8.** Mimariyi Temizleme; Yatay katman görünümü

Düz okların derleme zamanı bağımlılıklarını temsil ettiğini, kesikli ok ise yalnızca çalışma zamanı bağımlılığını temsil ettiğini unutmayın. Temizleme mimarisi sayesinde, UI katmanı derleme zamanında uygulama çekirdeğinde tanımlanan arabirimlerle birlikte çalışarak, ideal olarak altyapı katmanında tanımlanan uygulama türleri hakkında bilgi vermemelisiniz. Bununla birlikte, çalışma zamanında uygulamanın yürütülmesi için bu uygulama türleri gereklidir, bu nedenle, bağımlılık ekleme yoluyla uygulama çekirdeği arabirimlerine bağlanmaları ve bunların kablolu olması gerekir.

Şekil 5-9, bu önerileri izleyerek ASP.NET Core uygulamasının mimarisinin daha ayrıntılı bir görünümünü gösterir.

![Temizleme mimarisini izleyen mimari diyagramı ASP.NET Core](./media/image5-9.png)

**Şekil 5-9.** Temizleme mimarisini izleyen mimari diyagramı ASP.NET Core.

Uygulama çekirdeği altyapıya bağlı olmadığından, bu katman için otomatik birim testlerini yazmak çok kolaydır. Şekil 5-10 ve 5-11, testlerin bu mimariye nasıl uyduğunu gösterir.

![UnitTestCore](./media/image5-10.png)

**Şekil 5-10.** Birim testi uygulama çekirdeği yalıtımına göre.

![Tümleştirme Testleri](./media/image5-11.png)

**Şekil 5-11.** Dış bağımlılıklarla tümleştirme test altyapısı uygulamaları.

UI katmanının altyapı projesinde tanımlı türler üzerinde doğrudan bağımlılığı olmadığından, uygulamayı kolaylaştırmak ya da uygulama gereksinimlerini değiştirmeye yanıt vermek için uygulamaları değiştirmek çok kolay olur. ASP.NET Core yerleşik kullanımı ve bağımlılık ekleme için destek, bu mimarinin, önemsiz olmayan tek parçalı uygulamalar sağlamak için en uygun yolu sağlar.

Tek parçalı uygulamalar için uygulama çekirdeği, altyapı ve Kullanıcı arabirimi projelerinin hepsi tek bir uygulama olarak çalıştırılır. Çalışma zamanı uygulama mimarisi Şekil 5-12 gibi görünebilir.

![ASP.NET Core mimarisi 2](./media/image5-12.png)

**Şekil 5-12.** Örnek bir ASP.NET Core uygulamasının çalışma zamanı mimarisi.

### <a name="organizing-code-in-clean-architecture"></a>Temiz mimaride kod düzenleme

Temiz bir mimari çözümünde, her projede açık sorumluluklar vardır. Bu nedenle, belirli türler her bir projeye aittir ve ilgili projede bu türlere karşılık gelen klasörleri sıkça bulabilirsiniz.

Uygulama çekirdeği, varlıklar, hizmetler ve arabirimler içeren iş modelini barındırır. Bu arabirimler, veri erişimi, dosya sistemi erişimi, ağ çağrıları vb. gibi altyapı kullanılarak gerçekleştirilecek işlemler için soyutlamalar içerir. Bazen bu katmanda tanımlanan hizmetlerin veya arabirimlerin, Kullanıcı arabirimi veya altyapıda bağımlılığı olmayan varlık olmayan türlerle çalışması gerekir. Bunlar, basit Veri Aktarımı nesneleri (DTOs) olarak tanımlanabilir.

### <a name="application-core-types"></a>Uygulama çekirdek türleri

- Varlıklar (kalıcı olan iş modeli sınıfları)
- Arabirimler
- Hizmetler
- DTO

Altyapı projesi genellikle veri erişim uygulamalarını içerir. Tipik bir ASP.NET Core Web uygulamasında bu uygulamalar, Entity Framework (EF) DbContext, tanımlanmış olan EF Core `Migration` nesneleri ve veri erişimi uygulama sınıflarını içerir. Soyut veri erişimi uygulama kodunun en yaygın yolu, [Depo tasarımı deseninin](https://deviq.com/repository-pattern/)kullanımıdır.

Veri erişimi uygulamalarına ek olarak, altyapı projesi altyapı sorunları ile etkileşimde bulunmak zorunda olan hizmetlerin uygulamalarını içermelidir. Bu hizmetler uygulama çekirdeğinde tanımlanmış arabirimleri uygulamalıdır ve bu nedenle altyapının uygulama çekirdeği projesine bir başvurusu olmalıdır.

### <a name="infrastructure-types"></a>Altyapı türleri

- EF Core türleri (`DbContext`, `Migration`)
- Veri erişimi uygulama türleri (depolar)
- Altyapıya özgü hizmetler (örneğin, `FileLogger` veya) `SmtpNotifier`

ASP.NET Core MVC uygulamasındaki kullanıcı arabirimi katmanı, uygulamanın giriş noktasıdır. Bu proje, uygulama çekirdeği projesine başvurmalıdır ve kendi türleri uygulama çekirdeğinde tanımlanan arabirimler aracılığıyla altyapıyla kesinlikle etkileşimde bulunmalıdır. Kullanıcı arabirimi katmanında altyapı katmanı türlerine yönelik doğrudan örnek oluşturma veya statik çağrılara izin verilmelidir.

### <a name="ui-layer-types"></a>UI katman türleri

- Denetleyiciler
- Filtreler
- Görünümler
- ViewModel 'lar
- Başlangıç

Başlangıç sınıfı, uygulamayı yapılandırmadan ve uygulama türlerini arabirimlere bağlamak için, bağımlılık ekleme işleminin çalışma zamanında düzgün çalışmasına izin verir.

> [!NOTE]
> Kullanıcı arabirimi projesinin Startup.cs dosyasında, ConfigureServices 'e bağımlılık ekleme eklemek için, projenin altyapı projesine başvurması gerekebilir. Bu bağımlılık, bir özel dı kapsayıcısı kullanılarak en kolay şekilde ortadan kaldırılabilir. Bu örneğin amaçları doğrultusunda, en basit yaklaşım, UI projesinin altyapı projesine başvurmasına izin verkullanmaktır.

## <a name="monolithic-applications-and-containers"></a>Tek parçalı uygulamalar ve kapsayıcılar

Tek ve tek parçalı dağıtım temelli bir Web uygulaması veya hizmeti oluşturabilir ve bunu bir kapsayıcı olarak dağıtabilirsiniz. Uygulama içinde tek parçalı olmayabilir, ancak birçok kitaplık, bileşen veya katmana düzenlenmiş olabilir. Dışarıdan, tek bir işlem, tek bir Web uygulaması veya tek hizmet gibi tek bir kapsayıcıdır.

Bu modeli yönetmek için, uygulamayı temsil etmek üzere tek bir kapsayıcı dağıtırsınız. Ölçeklemek için, yalnızca bir yük dengeleyiciye sahip ek kopyalar eklemeniz yeterlidir. Kolaylık, tek bir kapsayıcıda veya VM 'de tek bir dağıtımı yönetmekten gelir.

![Şekil 5-13](./media/image5-13.png)

Şekil 5-13 ' de gösterildiği gibi, her bir kapsayıcı içinde birden çok bileşen/kitaplık veya iç katman ekleyebilirsiniz. Ancak, _"bir kapsayıcı tek bir işlem yaptığı ve tek bir işlemde_yaptığı" kapsayıcı ilkesini takip eden tek parçalı desenler bir çakışma olabilir.

Bu yaklaşımın downi, uygulamanın ne zaman büyüdüğü, ölçeklendirilmesi için de gelir. Uygulamanın tamamı ölçeklenmez, aslında bir sorun değildir. Ancak çoğu durumda, uygulamanın birkaç bölümü ölçeklendirmeyi gerektiren sıkıştırma noktalarınken diğer bileşenler daha az kullanılır.

Genellikle, büyük olasılıkla ölçeklendirmeniz gereken, ürün bilgileri bileşeni olan tipik duyun örneğini kullanarak. Birçok müşteri, ürünleri satın almanızdan daha fazla sayıda müşteriye gözatmasını Daha fazla müşteri, kendi sepetini ödeme işlem hattını kullanmından kullanıyor. Daha az müşteri, yorum ekler veya satın alma geçmişini görüntüler. Yalnızca, tek bir bölgede, içerik ve pazarlama kampanyalarını yönetmesi gereken birkaç çalışanın olması olasıdır. Tek parçalı tasarımı ölçeklendirerek, tüm kod birden çok kez dağıtılır.

"Her şeyi ölçeklendirin" sorununa ek olarak, tek bir bileşendeki değişiklikler tüm uygulamanın tam olarak yeniden test edilmesini ve tüm örneklerin tam yeniden dağıtım yapılmasını gerektirir.

Tek parçalı yaklaşım yaygındır ve birçok kuruluş bu mimari yaklaşımla geliştirilmektedir. Çoğu, diğerleri sınırlara vururken çok iyi sonuç elde edilir. Bu modelde birçok uygulama tasarlanıyor, çünkü araçlar ve altyapı hizmet yönelimli mimariler (SOA) oluşturmak için çok zor olduğundan, uygulama grew 'a kadar ihtiyacı görmez. Tek parçalı yaklaşım sınırlarına ulaşacağınızı fark ederseniz, kapsayıcıyı daha iyi hale getirebilmesine olanak tanımak üzere uygulamayı bölmek ve mikro hizmetler bir sonraki mantıksal adım olabilir.

![Şekil 5-14](./media/image5-14.png)

Microsoft Azure tek parçalı uygulamalar dağıtmak, her örnek için adanmış VM 'Ler kullanılarak elde edilebilir. [Azure sanal makine ölçek kümelerini](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)kullanarak VM 'leri kolayca ölçeklendirebilirsiniz. [Azure Uygulama Hizmetleri](https://azure.microsoft.com/services/app-service/) tek parçalı uygulamalar çalıştırabilir ve VM 'leri yönetmek zorunda kalmadan örnekleri kolayca ölçeklendirebilir. Azure Uygulama Hizmetleri, tek tek Docker Kapsayıcıları örnekleri çalıştırabilir ve dağıtımı basitleştirir. Docker 'ı kullanarak tek bir VM 'yi Docker Konağı olarak dağıtabilir ve birden çok örnek çalıştırabilirsiniz. Şekil 5-14 ' de gösterildiği gibi Azure dengeleyicisi 'ni kullanarak ölçeklendirmeyi yönetebilirsiniz.

Çeşitli konaklara dağıtım, geleneksel dağıtım teknikleri ile yönetilebilir. Docker konakları el ile gerçekleştirilen ve sürekli teslim (CD) işlem hatları gibi Otomasyon aracılığıyla **Docker Run** gibi komutlarla yönetilebilir.

### <a name="monolithic-application-deployed-as-a-container"></a>Kapsayıcı olarak dağıtılan tek parçalı uygulama

Tek parçalı uygulama dağıtımlarını yönetmek için kapsayıcıları kullanmanın avantajları vardır. Kapsayıcı örneklerinin ölçeklendirilmesi, ek VM 'Leri dağıtmaktan daha hızlı ve daha kolaydır. VM 'Leri ölçeklendirmek için sanal makine ölçek kümeleri kullanılırken bile, örnek bir süre sürer. Uygulama örnekleri olarak dağıtıldığında, uygulamanın yapılandırması VM 'nin bir parçası olarak yönetilir.

Docker görüntüsü olarak güncelleştirmelerin dağıtımı, çok daha hızlı ve daha verimlidir. Docker görüntüleri genellikle Saniyeler içinde başlar, piyasaya çıkarma hızlandırın. Docker örneğini aşağı doğru artırma, genellikle bir saniyeden daha az bir şekilde `docker stop` tamamlanan bir komut vermek kadar kolaydır.

Kapsayıcılar, Tasarım gereği doğal olarak değişmez, ancak güncelleştirme betikleri, diskte kalan belirli bir yapılandırma veya dosya için hesabı unutabilirken, bu durumda bozuk VM 'Lerde endişelenmenize gerek kalmaz.

Docker kapsayıcılarını, daha basit Web uygulamalarının tek parçalı dağıtımı için kullanabilirsiniz. Bu, sürekli tümleştirme ve sürekli dağıtım işlem hatlarını geliştirir ve dağıtım-üretim başarısını elde etmenize yardımcı olur. Daha fazla "makinenizde çalışmıyor, neden üretimde çalışmıyor?"

Mikro hizmet tabanlı mimarinin birçok avantajı vardır, ancak bu avantajlar artan karmaşıklık maliyetlerine göre gelir. Bazı durumlarda, maliyetler avantajlardan yararlanır. böylece tek bir kapsayıcıda veya yalnızca birkaç kapsayıcıda çalışan tek parçalı bir dağıtım uygulaması daha iyi bir seçenektir.

Tek parçalı bir uygulama iyi ayrılmış mikro hizmetlere kolayca parçalanmayabilir. Mikro hizmetler, daha esnek bir uygulama sağlamak için birbirinden bağımsız olarak çalışmalıdır. Uygulamanın bağımsız Özellik dilimlerini teslim ediyorsanız, yalnızca karmaşıklık ekler.

Uygulamanın özellikleri bağımsız olarak ölçeklendirmeniz gerekebilir. Birçok uygulama, tek bir örneği aşmaları gerektiğinde bunu, tüm örneği klonlamak için görece basit bir süreç aracılığıyla yapabilir. Uygulamayı ayrık hizmetlere ayırmak için ek iş, uygulamanın tam örneklerinin ölçeklendirilmesi basit ve ekonomik hale geldiğinde en az avantaj sağlar.

Uygulamanın geliştirilmesi sırasında, doğal işlev sınırlarının bulunduğu açık bir fikriniz olmayabilir. En az uygulanabilir bir ürün geliştirirken doğal ayrım henüz ortaya çıkabilir. Bu koşullardan bazıları geçici olabilir. Tek parçalı bir uygulama oluşturarak başlayabilir ve daha sonra bazı özellikleri, mikro hizmetler olarak geliştirilip dağıtılacak şekilde ayırabilirsiniz. Diğer koşullar uygulamanın sorun alanı için önemli olabilir, yani uygulama hiçbir şekilde birden fazla mikro hizmete parçalanmayabilir.

Bir uygulamayı birçok ayrı işleme ayırmak de ek yük getirir. Özellikleri farklı işlemlere ayırma daha karmaşıktır. İletişim protokolleri daha karmaşık hale gelir. Yöntem çağrıları yerine, hizmetler arasında zaman uyumsuz iletişimler kullanmanız gerekir. Mikro hizmetler mimarisine geçtiğinizde, eShopOnContainers uygulamasının mikro hizmetler sürümünde uygulanan yapı taşlarından çoğunu eklemeniz gerekir: olay veri yolu işleme, ileti dayanıklılığı ve yeniden denemeler, nihai tutarlılık ve daha fazlası.

Çok daha basit [Eshoponweb Reference uygulaması](https://github.com/dotnet-architecture/eShopOnWeb) , tek Kapsayıcılı tek parçalı kapsayıcı kullanımını destekler. Uygulama, geleneksel MVC görünümlerini, Web API 'Lerini ve Razor Pages içeren bir Web uygulaması içerir. Bu uygulama, `docker-compose build` ve `docker-compose up` komutları kullanılarak çözüm kökünden başlatılabilir. Bu komut, Web projesinin kökünde `Dockerfile` bulunan ' i kullanarak Web örneği için bir kapsayıcı yapılandırır ve kapsayıcıyı belirtilen bir bağlantı noktasında çalıştırır. Bu uygulamanın kaynağını GitHub 'dan indirebilir ve yerel olarak çalıştırabilirsiniz. Bu tek parçalı uygulama avantajlarının bir kapsayıcı ortamında dağıtılması bile.

Bir tane için Kapsayıcılı dağıtım, uygulamanın her örneğinin aynı ortamda çalıştığı anlamına gelir. Bu, erken test ve geliştirmenin gerçekleştiği geliştirici ortamını içerir. Geliştirme ekibi, uygulamayı üretim ortamıyla eşleşen kapsayıcılı bir ortamda çalıştırabilir.

Ayrıca, Kapsayıcılı uygulamalar daha düşük maliyette ölçeği azaltır. Kapsayıcı ortamının kullanılması, geleneksel VM ortamlarından daha fazla kaynak paylaşımını mümkün bir şekilde sunar.

Son olarak, uygulamayı kapsayıcı iş mantığı ve depolama sunucusu arasında ayrımı zorlar. Uygulama ölçeklendirilirken, birden çok kapsayıcı tek bir fiziksel depolama ortamına bağlıdır. Bu depolama ortamı genellikle SQL Server veritabanı çalıştıran yüksek kullanılabilirliğe sahip bir sunucu olur.

## <a name="docker-support"></a>Docker desteği

`eShopOnWeb` Proje .NET Core üzerinde çalışır. Bu nedenle, Linux tabanlı veya Windows tabanlı kapsayıcılardan çalıştırılabilir. Docker dağıtımı için SQL Server aynı konak türünü kullanmak istediğinizi unutmayın. Linux tabanlı kapsayıcılar daha küçük bir ayak izine izin verir ve tercih edilir.

**Çözüm Gezgini** bir projeye sağ tıklayıp**Docker desteği** **Ekle** > ' yi seçerek var olan bir uygulamaya Docker desteği eklemek için Visual Studio 2017 veya sonraki bir sürümünü kullanabilirsiniz. Bu, gerekli dosyaları ekler ve projeyi kullanmak için değiştirir. Geçerli `eShopOnWeb` örnekte bu dosyalar zaten var.

Çözüm düzeyi `docker-compose.yml` dosya, hangi görüntülerin derlemesinin ve hangi kapsayıcıların başlatılabileceğinize ilişkin bilgiler içerir. Bu dosya, aynı anda birden çok `docker-compose` uygulamayı başlatmak için komutunu kullanmanıza olanak sağlar. Bu durumda, yalnızca Web projesi başlatılıyor. Ayrıca, ayrı bir veritabanı kapsayıcısı gibi bağımlılıkları yapılandırmak için de kullanabilirsiniz.

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

Dosya, `Web` projedeki öğesine `Dockerfile` başvurur. `docker-compose.yml` `Dockerfile` Kullanılacak temel kapsayıcıyı ve uygulamanın nasıl yapılandırılacağını belirtmek için kullanılır. `Web`' :`Dockerfile`

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /app

COPY *.sln .
COPY . .
WORKDIR /app/src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS runtime
WORKDIR /app
COPY --from=build /app/src/Web/out ./

# Optional: Set this here if not setting it from docker-compose.yml
# ENV ASPNETCORE_ENVIRONMENT Development

ENTRYPOINT ["dotnet", "Web.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Docker sorunlarını giderme

Kapsayıcılı uygulamayı çalıştırdıktan sonra, siz durduruncaya kadar çalışmaya devam eder. `docker ps` Komutuyla hangi kapsayıcıların çalıştığını görüntüleyebilirsiniz. `docker stop` Komutu kullanarak ve kapsayıcı kimliğini belirterek çalışan kapsayıcıyı durdurabilirsiniz.

Docker Kapsayıcıları çalıştırmanın, daha önce geliştirme ortamınızda kullanmayı deneyebileceğinizi belirten bağlantı noktalarına bağlanmadığını unutmayın. Çalışan bir Docker kapsayıcısı ile aynı bağlantı noktasını kullanarak bir uygulamayı çalıştırmaya veya hata ayıklamanıza çalışırsanız, sunucunun o bağlantı noktasına bağlanmadığını belirten bir hata alırsınız. Bir kez daha, kapsayıcıyı durdurmak sorunu çözmelidir.

Visual Studio kullanarak uygulamanıza Docker desteği eklemek istiyorsanız, bunu yaptığınızda Docker Desktop 'ın çalıştığından emin olun. Sihirbazı başlattığınızda Docker Desktop çalışmıyorsa sihirbaz düzgün çalışmaz. Ayrıca, sihirbaz geçerli kapsayıcı seçiminizi inceleyerek doğru Docker desteğini de ekler. Windows kapsayıcıları için destek eklemek istiyorsanız, Windows kapsayıcılarıyla çalışan Docker Desktop 'ı kullanırken Sihirbazı çalıştırmanız gerekir. Linux kapsayıcıları için destek eklemek istiyorsanız, Linux kapsayıcılarıyla çalışırken Docker çalışırken Sihirbazı çalıştırın.

### <a name="references--common-web-architectures"></a>Başvurular – ortak Web mimarileri

- **Temizleme mimarisi**  
  <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
- **Soğan mimarisi**  
  <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
- **Depo deseninin**  
  <https://deviq.com/repository-pattern/>
- **Temizleme mimarisi çözüm örneği**  
  <https://github.com/ardalis/cleanarchitecture>
- **Mikro hizmetler e-kitabı mimarisi**  
  <https://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
>[Önceki](architectural-principles.md)
>[İleri](common-client-side-web-technologies.md)
