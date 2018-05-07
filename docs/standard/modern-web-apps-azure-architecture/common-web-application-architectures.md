---
title: Ortak web uygulama mimariler
description: ASP.NET Core ve Microsoft Azure ile modern web uygulamaları mimari | Ortak web uygulama mimariler
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: 943163ca4c82ad75f177ebe73559d909e7292c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="common-web-application-architectures"></a>Ortak Web uygulama mimariler

> "İyi mimarisi pahalı olduğunu düşünüyorsanız, hatalı mimarisi deneyin."  
> _-Brian altbilgi ve Joseph Yoder_

## <a name="summary"></a>Özet

Çoğu geleneksel .NET uygulamaları, yürütülebilir bir dosya ya da tek bir IIS appdomain içinde çalışan bir tek bir web uygulaması için karşılık gelen tek birim olarak dağıtılır. Bu basit dağıtım modeli ve birçok dahili ve daha küçük ortak uygulama çok iyi işlevi görür. Ancak, bile bu tek birim dağıtımının verildiğinde, en Önemsiz olmayan iş uygulamaları birkaç katmanlara mantıksal bazı ayrılması yararlanır.

## <a name="what-is-a-monolithic-application"></a>Tek yapılı bir uygulaması nedir?

Tek yapılı bir uygulama açısından davranışını tamamen kendi içinde yer alan, biridir. Kendi işlemleri sırasında diğer hizmetleri ya da veri depoları ile etkileşimde bulunabilir, ancak davranışını çekirdek kendi işlemi içinde çalıştırılan ve tüm uygulama genellikle tek bir birim olarak dağıtılır. Genellikle bu tür bir uygulama yatay ölçek gerekirse, tüm uygulama birden fazla sunucu veya sanal makineler arasında çoğaltılır.

## <a name="all-in-one-applications"></a>Hepsi bir arada uygulamaları

Bir uygulama mimarisi projelerde olabildiğince az sayıda biridir. Bu mimaride, uygulamanın tüm mantığı tek bir projede yer, tek bir derleme derlenmiş ve tek bir birim olarak dağıtılabilir.

Yeni bir ASP.NET Core projesi Visual Studio'da veya komut satırından oluşturulan olup olmadığını basit bir "hepsi bir arada" monolith başlar. Sunu, iş ve veri erişim mantığı dahil uygulamanın davranışını hepsini içerir. Şekil 5-1 tek proje uygulama dosya yapısını gösterir.

**Şekil 5-1.** Tek bir proje ASP.NET Core uygulama

![](./media/image5-1.png)

Bir tek proje senaryosunda, sorunları ayrılması klasörleri kullanımı ile elde edilir. Veri ve hizmetler için MVC düzeni sorumluluklarını modeller, görünümler ve denetleyiciler ayrı klasörlerini yanı sıra, ek klasörler varsayılan şablonu içerir. Bu düzenlemenin sunu ayrıntıları görünümleri klasörüne mümkün olduğunca çok sınırlı ve veri erişim uygulama ayrıntılarını sınıfları veri klasöründe tutulan sınırlı olması gerekir. İş mantığı, hizmetleri ve sınıfları modeller klasörü içinde bulunmalıdır.

Basit rağmen proje tek tek yapılı çözüm bazı dezavantajları vardır. Proje boyutu ve karmaşıklığı büyüdükçe, dosya ve klasörleri sayısı da büyümeye devam edecek. Kullanıcı Arabirimi sorunları (modeller, görünümler, denetleyicileri) birlikte alfabetik olarak gruplandırılmaz, birden çok klasörlerde bulunur. Bu sorunu daha zayıf için filtreleri veya ModelBinders, gibi ek kullanıcı Arabirimi düzeyi yapıları kendi klasörlerinde eklenen alır. İş mantığı arasında modelleri ve Hizmetleri klasörleri dağılmış ve hangisinin hangi klasörlerin sınıflarda hangi diğerlerine bağlı NET bir belirti yok. İçin proje düzeyinde kuruluş bu eksiklik sık müşteri adayları [spaghetti kod](http://deviq.com/spaghetti-code/).

Bu sorunları gidermek için uygulamalar genellikle birden çok proje çözümü, burada her proje olarak kabul belirli bir bulunması halinde gelişmesi *katman* uygulamanın.

## <a name="what-are-layers"></a>Katmanları nelerdir?

Uygulamaları karmaşıklığı arttıkça, bu karmaşıklık yönetmek için bir uygulamanın kendi sorumluluklarını veya kaygılarınız göre ayırmak için yoludur. Bu sorunları ilkesine ayrılması izler ve geliştiricilerin kolayca bazı işlevleri burada uygulanan bulabilmesi için düzenlenmiş büyüyen bir codebase korunmasına yardımcı olabilirsiniz. Katmanlı mimarisi, çok sayıda avantaj yalnızca kodu kuruluş dışına yine de sunar.

Kod katmanlara düzenleyerek, ortak bir alt düzey işlevselliği uygulama genelinde yeniden kullanılabilir. Bu yeniden daha az kod yazılması gereken gösterdiğinden ve KURU ilkesini izleyen tek bir uygulama üzerinde standart hale getirmek uygulama izin vermek için faydalıdır.

Bir katmanlı mimarisiyle uygulamaları Katmanlar diğer katmanları ile iletişim kurabilen kısıtlamaları zorunlu kılabilir. Bu kapsülleme elde etmek için yardımcı olur. Bir katman değiştirilmiş ya da değiştirilen ile çalışan katmanları etkilenmiş. Hangi sınırlayarak, böylece tek bir değişiklik tüm uygulama etkilemez diğer katmanları değişikliklerin etkisini azaltılabilir Katmanlar bağlıdır.

Katmanlar (ve saklama) çok uygulamadaki işlevin yerini kolaylaştırır. Örneğin, uygulamanın kendi SQL Server veritabanı kalıcılığını başlangıçta kullanabilir, ancak daha sonra bir bulut tabanlı Kalıcılık stratejisi veya web API'si arkasında kullanmayı tercih edebilirsiniz. Uygulamanın düzgün mantıksal katman içinde Kalıcılık uygulaması kapsüllenmiş, bu SQL Server belirli katmanı aynı Ortak arabirimi uygulama yeni bir tane tarafından değiştirilebilir.

Gereksinimleri gelecekteki değişikliklere yanıt uygulamalarında çıkışı takas olası ek olarak, uygulama katmanları Ayrıca, test amacıyla uygulamaları takas etmek kolaylaştırabilir. Gerçek veri katmanı veya uygulamanın UI katmanı karşı çalışan testleri yazmak yerine, bu Katmanlar test zaman isteklerine bilinen yanıtlar sağlayan sahte uygulamalarıyla birlikte değiştirilebilir. Bu genellikle testleri yazmak çok daha kolay ve çok daha hızlı hale getirir çalışması için karşılaştırıldığında testlerinin yeniden uygulamanın gerçek altyapı.

Mantıksal katmanlama Kurumsal yazılım uygulamaları kodda organizasyonu geliştirmek için ortak bir tekniktir ve kod katmanlara düzenlenebilir birkaç yolu vardır.

> [!NOTE]
> *Katmanlar* mantıksal ayırma uygulama içinde temsil eder. Uygulama mantığını fiziksel sunucuları veya işlemler ayırmak için Dağıtılmış gelmesi durumunda, bu ayrı fiziksel dağıtım hedefleri olarak adlandırılır *katmanları*. Bu olası ve oldukça yaygın, tek bir katman için Dağıtılmış bir N katmanlı uygulamalara sahip olur.

## <a name="traditional-n-layer-architecture-applications"></a>Geleneksel "N katmanlı" mimarisi uygulamaları

Uygulama mantığını en yaygın organizasyonu, Şekil 5-2'de gösterilen Katmanlar.

**Şekil 5-2.** Genel uygulama katmanları.

![](./media/image5-2.png)

Bu katmanlar sık UI kısaltılır BLL (iş mantığı katmanı) ve DAL (veri erişim katmanı). Bu mimarisi kullanarak, kullanıcılar yalnızca BLL ile etkileşime giren UI katmanında isteklerini olun. BLL, buna karşılık, veri erişim istekleri için DAL çağırabilirsiniz. UI katmanında tüm istekler DAL ile doğrudan yapmamanız gerekir ya da kalıcılığı doğrudan arasında başka yollarla ile etkileşim. Benzer şekilde, BLL yalnızca ile kalıcılığı DAL giderek etkileşim. Bu şekilde, iyi bilinen sorumluluğunu her katman vardır.

Bu geleneksel katmanlama yaklaşımın bir dezavantajı, derleme zamanı bağımlılıkları üstten alta çalıştırın olabilir. Diğer bir deyişle, kullanıcı Arabirimi katman üzerinde DAL bağlıdır BLL bağlıdır. Bu, genellikle en önemli mantığı uygulamada tutan BLL veri erişim uygulama ayrıntıları (ve genellikle bir veritabanı varlığını) bağımlı olduğu anlamına gelir. İş mantığı bu tür bir mimaride sınama genellikle bir test veritabanı gerektiren zor olabilir. Sonraki bölümde göreceğiniz gibi bağımlılık ters çevirmeyi ilkesini bu sorunu gidermek için kullanılabilir.

Şekil 5-3 uygulama üç projelere sorumluluk (veya katman) yeni bir örnek çözümü gösterir.

**Şekil 5-3.** Üç projeleri ile basit bir tek yapılı uygulamasının.

![](./media/image5-3.png)

Bu uygulamayı Kurumsal amaçlara yönelik birkaç proje kullansa da, tek bir birim olarak hala dağıtılır ve istemcileri ile bir tek bir web uygulaması gibi etkileşim. Bu, çok basit dağıtım işlemine izin verir. Şekil 5-4 gösterir bu tür bir uygulama nasıl olabileceği Windows azure'da barındırılan.

![](./media/image5-4.png)

**Şekil 5-4.** Azure Web uygulaması, basit dağıtım

Uygulama büyüme gereksinimlerine göre daha karmaşık ve güçlü dağıtım çözümleri gerekli olabilir. Şekil 5-5 ek özellikleri desteklemektedir daha karmaşık bir dağıtım planı örneği gösterilmektedir.

![](./media/image5-5.png)

**Şekil 5-5.** Bir Azure App Service'e bir web uygulaması dağıtma

Dahili olarak, birden çok proje üzerinde sorumluluk göre bu projenin kuruluşunuzun Uygulama Bakımı artırır.

Bu birim veya bulut tabanlı isteğe bağlı ölçeklenebilirlik yararlanmak için genişletilebilir. Ölçeklendirmeyi ek CPU, bellek, disk alanı veya diğer kaynakları uygulamanızı barındırma sunucuları ekleme anlamına gelir. Bu fiziksel sunucularda veya sanal makinelerde olup ölçeğini ek örneklerini bu sunucular ekleme anlamına gelir. Uygulamanız birden çok örneklerinde barındırıldığında, bir yük dengeleyici isteklerinin tek tek uygulama örneklerine atamak için kullanılır.

Azure üzerinde bir web uygulaması Ölçeklendirmesi en kolay yaklaşım, uygulamanın uygulama hizmeti planı'nda el ile ölçeklendirme yapılandırmaktır. Şekil 5-6 kaç tane örnek bir uygulama hizmet yapılandırmak için uygun Azure Pano ekranı gösterir.

![](./media/image5-6.png)

**Şekil 5-6.** App Service, Azure içinde ölçeklendirme planı.

## <a name="clean-architecture"></a>Temiz mimarisi

Bağımlılık ters çevirmeyi ilkesine yanı sıra Domain-Driven tasarım (DDD) İlkeleri izleyin uygulamalar benzer bir mimariye gelmesini eğilimindedir. Bu mimari yıllar içinde birçok adlarıyla geçti. İlk adlarından birini Altıgen bağlantı noktaları-ve-bağdaştırıcıları tarafından izlenen, mimarisidir. Daha kısa süre önce onu olarak alıntı olarak [çoklu kare mimarisi](http://jeffreypalermo.com/blog/the-onion-architecture-part-1/) veya [temiz mimarisi](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Bu e-kitap mimarisinde açıklamak için temel olarak kullanılan temiz mimari, son bu adı var.

> [!NOTE]
> Temiz mimarisi olmayan olanlar için DDD ilkeleri kullanılarak oluşturulan uygulamaların uygulanabilir terim DDD kullanılarak oluşturulmuştur. Eski olması durumunda bu birleşimi için "Temiz DDD mimari" adlandırılabilir.

Temiz mimarisi uygulama Merkezi'nde iş mantığı ve uygulama modeli koyar. Veri erişimi veya diğer altyapı sorunları bağımlı iş mantığı sahip olmak yerine bu bağımlılığı ters: altyapı ve uygulama ayrıntıları uygulama Çekirdeğinde bağlıdır. Bu altyapı katmanında tanımlanan türleri tarafından uygulanan uygulama çekirdek soyutlamalar veya arabirimlerini tanımlayarak sağlanır. Bu mimari görselleştirme en yaygın yolu eşmerkezli daireler, bir çoklu kare benzer bir dizi kullanmaktır. Şekil 5-X mimari gösteriminin bu stili örneği gösterilmektedir.

![](./media/image5-7.png)

**Şekil 5-7.** Temiz mimarisi; Çoklu kare görünümü

Bu diyagramda, bağımlılıklar doğru içteki daire akışı. Bu nedenle, (hangi adını konumundan Bu diyagramda, çekirdek alır) uygulama çekirdek diğer uygulama katmanları bağımlılık olduğunu görebilirsiniz. Çok merkezinde uygulamanın varlıkları ve arabirimleri ' dir. Yalnızca dışında ancak yine de uygulama çekirdek, iç daire içinde tanımlanan arabirimleri genellikle uygulama etki alanı Hizmetleri değildir. Uygulama çekirdek dışında kullanıcı arabirimi ve altyapı Katmanlar uygulama çekirdeği üzerinde ancak bir diğer (zorunlu) bağlıdır.

Şekil 5-X daha iyi kullanıcı Arabirimi ve diğer katmanları arasındaki bağımlılığı yansıtan daha geleneksel yatay katman diyagramını gösterir.

![](./media/image5-8.png)

**Şekil 5-8.** Temiz mimarisi; Yatay Katman görünümü

Not yalnızca çalışma zamanı bağımlılık kesikli oku temsil ederken, düz okları derleme zamanı bağımlılıkları temsil eder. Temiz mimarisi kullanarak, uygulama çekirdek derleme zamanında tanımlanan arabirimlerle UI katmanında çalışır ve ideal olarak uygulama türleri bilgisi altyapı katmanda tanımlamadığınız. Mevcut ve bağımlılık ekleme aracılığıyla uygulama çekirdek arabirimleri kadar kablolu olması gerekir böylece çalışma zamanında, ancak, bu uygulama türleri uygulamanın yürütmek için gerekli olacaktır.

Şekil 5-9 bu önerileri yapılandırıldığında ASP.NET Core uygulamanın mimarisinin ayrıntılı görünümünü gösterir.

![ASPNET çekirdek mimarisi](./media/image5-9.png)

**Şekil 5-9.** Temiz mimarisi aşağıdaki ASP.NET Core mimarisi diyagramı.

Uygulama çekirdek altyapısına bağımlı değil çünkü bu katman için otomatik birim testleri yazma çok kolaydır. Şekil 5-10 ve 5-11 testleri bu mimariye nasıl uyduğunu gösterir.

![UnitTestCore](./media/image5-10.png)

**Şekil 5-10.** Birim yalıtım modunda uygulama çekirdek testi.

![IntegrationTests](./media/image5-11.png)

**Şekil 5-11.** Dış bağımlılıkları altyapı uygulamaları sınama tümleştirme.

UI katmanında altyapı proje tanımlanan türlerinde doğrudan herhangi bir bağımlılığı olmadığından benzer şekilde test kolaylaştırmak için ya da uygulamaları veya uygulama gereksinimleri değiştirme yanıt değiştirilecek çok kolaydır. ASP.NET Core'nın yerleşik kullanımını ve bağımlılık ekleme desteği yapısı Önemsiz olmayan tek yapılı uygulamalar için en uygun şekilde bu mimari sağlar.

Tek yapılı uygulamalar için uygulama çekirdek, altyapı ve kullanıcı arabirimi projeleri tümü tek bir uygulama olarak çalıştırılır. Çalışma zamanı uygulama mimarisi şey Şekil 5-12'gibi görünebilir.

![ASPNET çekirdek mimarisi 2](./media/image5-12.png)

**Şekil 5-12.** Bir örnek ASP.NET Core uygulamanın çalışma zamanı mimarisi.

### <a name="organizing-code-in-clean-architecture"></a>Temiz mimarisinde kod düzenleme

Bir temiz mimarisi çözümü her proje Temizle sorumlulukları vardır. Bu nedenle, belirli türleri her projeye ait ve bu tür uygun projesinde karşılık gelen klasörleri sık bulabilirsiniz.

Uygulama çekirdek varlıklar, hizmet ve arabirimi içerir iş modeli tutar. Bu arabirimleri altyapısı, veri erişimi, dosya sistemi erişimi, ağ çağrıları, vb. gibi kullanılarak gerçekleştirilen işlemleri için soyutlamalar içerir. Bazen Hizmetleri veya bu katmanda tanımlanan arabirimleri hiçbir kullanıcı Arabirimi veya altyapı bağımlı varlık olmayan türleriyle çalışmak gerekir. Bu basit veri aktarım nesneleri (DTOs) tanımlanabilir.

> ### <a name="application-core-types"></a>Uygulama çekirdek türleri
> -   Varlıkları (kalıcı iş modeli sınıflar)
> -   Arabirimler
> -   Hizmetler
> -   DTOs

Altyapı proje genellikle veri erişimi uygulamaları içerir. Tipik bir ASP.NET Core web uygulamasında bu Entity Framework DbContext, tanımlanmış herhangi EF çekirdek geçişler ve veri erişim uygulama sınıfları içerir. Veri erişim uygulama kodu soyut en yaygın kullanım yoluyla yoludur [depo tasarım desenini](http://deviq.com/repository-pattern/).

Veri erişimi uygulamaları yanı sıra uygulamaları altyapı sorunları ile etkileşimde hizmetleri altyapısı projesi içermelidir. Hizmetlerin uygulama çekirdek tanımlanan arabirimleri uygulamanız gerekir ve bu nedenle altyapı uygulama çekirdek projesine bir başvuru sahip olmalıdır.

> ### <a name="infrastructure-types"></a>Altyapı türleri
> -   EF çekirdek türleri (DbContext, geçiş)
> -   Veri erişim uygulama türleri (depoları)
> -   Altyapı özgü hizmetler (FileLogger, SmtpNotifier, vb.)

ASP.NET Core MVC uygulamasındaki kullanıcı arabirimi katmanı uygulaması için giriş noktası olacaktır ve ASP.NET Core MVC projesinde olacaktır. Bu proje uygulama çekirdek projeye başvuruda bulunmalıdır ve türlerinden kesinlikle uygulama çekirdek tanımlanan arabirimleri aracılığıyla altyapısıyla etkileşim. Hiçbir sayısı doğrudan örneklemesi (veya statik çağrıları) altyapısı katman türleri UI katmanda izin.

> ### <a name="ui-layer-types"></a>UI katman türleri
> -   Denetleyiciler
> -   FilTReleri
> -   Görünümler
> -   ViewModels
> -   Başlangıç

Başlangıç sınıfı ve kablolama uygulama türleri yukarı uygulamayı yapılandırma için çalışma zamanında düzgün çalışması bağımlılık ekleme izin vererek arabirimlerine sorumludur.

> [!NOTE]
> Bağımlılık yerleştirmeye UI projesinin ConfigureServices haline dosyasındaki wire için proje altyapısı projesi başvurmanız gerekebilir. Bu bağımlılık, en kolay özel dı kapsayıcısını kullanarak ortadan kaldırılabilir. Bu örnek amaçları doğrultusunda, en kolay yaklaşım altyapısı projesi başvurmak kullanıcı Arabirimi proje izin vermektir.

## <a name="monolithic-applications-and-containers"></a>Tek yapılı uygulamaları ve kapsayıcıları 

Bir tek ve dağıtım tek yapılı tabanlı Web uygulaması veya hizmeti oluşturmak ve bir kapsayıcı olarak dağıtın. Uygulama içinde bu tek yapılı ancak birkaç kitaplıkları, bileşenler veya katmanlar halinde düzenlenmiş olmayabilir. Harici olarak bunu bir tek tek bir işlem, tek bir web uygulaması veya tek bir hizmet gibi kapsayıcıdır.

Bu model yönetmek için uygulamayı temsil etmek için tek bir kapsayıcı dağıtın. Ölçeklendirmek için önde bir yük dengeleyici ile ek kopyalar eklemeniz yeterlidir. Basitlik, tek bir dağıtım bir tek kapsayıcı veya VM yönetme gelir.

![](./media/image5-13.png)

Şekil 5-X gösterildiği gibi birden çok bileşenleri/kitaplıklarına veya her kapsayıcı içindeki iç katmanları içerebilir. Ancak, kapsayıcı asıl, aşağıdaki *"bir kapsayıcı bir şeyi yapar ve tek bir işlemde mu*", tek yapılı desen bir çakışma olabilir.

Bu yaklaşımın bir dezavantajı olursa/uygulama büyürken ölçeklendirmek için gerektiren gelir. Tüm uygulama ölçeklendirilmiş, onu gerçekten bir sorun değildir. Bununla birlikte, çoğu durumda, birkaç uygulama ölçeklendirme, diğer bileşenler durumdayken gerektiren sıkıştırma noktaları daha az kullanılan bölümlerdir.

Tipik bir e-ticaret örneğinde; büyük olasılıkla ölçeklendirmek gerekenler ürün bilgi bileşendir. Birçok daha fazla müşteri ürünleri bunları satın daha göz atın. Daha fazla müşteriler kendi Sepeti ödeme işlem hattını kullanma daha kullanın. Daha az müşteriler, yorum eklemek veya satın alma geçmişlerini görüntüleyin. Ve büyük olasılıkla, içerik ve pazarlama kampanyaları yönetmek için gerekli olan tek bir bölgedeki çalışanlar sayıda yeterlidir. Tek yapılı tasarım ölçeklendirme tarafından tüm kod birden çok kez dağıtılır.

Ölçeğin ek olarak, tüm uygulama ve tüm örnekleri tam çözümünüzün yeniden dağıtımını tam retesting sorun, her şeyi tek bir bileşen değişiklikler gerektirir.

Tek yapılı bir yaklaşım yaygındır ve birçok kuruluş bu mimari yaklaşımda geliştirme. Başkalarının sınırları devreyi sırada çok iyi yeterli sonuçları yaşıyor. Birçok uygulamalarını bu modelde, çünkü araçları ve altyapısı hizmet odaklı mimari (SOA) oluşturmak çok zor ve uygulama büyüdü kadar gereken - bkz kaydetmedi tasarlanmıştır. Tek yapılı bir yaklaşım sınırları basarsa bulursanız, daha iyi kapsayıcıları ve mikro yararlanan etkinleştirmek için uygulama ayırma sonraki mantıklı adım olabilir.

![](./media/image5-14.png)

Microsoft azure'da tek yapılı uygulamaları dağıtma, özel VM'ler için her bir örneği kullanılarak gerçekleştirilebilir. Kullanarak [Azure VM ölçek kümesi](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), sanal makineleri kolayca ölçeklendirebilirsiniz. [Azure App Services](https://azure.microsoft.com/services/app-service/) tek yapılı uygulamaları çalıştırabilir ve sanal makineleri yönetmek zorunda kalmadan örnekleri kolayca ölçeklendirin. Azure App Services Dağıtımı basitleştirme Docker kapsayıcıları de, tek tek örneklerini çalıştırabilirsiniz. Docker kullanarak, Docker ana bilgisayar olarak tek bir VM'yi dağıtmak ve birden çok örneği çalıştırın. Şekil 5-14'te gösterildiği gibi Azure dengeleyici kullanarak ölçeklendirme yönetebilirsiniz.

Çeşitli konakları dağıtımına geleneksel dağıtım teknikleri ile yönetilebilir. Docker ana bilgisayarları gibi komutlarla yönetilebilir **çalıştırmak docker** sürekli teslim (CD) ardışık düzenleri gibi el ile veya Otomasyon aracılığıyla gerçekleştirilir.

### <a name="monolithic-application-deployed-as-a-container"></a>Bir kapsayıcı olarak dağıtılan tek yapılı uygulaması

Tek yapılı uygulama dağıtımlarını yönetmek için kapsayıcıları kullanmanın yararları vardır. Kapsayıcıları örneklerini ölçeklendirme çok daha hızlı ve ek sanal makineleri dağıtma daha kolay olur. VM ölçek kümesi VM ölçeklendirme kullanırken bile, örneğine zaman ayırın. Uygulama örnekleri dağıtıldığında, uygulama yapılandırmasını VM bir parçası olarak yönetilir.

Şu ana kadar daha hızlı Docker görüntüleri olarak güncelleştirmeleri dağıtmak ve ağ verimli. Docker görüntüleri genellikle piyasa sürümlerini hızlandırma saniye cinsinden başlatın. Docker örneği hattının kaldırılması veren olarak kadar kolay bir **docker Dur** genellikle değerinden bir saniyede Tamamlanıyor komutu.

Kapsayıcıları tasarım gereği kendiliğinden değişmez, güncelleştirme kodları bazı belirli yapılandırma veya dosya soldan için diskte hesap unuttunuz ancak hiçbir zaman bozuk VM'ler hakkında endişelenmeniz gerekir.

Tek yapılı uygulamaları Docker, ölçeklendirilebilir, alt sistemlerini tek yapılı uygulamasına çiğnemekten yararlanabilir geliştirilen ve tek tek dağıtılan giriş noktanızdır mikro, bölge olabilir.

> ### <a name="references--common-web-architectures"></a>Başvuruları – ortak Web mimariler
> - **Temiz mimarisi**  
> <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **Çoklu kare mimarisi**  
> <http://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **Depo düzeni**  
> <http://deviq.com/repository-pattern/>
> - **Temiz mimarisi çözümü örneği**  
> <https://github.com/ardalis/cleanarchitecture>
> - **Mikro e-kitap mimarisi oluşturma** <http://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
[Önceki] (Mimari-principles.md) [sonraki] (ortak-istemci-tarafı-web-technologies.md)
