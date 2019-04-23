---
title: Ortak web uygulaması mimarileri
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | Ortak web uygulaması mimarileri keşfedin
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 22cb673f09faf7b0eabcfa5b3f6700d33242d84b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122700"
---
# <a name="common-web-application-architectures"></a>Ortak web uygulaması mimarileri

> "İyi olabileceğini düşünüyorsanız mimarisi pahalıdır, hatalı mimarisi deneyin."  
> _-Brian alt ve Joseph Yoder_

Çoğu geleneksel .NET uygulamaları, bir yürütülebilir dosyası ya da tek bir IIS appdomain içinde çalışan tek bir web uygulaması için karşılık gelen bir tek birim olarak dağıtılır. Bu en basit dağıtım modelidir ve çoğu iç ve daha küçük genel uygulama çok iyi işlevi görür. Ancak, bile bu tekli ünite dağıtımının göz önünde bulundurulduğunda, en Önemsiz olmayan bir iş kolu uygulamaları birkaç katmanlara bazı mantıksal ayrılığı yararlanın.

## <a name="what-is-a-monolithic-application"></a>Tek parça bir uygulamayı nedir?

Tek parça bir uygulamayı, davranışı bakımından tamamen kendi içinde yer alan, biridir. Kendi işlemleri sırasında diğer hizmetleri ya da veri depoları ile etkileşimde bulunabilir, ancak davranışını setinin kendi işlemi içinde çalıştırılan ve tüm uygulama genellikle tek bir birim olarak dağıtılır. Genellikle bu tür bir uygulama, yatay olarak genişletmek gerekiyorsa, tüm uygulama birden fazla sunucu veya sanal makineler arasında çoğaltılır.

## <a name="all-in-one-applications"></a>Hepsi bir arada uygulamalar

Projelerin bir uygulama mimarisi için olası en küçük sayı biridir. Bu mimaride, uygulamanın tamamını mantıksal tek bir projede yer alan, tek bir bütünleştirilmiş kod derlenir ve tek bir birim olarak dağıtılabilir.

Yeni bir ASP.NET Core proje Visual Studio'da ya da komut satırından oluşturmadığımız basit bir "hepsi bir arada özellikli" tek başlar. Tüm sunu, iş ve veri erişim mantığı da dahil olmak üzere uygulama davranışını içerir. Şekil 5-1 tek proje uygulamanın dosya yapısı gösterilmektedir.

![](./media/image5-1.png)

**Şekil 5-1.** Tek proje ASP.NET Core uygulaması.

Tek bir projede bir senaryoda, görev ayrımı nettir klasörleri kullanılarak elde edilir. Varsayılan şablonu, veri ve hizmetler için ayrı klasörlerini modelleri, görünümleri ve denetleyicileri MVC düzeni sorumluluklarını yanı sıra, ek klasörleri içerir. Bu düzenleme sunu Ayrıntılar görünümleri klasörüne mümkün olduğunca sınırlı ve veri erişim uygulama ayrıntılarını sınıfları veri klasöründe tutulan sınırlı olmalıdır. İş mantığı Hizmetleri ve modeller klasörü içindeki sınıflarda yer almalıdır.

Basit olsa da, tek proje tek parça çözüm bazı dezavantajlara sahiptir. Proje boyutu ve karmaşıklığı arttıkça, dosya ve klasörlerin sayısı da büyümeye devam edecektir. Kullanıcı Arabirimi (UI) ile ilgili sorunları giderme (modelleri, görünümleri, denetleyicileri) alfabetik olarak gruplandırılmış değil, birden çok klasörlerinde yer alır. Bu sorunu daha zayıf için filtreler veya ModelBinders, gibi ek kullanıcı Arabirimi düzeyinde yapılar kendi klasörlerine eklenen alır. İş mantığı, model ve hizmet klasörler arasında dağılmış ve hangi klasörleri sınıflarda hangi bazılarında bağımlı NET bir belirti yoktur. İçin proje düzeyinde kuruluş bu eksikliği sık müşteri adayları [spaghetti kod](https://deviq.com/spaghetti-code/).

Bu sorunları gidermeye yönelik uygulamalar genellikle birden çok proje çözümü, burada her proje olarak kabul edilir belirli bir bulunması halinde evrim Geçiren _katman_ uygulama.

## <a name="what-are-layers"></a>Katmanları nelerdir?

Uygulamaların karmaşıklığı arttıkça, bu karmaşıklık yönetmek için bir uygulamanın kendi sorumluluklarını veya endişeniz varsa göre bölüneceği yoludur. Bu sorunları asıl ayrımı izler ve böylece geliştiriciler, burada bazı işlevlere uygulanan kolayca bulabilirsiniz düzenlenmiş büyüyen bir kod temeli korunmasına yardımcı olabilirsiniz. Katmanlı bir mimari, çok sayıda avantaj yalnızca kod kuruluş dışına yine de sunar.

Kod katmanlara düzenleyerek, düşük düzey ortak işlevselliği uygulama genelinde yeniden kullanılabilir. Bu yeniden yazılması gerekiyor daha az kod anlamına geldiğinden ve aşağıdaki tek bir uygulama üzerinde standart hale getirmek uygulama izin yararlıdır [kendiniz (KURU) yineleme](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) ilkesi.

Katmanlı bir mimari ile uygulamaları katman diğer katmanlarla kurabilir kısıtlamaları zorunlu kılabilir. Kapsülleme sağlamak için yardımcı olur. Bir katmanı değiştirilmiş ya da yerine onunla çalışan katmanları etkilenmiş. Hangi sınırlayarak, böylece uygulamanın tamamı tek bir değişiklik etkilemez diğer katmanları değişikliklerinin etkisini azaltılabilir katmanları bağlıdır.

Katmanları (ve saklama) işlevselliği uygulamadaki değiştirmek çok daha kolay olun. Örneğin, bir uygulama başlangıçta kendi SQL Server veritabanı için Kalıcılık kullanabilirsiniz, ancak daha sonra bir bulut tabanlı süreklilik stratejisi ya da bir web API'si arkasında kullanmayı seçebilirsiniz. Uygulama düzgün şekilde Kalıcılık uygulanması mantıksal katman içinde kapsüllenmiş, bu SQL Server belirli katman aynı genel arabirimi uygulayan yeni bir tane tarafından değiştirilebilir.

Gelecekteki gereksinimlerdeki değişikliklere yanıt uygulamalarında kullanıma takas olası ek olarak, uygulama katmanları Ayrıca, test amaçlı uygulamalarını takas etmek kolaylaştırabilir. Gerçek veri katmanı veya uygulama UI yerleşiminde karşı çalışan testler yazmak zorunda kalmak yerine bu Katmanlar test zaman isteklerine bilinen yanıtlar sağlayan sahte uygulamaları ile değiştirilebilir. Bu genellikle testleri yazmak çok daha kolay ve testleri uygulamanın gerçek altyapı karşı çalışmaya kıyasla çalıştırmak için çok daha hızlı hale getirir.

Mantıksal katman kuruluşun kurumsal yazılım uygulamaları kod iyileştirmeye yönelik yaygın bir tekniktir ve kod katmanlara düzenlenebilir birkaç yolu vardır.

> [!NOTE]
 > _Katmanlar_ uygulama içinde mantıksal ayrılığı temsil eder. Uygulama mantığı fiziksel sunucuları veya işlemler ayırmak için dağıtılmış, durumunda, bu ayrı bir fiziksel dağıtım hedefleri olarak adlandırılır _katmanları_. Bu, olası ve tek bir katmana dağıtılır bir N katmanlı uygulama için çok yaygın olur.

## <a name="traditional-n-layer-architecture-applications"></a>Geleneksel "N-katmanı" mimarisi uygulama

Şekil 5-2'de en yaygın uygulama mantığı organizasyonunu katmanlara gösterilmektedir.

![](./media/image5-2.png)

**Şekil 5-2.** Normal uygulama katmanları.

Bu katmanlar sık kullanıcı Arabirimi kısaltılır BLL (iş mantığı katmanı) ve DAL (veri erişim katmanı). Bu mimariyi kullanarak, kullanıcılar yalnızca BLL ile etkileşime giren UI yerleşiminde isteklerini olun. BLL, buna karşılık, veri erişim istekleri için DAL çağırabilirsiniz. UI yerleşiminde herhangi bir DAL ile doğrudan isteklerde olmaması gerekir ya da doğrudan arasında başka yollarla kalıcılığı ile etkileşim. Benzer şekilde, BLL yalnızca kalıcılığı ile bir DAL giderek etkileşim. Bu şekilde, her katmanın kendi iyi bilinen bir sorumluluğu vardır.

Bu geleneksel katmanlama yaklaşımın bir dezavantajı derleme zamanı bağımlılıklarını üstten alta çalışmasıdır. Diğer bir deyişle UI yerleşiminde DAL üzerinde bağlıdır BLL bağlıdır. Bu, genellikle en önemli mantıksal uygulamada tutar, BLL veri erişimi uygulama ayrıntıları (ve genellikle veritabanı varlığı) bağlı olduğu anlamına gelir. İş mantığı bu tür bir mimari test genellikle test veritabanı gerektiren, zordur. Sonraki bölümde göreceğiniz gibi bağımlılık tersine çevirme ilkesini bu sorunu gidermek için kullanılabilir.

Şekil 5-3 uygulama sorumluluğu (veya katman) üç projelere bozucu bir örnek çözüm gösterilmektedir.

![](./media/image5-3.png)

**Şekil 5-3.** Basit monolitik bir uygulamayla üç projeleri.

Bu uygulama, kuruluş amacıyla birkaç proje kullansa da, yine de tek bir birim olarak dağıtılır ve istemcileri ile tek bir web uygulaması kullanacaksınız. Bu, çok basit dağıtım işlemi için sağlar. Şekil 5-4'te gösterildiği böyle bir uygulamayı nasıl olabileceği barındırılan Azure kullanarak.

![](./media/image5-4.png)

**Şekil 5-4.** Azure Web uygulamasının basit dağıtım

Uygulamanın büyümesi gerektiğinde gibi daha karmaşık ve güçlü dağıtım çözümleri gerekli olabilir. Şekil 5-5 ek özelliklerini destekler. daha karmaşık bir dağıtım planı örneği gösterilmektedir.

![](./media/image5-5.png)

**Şekil 5-5.** Bir Azure App Service'te bir web uygulaması dağıtma

Dahili olarak, bu projenin kuruluşunuzun birden çok proje sorumluluğa tabanlı uygulama Bakımı artırır.

Bu birimi artırmaya veya genişletmeye bulut tabanlı isteğe bağlı ölçeklenebilirlik avantajlarından yararlanmak için ölçeklendirilebilir. Büyütme, uygulamanızı barındıran sunucuların ek CPU, bellek, disk alanı veya diğer kaynaklar ekleme anlamına gelir. Bunlar, fiziksel sunucuları, sanal makineler ve kapsayıcılar olup olmadığını ölçek genişletme bu sunucular ek örneklerini eklemek anlamına gelir. Uygulamanızı birden çok örneğine barındırıldığında, bir yük dengeleyici tek tek uygulama örneklerine istekleri atamak için kullanılır.

Azure'da bir web uygulaması ölçeklendirme için en kolay yaklaşım, uygulamanın App Service planında el ile ölçeklendirme yapılandırmaktır. Şekil 5-6 kaç tane örnek bir uygulama hizmet veren yapılandırmak için uygun Azure Pano ekranı gösterilir.

![](./media/image5-6.png)

**Şekil 5-6.** App Service, Azure'da ölçeklendirme planı.

## <a name="clean-architecture"></a>Temiz mimarisi

Bağımlılık tersine çevirme ilkesini ve bunun yanı sıra etki alanı Odaklı Tasarım (DDD) İlkeleri izleyin uygulamaları benzer bir mimariye geldiğinde eğilimindedir. Bu mimari, yıllar içinde birçok adlarıyla geçti. Adlarını Altıgen mimarisi, bağlantı noktaları-ve-bağdaştırıcıları tarafından izlenen biriydi. Daha yakın bir tarihte bu olarak alıntı olarak [çoklu kare mimarisi](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) veya [temiz mimarisi](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). İkinci Ad, temiz mimarisi bu mimaride bu e-kitap adı olarak kullanılır.

> [!NOTE]
> Temiz bir mimari filtrelenmeyen seçeceğine DDD ilkeleri kullanılarak oluşturulan uygulamalar uygulanabilir terimi DDD kullanmaktır. Eski söz konusu olduğunda bu birleşimi için "DDD mimarisine temiz" başvurulabilir.

Temiz mimarisi, iş mantığı ve uygulama modeli uygulama merkezinde koyar. Veri erişim veya diğer altyapıyla ilgili endişelerini bağımlı iş mantığına sahip olmak yerine bu bağımlılık ters: uygulama Çekirdeğinde altyapı ve uygulama ayrıntılarına bağlıdır. Bu, altyapı katman içinde tanımlanan tür tarafından uygulanan uygulama core'da soyutlama veya arabirimleri tanımlayarak sağlanır. Bu mimari görselleştirmenin en yaygın yolu, bir dizi için bir çoklu kare benzer Eşmerkezli daire kullanmaktır. Şekil 5-7, bu tür bir mimari temsili bir örnek göstermektedir.

![](./media/image5-7.png)

**Şekil 5-7.** Mimari temizleme; Çoklu kare görüntüle

Bu diyagramda, bağımlılıkları en içteki daire doğru akış. Uygulama çekirdeği konumundan bu diyagramının çekirdek adını alır. Ve diyagram üzerinde uygulama çekirdeği diğer uygulama katmanları hiçbir bağımlılığı olduğunu görebilirsiniz. Uygulama varlıkları ve arabirimler çok Merkezi'nde var. Yalnızca dışında ancak uygulama çekirdeği aşamasında, genellikle iç daire içinde tanımlanan arabirimleri uygulayan etki alanı Hizmetleri değildir. Uygulama çekirdek dışında hem kullanıcı Arabirimi ve altyapı katmanlarının uygulama çekirdeği, ancak başka bir (zorunlu) bağlıdır.

Şekil 5-8 bağımlılık UI ve diğer katmanlar arasında daha iyi yansıtmaktadır daha geleneksel bir yatay katman diyagramı gösterir.

![](./media/image5-8.png)

**Şekil 5-8.** Mimari temizleme; Yatay katman görüntüle

Yalnızca çalışma zamanı bağımlılık kesikli oku temsil ederken, düz bir ok derleme zamanı bağımlılıklarını temsil ettiğini unutmayın. Temiz yapı ile UI yerleşiminde uygulama çekirdek derleme zamanında tanımlanan arabirimleri ile çalışır ve ideal olarak altyapı katmanda tanımlanan uygulama türleri hakkında bilmeniz gerekir. Mevcut ve bağımlılık ekleme aracılığıyla uygulama temel arabirimler kadar kablolu erişebilmeleri çalışma zamanında, ancak bu uygulama türleri yürütmek, uygulama için gerekli değildir.

Şekil 5-9, bu önerileri oluşturulduğunda bir ASP.NET Core uygulama mimarisi daha ayrıntılı bir görünümünü gösterir.

![ASP.NET Core mimarisi](./media/image5-9.png)

**Şekil 5-9.** ASP.NET Core mimarisi diyagramı aşağıdaki temiz mimarisi.

Uygulama çekirdeği altyapısında almadığından Bu katman için otomatik birim testleri yazmak çok daha kolaydır. Şekil 5-10-5-11 testleri bu mimariye nasıl getireceğinizi gösterir.

![UnitTestCore](./media/image5-10.png)

**Şekil 5-10.** Uygulama çekirdeği yalıtım modunda test birimi.

![IntegrationTests](./media/image5-11.png)

**Şekil 5-11.** Harici bağımlılıkları olan altyapı uygulamaları sınama tümleştirme.

UI yerleşiminde, altyapı projede tanımlanan türler üzerinde herhangi bir doğrudan bağımlılığı olmadığı benzer şekilde test edilmesini kolaylaştırmak için ya da uygulamaları veya uygulama gereksinimlerini değiştirme yanıt değiştirilecek çok kolaydır. ASP.NET Core'nın yerleşik kullanımını ve bağımlılık ekleme için destek yapısı Önemsiz olmayan tek yapılı uygulamaları için en uygun şekilde bu mimari sağlar.

Tek yapılı uygulamalar için uygulama çekirdeği, altyapı ve UI projeleri tümünü tek bir uygulama çalıştırılır. Çalışma zamanı uygulama mimarisi, Şekil 5-12'gibi bir şey görünebilir.

![ASP.NET Core mimarisi 2](./media/image5-12.png)

**Şekil 5-12.** Örnek ASP.NET Core uygulamanın çalışma zamanı mimari.

### <a name="organizing-code-in-clean-architecture"></a>Kodu temiz mimarisinde düzenleme

Bir temiz mimarisi çözümde her proje Temizle sorumlulukları vardır. Bu nedenle, her projede belirli türlerine ait ve bu tür uygun projedeki karşılık gelen klasörlere sık bulabilirsiniz.

Uygulama çekirdeği varlıklar, hizmetler ve arabirimler içerir iş modeli tutar. Bu arabirimler soyutlama altyapısını kullanarak veri erişimi, dosya sistemi erişimini, ağ çağrıları, vb. gibi gerçekleştirilecek işlemleri içerir. Bazen Hizmetleri veya bu katmanda tanımlanan arabirimleri kullanıcı Arabirimi veya altyapı üzerinde hiçbir bağımlılık sahip olmayan varlık türleriyle çalışmak gerekir. Bu basit veri aktarımı nesneleri (Dto) tanımlanabilir.

### <a name="application-core-types"></a>Uygulama temel türleri

- Varlıkları (kalıcı iş modeli sınıflar)
- Arabirimler
- Hizmetler
- Dto'lar

Altyapı proje, genellikle veri erişimi uygulamaları içerir. Tipik bir ASP.NET Core web uygulamasında bu uygulamalardan herhangi EF Core, Entity Framework (EF) DbContext dahil `Migration` tanımlanan nesneleri ve veri erişim uygulama sınıfları. Veri erişim uygulama kodu soyutlamak için en yaygın kullanımının yoludur [deposu tasarım deseni](https://deviq.com/repository-pattern/).

Veri erişimi uygulamaları yanı sıra altyapısı projesi altyapıyla ilgili endişelerini ile etkileşmesi gereken hizmetleri, uygulamaları içermelidir. Bu hizmetler, arabirimler uygulama çekirdek tanımlanan uygulamalıdır ve altyapı uygulama Core projesine bir başvuru şekilde sahip olmalıdır.

### <a name="infrastructure-types"></a>Altyapı türleri

- EF Core türleri (`DbContext`, `Migration`)
- Veri erişim uygulama türleri (depo)
- Özel altyapı Hizmetleri (örneğin, `FileLogger` veya `SmtpNotifier`)

Bir ASP.NET Core MVC uygulamasındaki kullanıcı arabirimi katmanı, uygulama için giriş noktasıdır. Bu proje uygulama çekirdeği projeye başvurması ve türlerinden altyapısı kesinlikle uygulama çekirdek tanımlanan arabirimleri aracılığıyla etkileşim. Hiçbir doğrudan örneğinin veya statik çağrıları altyapı katman türleri için kullanıcı Arabirimi katmanında izin verilmelidir.

### <a name="ui-layer-types"></a>UI katman türleri

- Denetleyiciler
- FilTReleri
- Görünümler
- Viewmodel'lar
- Başlangıç

Başlangıç sınıfı için uygulamayı yapılandırma ve teknik uygulama türleri'kurmak için çalışma zamanında düzgün çalışması bağımlılık ekleme sağlayan arabirimler için sorumludur.

> [!NOTE]
> Bağımlılık ekleme UI proje Startup.cs dosyasındaki Createservicereplicalisteners() wire için proje altyapısı projesi başvuru gerekebilir. Bu bağımlılık, en kolay özel DI kapsayıcı kullanılarak kaldırılabilir. Bu örnek amaçları için en kolay yaklaşım, altyapı projesine başvuruda bulunmak kullanıcı Arabirimi proje izin vermektir.

## <a name="monolithic-applications-and-containers"></a>Tek yapılı uygulamalar ve kapsayıcılar

Tek ve tek parça dağıtım tabanlı Web uygulaması veya hizmeti oluşturma ve kapsayıcı olarak dağıtın. Uygulama içinde bu tek parçalı ancak düzenlenmiş şekilde birkaç kitaplıklar, bileşenler veya katmanları olmayabilir. Harici olarak, bir tek tek işlem, tek bir web uygulaması veya tek bir hizmet gibi kapsayıcıdır.

Bu model yönetmek için uygulamayı temsil etmek için tek bir kapsayıcı dağıtırsınız. Ölçeklendirmek için önde gelen bir yük dengeleyici ile ek kopya eklemeniz yeterlidir. Basitlik, tek bir dağıtım bir çoklu kapsayıcı veya VM yönetmesini gelir.

![](./media/image5-13.png)

Şekil 5-13'te gösterildiği gibi birden çok bileşenleri/kitaplıkları veya her bir kapsayıcı içindeki iç Katmanlar içerebilir. Ancak, kapsayıcı İlkesi'ni aşağıdaki _"kapsayıcı bir şeyi yapar ve bunu tek bir işlemde yapar_", tek parçalı deseni bir çakışma olabilir.

Bu yaklaşımın bir dezavantajı, / uygulama büyürken, ölçeklendirme gerektiren gelir. Uygulamanın tamamı ölçeklenen, gerçekten bir sorun değildir. Ancak, çoğu durumda, ölçeklendirme, diğer bileşenleri çalışırken gerektiren sıkıştırma noktaları daha az kullanılan uygulamanın bazı bölümlerini uygulanır.

Tipik bir e-ticaret örneği kullanarak, büyük olasılıkla ölçeklendirmek gerekenler ürün bilgileri bileşendir. Pek çok daha fazla müşteriye satın çok ürünlerin göz atın. Daha fazla müşteriye kendi Sepeti ödeme işlem hattını kullanma daha kullanın. Daha az müşteriler, yorum eklemek veya satın alma geçmişlerini görüntüleyin. Ve büyük olasılıkla yalnızca birkaç çalışanlar, içerik ve pazarlama kampanyaları yönetmek için gereken tek bir bölgede sahipsiniz. Tek yapılı tasarım ölçeğini genişleterek tüm kodu birden çok kez dağıtılır.

"Her şey Ölçeklendir" sorun ek olarak, tüm uygulama ve tam yeniden dağıtma işlemi tüm örneklerin tam çözülüp tek bir bileşen değişiklikler gerektirir.

Tek parçalı bir yaklaşım için ortaktır ve bu mimari yaklaşım ile pek çok kuruluş geliştiriyorsunuz. Başkalarının ulaştığını anlayabilmesini olsa çok iyi yeterli sonuçları yaşıyorsunuz demektir. Çoğu uygulamalarını bu modelde, araçları ve altyapısı, hizmet odaklı mimarilerin (SOA) oluşturmak çok zor ve uygulama büyüdü kadar gereken görmediniz tasarlanmıştır. Tek parçalı bir yaklaşım sınırlarını aldığınızı bulursanız, uygulamanın kapsayıcıları ve mikro Hizmetleri daha iyi yararlanmasını sağlamak için bozucu sonraki mantıksal adım olabilir.

![](./media/image5-14.png)

Microsoft azure'da tek yapılı uygulamaları dağıtma, her örneği için özel VM'ler kullanarak gerçekleştirilebilir. Kullanarak [Azure sanal makine ölçek kümeleri](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), sanal makineleri kolayca ölçeklendirebilirsiniz. [Azure uygulama hizmetleri](https://azure.microsoft.com/services/app-service/) tek yapılı uygulamaları çalıştırabilir ve Vm'leri yönetmek zorunda kalmadan örneklerini kolayca ölçeklendirin. Azure uygulama hizmetleri, dağıtımını basitleştirme amacıyla da Docker kapsayıcıları tek örneğini çalıştırabilirsiniz. Docker kullanarak Docker konağı olarak tek bir VM dağıtma ve birden çok örneği çalıştırın. Azure, Şekil 5-14'te gösterildiği gibi kullanarak ölçeklendirme yönetebilirsiniz.

Çeşitli konaklarına dağıtım geleneksel dağıtım teknikleri ile yönetilebilir. Docker ana bilgisayarları gibi komutlarla yönetilebilir **docker run** sürekli teslim (CD) işlem hatları gibi el ile veya Otomasyon aracılığıyla gerçekleştirilir.

### <a name="monolithic-application-deployed-as-a-container"></a>Bir kapsayıcı dağıtılan tek parçalı uygulama

Tek parçalı uygulama dağıtımlarını yönetmek için kapsayıcılar'ı kullanmanın avantajları vardır. Kapsayıcı örnekleri ölçeklendirme, çok daha hızlı ve ek sanal makineleri dağıtma kolaydır. Bile sanal makine ölçek VM ölçek kümeleri kullanırken, örnek için zaman ayırın. Uygulama örnekleri olarak dağıtıldığında, uygulama yapılandırmasını VM bir parçası olarak yönetilir.

Docker görüntülerini çok daha hızlı olduğundan, güncelleştirmeleri dağıtmak ve etkili ağ. Docker görüntülerini genellikle piyasaya çıkarma hızlandırma saniyeler içinde başlayın. Bir Docker örneğini bozmadan verme olarak kadar kolay bir `docker stop` komutu, genellikle kısa bir saniye içinde tamamlanıyor.

Kapsayıcıları tasarım gereği kendiliğinden sabittir gibi güncelleştirme betikleri bazı belirli bir yapılandırma veya dosya sol için diskte hesabı Unut ancak, hiçbir zaman bozuk VM'ler hakkında endişelenmenize gerek.

Docker kapsayıcıları tek parça daha basit web uygulamaları dağıtımını için kullanabilirsiniz. Bu artırır sürekli tümleştirme ve sürekli dağıtım işlem hatları ve üretim için dağıtım başarı elde etmenize yardımcı olur. Daha fazla "neden üretimde çalışmaz makineme çalışır?"

Bir mikro hizmet tabanlı mimariye pek çok faydası vardır, ancak bu avantajlar bulunan artan karmaşıklık bedeli. Daha iyi bir seçenek tek bir kapsayıcı veya yalnızca birkaç kapsayıcıları çalışan bir tek parçalı dağıtım uygulaması, bu nedenle bazı durumlarda, maliyetler, ağır basıyor.

Tek parça bir uygulamayı kolayca iyi ayrılmış mikro hizmetler halinde decomposable olmayabilir. Mikro hizmetler karşı daha dayanıklı bir uygulama sağlamak için birbirinden çalışması gerekir. Uygulamanın bağımsız özellik dilimleri teslim edilemiyor, bu ayırma karmaşıklık yalnızca ekler.

Bir uygulama, özelliklerin bağımsız olarak ölçeklendirme henüz gerekmeyebilir. Görece basit, tüm örnek kopyalama işleminde birçok uygulama, tek bir örnekten fazlasına ölçeklendirilemez gerektiğinde bunu yapabilirsiniz. Basit ve ekonomik ölçeklendirme uygulamasının tam örneği olduğunda, ayrık Hizmetleri uygulamasına ayırmak için ek iş minimal avantajı sağlar.

Erken geliştirme bir uygulamanın, sizin dair NET bir fikir doğal işlevsel sınırları nerede sahip olmayabilir. En düşük uygun bir ürün geliştirirken, doğal ayrımı henüz çıkmıştır değil. Bu koşullar bazıları geçici olabilir. Tek parça bir uygulamayı oluşturun ve daha sonra bazı özellikleri geliştirilen ve mikro hizmet dağıtılan ayrı. Diğer koşullar, uygulamanın birden fazla mikro hizmetler halinde hiçbir zaman bozuk durumda, yani, uygulamanın sorun alanı için gerekli olabilir.

Bir uygulamaya birçok ayrı işlemler ayırma yükü tanıtır. Özellikler farklı işlemlere ayırmak daha karmaşık yoktur. İletişim protokolleri, daha karmaşık hale gelir. Yerine yöntem çağrılarını, hizmetler arasında zaman uyumsuz iletişim kullanmanız gerekir. Bir mikro hizmet mimarisi için taşırken, birçok hizmetine uygulama mikro hizmetler sürümünde yapı taşlarını eklemeniz gerekir: olay veri yolu işleme, ileti dayanıklılık ve yeniden denemeler, nihai tutarlılığa kadar giden ve daha fazla.

Çok daha kolay [eShopOnWeb başvuru uygulaması](https://github.com/dotnet-architecture/eShopOnWeb) tek kapsayıcı monolitik kapsayıcı kullanımını destekler. Uygulama, geleneksel MVC görünümleri, web API'leri ve Razor sayfaları içeren bir web uygulaması içerir. Bu uygulamayı kullanarak çözüm kök başlatılabilir `docker-compose build` ve `docker-compose up` komutları. Bu komut, web kapsayıcısı yapılandırır kullanarak örnek `Dockerfile` web projesinin kök dizininde bulunan ve belirtilen bir bağlantı noktası kapsayıcı çalışır. Bu uygulama kaynağını Github'dan indirip yerel olarak çalıştırın. Tek parça bu uygulama bir kapsayıcı ortamında dağıtılan fayda sağlar.

Biri için kapsayıcı dağıtımı uygulamanın her örneği aynı ortamda çalıştığı anlamına gelir. Bu, burada erken test ve geliştirme gerçekleşmesi Geliştirici ortamı içerir. Geliştirme ekibi, uygulamayı üretim ortamına eşleşen bir kapsayıcı ortamında çalıştırabilirsiniz.

Ayrıca, kapsayıcıya alınmış uygulamaları ölçek genişletme daha düşük maliyetle. Bir kapsayıcı ortamı kullanarak büyük kaynak geleneksel VM ortamları paylaşımı etkinleştirir.

Son olarak, ASP.NET'in, iş mantığı ve depolama sunucusu arasında bir ayrım zorlar. Uygulama Ölçeklendirmesi eşitlenene gibi birden çok kapsayıcı tümünü tek bir fiziksel depolama bir ortamda kullanır. Bu depolama ortamına genelde bir SQL Server veritabanı çalıştıran bir yüksek kullanılabilirlik sunucusu olacaktır.

## <a name="docker-support"></a>Docker desteği

`eShopOnWeb` Üzerinde .NET Core projesi çalıştırır. Bu nedenle, Windows tabanlı veya Linux tabanlı kapsayıcılar içinde çalıştırabilirsiniz. Aynı ana bilgisayar türü için SQL Server kullanmak istediğiniz bir dağıtım için Docker unutmayın. Linux tabanlı kapsayıcılar bir daha küçük kaplama alanı izin ve tercih edilir.

Visual Studio 2017 veya sonraki bir projeye sağ tıklayarak mevcut bir uygulamaya Docker desteği eklemek için kullanabileceğiniz **Çözüm Gezgini** seçip **Ekle** > **Docker Destek**. Bu, gerekli dosyaları ekler ve bunları kullanmak için projeyi değiştirir. Geçerli `eShopOnWeb` örnek zaten bu dosyaları yerinde sahiptir.

Çözüm düzeyinde `docker-compose.yml` dosya ne oluşturmak için görüntüler ve başlatmak için hangi kapsayıcıları hakkında bilgiler içerir. Dosya kullanmanıza olanak tanır `docker-compose` birden çok uygulama aynı anda başlatmak için komutu. Bu durumda, yalnızca Web projesi kullanıma sunuluyor. Bağımlılıklar, ayrı bir veritabanı kapsayıcısı gibi yapılandırmak için de kullanabilirsiniz.

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

`docker-compose.yml` Dosya başvuruları `Dockerfile` içinde `Web` proje. `Dockerfile` Nasıl uygulama üzerinde yapılandırılır ve hangi temel kapsayıcı kullanılacak belirtmek için kullanılır. `Web`' `Dockerfile`:

```
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

### <a name="troubleshooting-docker-problems"></a>Docker ile ilgili sorunları giderme

Kapsayıcılı uygulama çalıştırıldıktan sonra siz durduruncaya kadar çalışmaya devam eder. Çalışan kapsayıcıları görmek `docker ps` komutu. Çalışan kapsayıcıya kullanarak durdurabilirsiniz `docker stop` komut ve kapsayıcı kimliği belirtme

Çalışan Docker kapsayıcılar, aksi takdirde kullanılacak geliştirme ortamınızda deneyebilir bağlantı noktalarına bağlı olabilir olduğunu unutmayın. Çalıştırın veya çalışan bir Docker kapsayıcısı aynı bağlantı noktasını kullanarak bir uygulamanın hatalarını ayıklama kullanmayı denerseniz, sunucunun bu bağlantı noktasına bağlanamaz bildiren bir hata alırsınız. Bir kez daha, kapsayıcı durdurma Sorun giderildi.

Visual Studio'yu kullanarak uygulamanıza Docker desteği eklemek istiyorsanız, bunu yaptığınızda Docker Masaüstü çalıştığından emin olun. Docker Masaüstü çalışmıyorsa Sihirbazı başlattığınızda sihirbaz düzgün çalışmıyor. Ayrıca, sihirbazın geçerli kapsayıcı seçiminizi doğru Docker desteği Ekle inceler. Windows kapsayıcıları için destek eklemek istiyorsanız, Docker Windows yapılandırılmış kapsayıcılarla çalıştıran masaüstü varken, Sihirbazı çalıştırmak gerekir. Linux kapsayıcıları için destek eklemek istiyorsanız, yapılandırılmış Linux kapsayıcıları ile çalışan Docker varken Sihirbazı'nı çalıştırın.

### <a name="references--common-web-architectures"></a>Başvuruları – ortak web mimarileri
> - **Temiz mimarisi**  
>   <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **Çoklu kare mimarisi**  
>   <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **Depo düzeni**  
>   <https://deviq.com/repository-pattern/>
> - **Temiz mimarisi çözümü örneği**  
>   <https://github.com/ardalis/cleanarchitecture>
> - **E-kitap mikro hizmet mimarileri oluşturma**  
>   <https://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
>[Önceki](architectural-principles.md)
>[İleri](common-client-side-web-technologies.md)
