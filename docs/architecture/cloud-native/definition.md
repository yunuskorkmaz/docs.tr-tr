---
title: Bulutta Yerel'i tanımlama
description: Bulut-yerel sistemler için temel temel sütunlar hakkında bilgi edinin
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 756a2565bd77fcef19a5f15579987836ff0e75a4
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989096"
---
# <a name="defining-cloud-native"></a>Bulut un yerel ini tanımlama

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Yaptığın şeyi bırak ve on iş arkadaşına mesaj at. "Bulut Yerlisi" terimini tanımlamalarını isteyin. Sekiz farklı cevap alma şansın yüksek.

Bulut yerlisi, kritik iş sistemleri oluşturma hakkındaki düşüncemizi değiştirmekle ilgilidir.

Bulut ait sistemler hızlı değişimi, büyük ölçekliliği ve esnekliği kucaklayacak şekilde tasarlanmıştır.

Cloud Native Computing Foundation resmi bir [tanım](https://github.com/cncf/foundation/blob/master/charter.md)sağlar:

> *Bulut tabanlı teknolojiler, kuruluşların genel, özel ve karma bulutlar gibi modern, dinamik ortamlarda ölçeklenebilir uygulamalar oluşturmasını ve çalıştırmasını sağlar. Konteynerler, servis meshes, mikrohizmetler, değişmez altyapı ve bildirimsel API'ler bu yaklaşım afiyet.*

> *Bu teknikler esnek, yönetilebilir ve gözlemlenebilir gevşek birleştirilmiş sistemleri sağlar. Sağlam otomasyonla birlikte, mühendislerin en az zahmetle sık ve öngörülebilir yüksek etkili değişiklikler yapmalarına olanak sağlar.*

Uygulamalar giderek daha fazla talep eden kullanıcılar ile karmaşık hale gelmiştir. Kullanıcılar hızlı yanıt verme, yenilikçi özellikler ve sıfır kapalı kalma süresi bekler. Performans sorunları, yinelenen hatalar ve hızlı hareket edememe artık kabul edilemez. Kolayca rakibine geçerler.

Bulut yerli *hız* ve *çeviklik*hakkında çok şey var. İş sistemleri, iş yeteneklerini etkinleştirmekten stratejik dönüşüm silahlarına, iş hızını ve büyümesini hızlandırmaya kadar gelişmektedir. Fikirleri hemen piyasaya almak zorunludur.

İşte bu teknikleri uygulayan bazı şirketler. Hızlarını, çevikliği ve ölçeklenebilirliği düşünün.

| Şirket | Deneyim |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Üretimde 600'den fazla hizmeti vardır. Günde yüz kez dağılır. |
| [Uber](https://eng.uber.com/micro-deploy/) | Üretimde depolanan 1.000'den fazla hizmete sahiptir. Her hafta birkaç bin yapı dağıtıyor. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Üretimde 300'den fazla hizmeti vardır. Günde neredeyse 1000 değişiklik yapar. |

Gördüğünüz gibi Netflix, Uber ve WeChat yüzlerce bağımsız mikro hizmetten oluşan sistemleri ortaya çıkarır. Bu mimari üslup, piyasa koşullarına hızla yanıt vermelerini sağlar. Canlı, karmaşık bir uygulamanın küçük alanlarını anında güncelleyebilir ve gerektiğinde bu alanları tek tek ölçeklendirebilirler.

Bulut yerlisinin hızı ve çevikliği bir dizi faktörden kaynaklanır. En önemlisi bulut altyapısıdır. Şekil 1-3'te gösterilen beş temel sütun da bulut alaşeli sistemler için temel taşı sağlar.

![Bulut ayarı temel direkleri](./media/cloud-native-foundational-pillars.png)

**Şekil 1-3**. Bulut ayarı temel direkleri

Her sütunun önemini daha iyi anlamak için biraz zaman ayıralım.

## <a name="the-cloud"></a>Bulut...

Bulut ayarı sistemler bulut hizmeti modelinden tam olarak yararlanır.

Dinamik, sanallaştırılmış bir bulut ortamında gelişmek üzere tasarlanan bu sistemler, [Hizmet Olarak Platform'u (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) bilgi işlem altyapısı ndan ve yönetilen hizmetlerden geniş ölçüde kullanır. Temel altyapıyı, dakikalar içinde sağlanan ve otomasyon yoluyla yeniden boyutlandırılan, ölçeklendirilmiş, taşınan veya imha edilen *tek kullanımlık* olarak ele almaktadırlar.

[Hayvanlar vs Sığır](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313)yaygın olarak kabul DevOps kavramı düşünün. Geleneksel bir veri merkezinde, sunucular *Evcil Hayvan*olarak kabul edilir: fiziksel bir makine, anlamlı bir ad verilir ve bakılır. Aynı makineye daha fazla kaynak ekleyerek (ölçeklendirme) ölçeklendirin. Sunucu hastalanırsa, sağlığına geri gidersiniz. Sunucu kullanılamaz hale gelirse, herkes fark eder.

*Sığır* hizmet modeli farklıdır. Her örneği sanal bir makine veya kapsayıcı olarak karşılarsınız. Aynıdır lar ve Service-01, Service-02 gibi bir sistem tanımlayıcısı atanırlar. Daha fazlasını oluşturarak ölçeklendirin (ölçeklendirin). Biri müsait olmadığında, kimse fark etmez.

Sığır modeli *değişmez altyapıyı*benimser. Sunucular onarılmaz veya değiştirilmez. Biri başarısız olursa veya güncellemeyi gerektiriyorsa, yok edilir ve yenisi sağlanır – hepsi otomasyon yoluyla yapılır.

Bulut-yerli sistemler Sığır hizmet modelini benimser. Çalıştıkları makinelere bakılmaksızın altyapı ölçeklendikçe veya çıkarken çalışmaya devam ederler.

Azure bulut platformu, otomatik ölçekleme, kendi kendine iyileştirme ve izleme özellikleriyle bu tür son derece esnek altyapıyı destekler.

## <a name="modern-design"></a>Modern tasarım

Bulut ayarı olan bir uygulamayı nasıl tasarlarsınız? Mimarin nasıl olurdu? Hangi ilkelere, kalıplara ve en iyi uygulamalara uyacaksınız? Hangi altyapı ve operasyonel kaygılar önemli olacak?

### <a name="the-twelve-factor-application"></a>On iki faktörlü uygulama

Bulut tabanlı uygulamalar oluşturmak için yaygın olarak kabul edilen bir metodoloji [Oniki Faktör Uygulamasıdır.](https://12factor.net/) Geliştiricilerin modern bulut ortamları için optimize edilmiş uygulamalar oluşturmak için izlediği bir dizi ilke ve uygulamayı açıklar. Ortamlar ve bildirimsel otomasyon arasında taşınabilirliğe özel önem verilir.

Web tabanlı herhangi bir uygulama için geçerli olmakla birlikte, birçok uygulayıcı bunu buluta özgü uygulamalar oluşturmak için sağlam bir temel olarak görmektedir. Bu ilkeler üzerine inşa edilmiş sistemler, pazar değişikliklerine hızlı bir şekilde tepki verecek özellikler dağıtabilir ve ölçeklendirilebilir.

Aşağıdaki tabloda On iki faktörlü metodoloji vurgulanır:

|    |  Faktörü | Açıklama  |
| :-------- | :-------- | :-------- |
| 1 | Kod Tabanı | Her microservice için tek bir kod tabanı, kendi deposunda saklanır. Sürüm denetimi ile izlenen, birden çok ortama (QA, Evreleme, Üretim) dağıtılabilir. |
| 2 | Bağımlılıklar | Her microservice, tüm sistemi etkilemeden değişiklikleri kucaklayarak kendi bağımlılıklarını yalıtır ve paketler. |
| 3 | Yapılandırmalar  | Yapılandırma bilgileri mikro hizmetin dışına taşınır ve kodun dışındaki bir yapılandırma yönetim aracı aracılığıyla dışsallaştırılır. Aynı dağıtım, uygulanan doğru yapılandırmayla ortamlar arasında yayılabilir.  |
| 4 | Destek Hizmetleri | Yardımcı kaynaklar (veri depoları, önbellekler, ileti aracıları) adreslenebilir bir URL üzerinden açıklanmalıdır. Bunu yapmak, kaynağı uygulamadan ayırarak değiştirilebilir olmasını sağlar.  |
| 5 | Oluşturma, Serbest Bırakma, Çalıştırma | Her sürüm, yapı, sürüm ve çalıştırma aşamaları arasında katı bir ayrım uygulamalıdır. Her biri benzersiz bir kimlikle etiketlenmeli ve geri dönme yeteneğini desteklemelidir. Modern CI/CD sistemleri bu ilkeyi gerçekleştirmeye yardımcı olur. |
| 6 | İşlemler | Her microservice, diğer çalışan hizmetlerden izole edilmiş kendi işleminde yürütmelidir. Dağıtılmış önbellek veya veri deposu gibi bir destek hizmeti için gerekli durumu dışsallaştırın. |
| 7 | Bağlantı Noktası Bağlama | Her microservice kendi bağlantı noktasında maruz kendi arayüzleri ve işlevselliği ile kendi kendine yeten olmalıdır. Bunu yapmak diğer mikro hizmetlerden izolasyon sağlar. |
| 8 | Eşzamanlılık | Hizmetler, mevcut en güçlü makinede tek bir büyük örneği ölçeklendirmenin aksine çok sayıda küçük özdeş işlem (kopya) arasında ölçeklendirilir. |
| 9 | Tek kullanımlık | Hizmet örnekleri tek kullanımlık olmalı, ölçeklenebilirlik fırsatlarını ve sistemi doğru durumda bırakmak için zarif kapatmaları artırmak için hızlı başlatmaları tercih ediyor. Docker konteynerler bir orkestratör ile birlikte doğal olarak bu gereksinimi karşılamak. |
| 10 | Dev/Prod Paritesi | Uygulama yaşam döngüsündeki ortamları mümkün olduğunca benzer şekilde tutun ve maliyetli kısayolları önleyebilirsiniz. Burada, konteynerlerin benimsenmesi büyük ölçüde aynı yürütme ortamı teşvik ederek katkıda bulunabilir. |
| 11 | Günlüğe kaydetme | Mikro hizmetler tarafından oluşturulan günlükleri olay akışları olarak ele a.ş. Bunları bir olay toplayıcısı ile işleyin ve verileri Azure Monitor veya Splunk ve sonunda uzun vadeli arşivleme gibi veri madenciliği/günlük yönetimi araçlarına yayıltın. |
| 12 | Yönetici İşlemleri | Yönetim/yönetim görevlerini tek seferlik işlemler olarak çalıştırın. Görevler, bir rapor için veri temizleme ve çekme analitiği içerebilir. Bu görevleri yürüten araçlar, üretim ortamından, ancak uygulamadan ayrı olarak çağrılmalıdır. |

Kitapta, [Beyond the Twelve-Factor App](https://content.pivotal.io/blog/beyond-the-twelve-factor-app), yazar Kevin Hoffman ayrıntıları her orijinal 12 faktör (2011 yılında yazılmış). Ayrıca, kitap günümüzün modern bulut uygulama tasarımı yansıtan üç ek faktör sağlar.

|    |  Yeni Faktör | Açıklama  |
| :-------- | :-------- | :-------- |
| 13 | ÖNCE API | Her şeyi bir hizmet haline getirin. Kodunuzu bir ön uç istemci, ağ geçidi veya başka bir hizmet tarafından tüketilen olacağını varsayalım. |
| 14 | Telemetri | Bir iş istasyonunda, uygulamanızda ve davranışlarında derin görünürlüğe sahipsiniz. Bulutun içinde, yok. Tasarımınızın izleme, etki alanına özgü ve sistem/sistem verilerini içerdiğinden emin olun. |
| 15 | Kimlik Doğrulama/ Yetkilendirme  | Kimliği baştan uygulayın. Genel bulutlarda kullanılabilen [RBAC (rol tabanlı erişim denetimi)](https://docs.microsoft.com/azure/role-based-access-control/overview) özelliklerini göz önünde bulundurun.  |

Bu bölümde ve kitap boyunca 12+ faktörün çoğuna atıfta bulunacağız.

### <a name="critical-design-considerations"></a>Kritik Tasarım Konuları

On iki faktörlü metodolojiden sağlanan kılavuzun ötesinde, dağıtılmış sistemler inşa ederken almanız gereken birkaç kritik tasarım kararı vardır.

*İletişim*

Ön uç istemci uygulamaları destekli uç temel hizmetlerle nasıl iletişim kurar? Doğrudan iletişime izin verecek misiniz? Veya, esneklik, denetim ve güvenlik sağlayan bir ağ geçidi cephesi ile arka uç hizmetleri özetleyebilir misiniz?

Arka uç çekirdek hizmetleri birbirleriyle nasıl iletişim kuracak? Bağlantı ve darbe performansı ve çeviklik yol doğrudan HTTP aramaları izin verir misiniz? Ya da sıra ve konu teknolojileri ile ayrılmış mesajlaşma düşünebilirsiniz?

İletişim ayrıntılı Bölüm 4, *Bulut-Yerli İletişim Desenleri ele alınmıştır.*

*Dayanıklılık*

Microservices mimarisi sisteminizi işlem sürecinden ağ iletişimine taşır. Dağıtılmış bir ortamda, Hizmet B Hizmet A'dan gelen bir çağrıya yanıt vermiyorsa ne yapacaksınız? Hizmet C geçici olarak kullanılamaz hale geldiğinde ve diğer hizmetler yığın ve sistem performansını düşürmek çağıran ne olur?

Esneklik ayrıntılı Bölüm 6, *Bulut-Yerli Esneklik*kaplıdır.

*Dağıtılmış Veriler*

Tasarım gereği, her microservice kendi verilerini kapsüller, kendi genel arayüzü üzerinden işlemleri açığa. Bu nedenle, verileri nasıl sorgularsınız veya birden çok hizmet arasında bir hareketi nasıl uygularsınız?

Dağıtılmış veriler ayrıntılı Bölüm 5, *Bulut-Yerel Veri Desenleri ele alınmıştır.*

*Kimlik*

Hizmetiniz, hizmete kimlerin eriştiyi ve hangi izinlere sahip olduklarını nasıl belirleyecek?

Kimlik ayrıntılı Bölüm 8, *Kimlik*kaplıdır.

## <a name="microservices"></a>Mikro hizmetler

Bulut-yerli sistemler, modern uygulamalar oluşturmak için popüler bir mimari stil olan mikro hizmetleri benimser.

Paylaşılan bir kumaş aracılığıyla etkileşim edebilen dağıtılmış küçük, bağımsız hizmetler kümesi olarak tasarlanan mikro hizmetler aşağıdaki özellikleri paylaşır:

- Her biri daha büyük bir etki alanı bağlamında belirli bir iş yeteneği uygular.

- Her biri bağımsız olarak geliştirilebilir.

- Her biri kendi veri depolama teknolojisini (SQL, NoSQL) ve programlama platformuna kapsülleme özelliğine sahiptir.

- Her biri kendi sürecinde çalışır ve HTTP/HTTPS, WebSockets veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)gibi standart iletişim protokollerini kullanarak başkalarıyla iletişim kurar.

- Bir uygulama oluşturmak için birlikte beste yaparlar.

Şekil 1-4, monolitik bir uygulama yaklaşımını mikrohizmet yaklaşımıyla karşılaştırmaktadır. Monolitin tek bir işlemde yürüten katmanlı bir mimariden nasıl oluştuğuna dikkat edin. Genellikle ilişkisel bir veritabanı tüketir. Ancak mikro hizmet yaklaşımı işlevselliği mantık ve veri içeren bağımsız hizmetlere ayırır. Her microservice kendi veri deposunu barındırar.

![Mikro hizmetlere karşı monolitik dağıtım](./media/monolithic-vs-microservices.png)

**Şekil 1-4.** Mikro hizmetlere karşı monolitik dağıtım

Mikro hizmetlerin, daha önce bölümde tartışılan [Twelve-Factor Uygulamasından](https://12factor.net/)"One Codebase, One Application" ilkesini nasıl tanıttıklarını not edin.

> *Faktör \#1, "Her microservice için kendi deposunda depolanan tek bir kod tabanı nı belirtir. Sürüm denetimi yle izlenirse, birden çok ortama dağıtılabilir."*

### <a name="why-microservices"></a>Neden mikro hizmetler?

Mikro hizmetler çeviklik sağlar.

Daha önce bölümde, biz mikro hizmetler ile bir monolit olarak inşa edilmiş bir e-ticaret uygulaması karşılaştırıldı. Örnekte, bazı açık faydalar gördük:

- Her microservice özerk bir yaşam döngüsüne sahiptir ve bağımsız olarak gelişebilir ve sık sık dağıtılabilir. Yeni bir özellik dağıtmak veya güncelleştirmek için üç aylık bir sürümü beklemeniz gerekmez. Karmaşık bir uygulamanın küçük bir alanını, tüm sistemi bozma riski daha az olan güncelleştirebilirsiniz.

- Her microservice bağımsız ölçeklendirilebilir. Tüm uygulamayı tek bir birim olarak ölçeklendirmek yerine, yalnızca daha fazla işlem gücü veya ağ bant genişliği gerektiren hizmetleri ölçeklendirin. Ölçeklendirmeye yönelik bu ince taneli yaklaşım, sisteminizin daha fazla denetimini sağlar ve sisteminizin her şeyi değil, bölümlerini ölçeklendirdiğiniz genel maliyetleri azaltmaya yardımcı olur.

Mikrohizmetleri anlamak için mükemmel bir referans kılavuzu [.NET Microservices: Containerized .NET Applications için Mimari.](https://docs.microsoft.com/dotnet/standard/microservices-architecture/) Kitap mikrohizmetler tasarım ve mimari içine derin dalışlar. Microsoft'tan ücretsiz olarak indirilebilen [tam destelik bir microservice referans mimarisinin](https://github.com/dotnet-architecture/eShopOnContainers) tamamlayıcısıdır.

### <a name="developing-microservices"></a>Mikro hizmetler geliştirme

Mikro hizmetler herhangi bir modern geliştirme platformu ile oluşturulabilir.

Microsoft .NET Core platformu mükemmel bir seçimdir. Ücretsiz ve açık kaynak kodlu, mikrohizmet geliştirmebasitleştirmek için birçok yerleşik özelliklere sahiptir. .NET Core çapraz platformdur. Uygulamalar Windows, macOS ve Linux'un çoğu tatları üzerinde oluşturulabilir ve çalıştırılabilir.

.NET Core son derece performanslı ve Node.js ve diğer rakip platformlara göre iyi bir puan almıştır. İlginçtir, [TechEmpower](https://www.techempower.com/) birçok web uygulama platformları ve [çerçeveleri](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) arasında performans kriterleri geniş bir dizi yürütülen. .NET Core ilk 10 içinde attı - node.js ve diğer rakip platformlar çok üzerinde.

.NET Core, Microsoft ve GitHub'daki .NET topluluğu tarafından korunmektedir.

## <a name="containers"></a>Kapsayıcılar

Günümüzde, *bulut yerli*ile ilgili herhangi bir konuşmada belirtilen terim *konteyner* duymak doğaldır. Kitapta, [Bulut Yerli Desenler](https://www.manning.com/books/cloud-native-patterns), yazar Cornelia Davis gözlemler, "Konteynerbulut yerli yazılım büyük bir etkinleştirici vardır." Cloud Native Computing Foundation, [bulut-yerel](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) yol haritasında ilk adım olarak mikrohizmet konteynerleştirmesini yerleştirir - işletmeler için bulut-yerel yolculuklarına başlayan rehberlik.

Bir microservice konteyner basit ve basittir. Kod, bağımlılıkları ve çalışma süresi [kapsayıcı görüntüsü](https://docs.docker.com/glossary/?term=image)olarak adlandırılan bir ikili içine paketlenir. Görüntüler, görüntüler için bir depo veya kitaplık görevi gören bir [kapsayıcı kayıt defterinde](https://caylent.com/container-registries/)depolanır. Kayıt defteri geliştirme bilgisayarınızda, veri merkezinizde veya genel bir bulutta bulunabilir. Docker kendisi [Docker Hub](https://hub.docker.com/)üzerinden bir kamu kayıt tutar. Azure bulutu, kapsayıcı görüntülerini çalıştıracak bulut uygulamalarına yakın depolamak için bir [kapsayıcı kayıt defterine](https://azure.microsoft.com/services/container-registry/) sahiptir.

Gerektiğinde, görüntüyü çalışan bir kapsayıcı örneğine dönüştürürsunuz. Örnek, [kapsayıcı çalışma zamanı](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) altyapısı yüklü olan herhangi bir bilgisayarda çalışır. Konteynerleştirilmiş hizmetin gerektiği kadar örneği olabilir.

Şekil 1-5, her biri kendi konteynerinde, tek bir ana bilgisayarda çalışan üç farklı mikro hizmeti gösterir.

![Konteyner ana bilgisayarda çalışan birden çok kapsayıcı](./media/hosting-mulitple-containers.png)

**Şekil 1-5**. Konteyner ana bilgisayarda çalışan birden çok kapsayıcı

Her kapsayıcının farklı olabilecek kendi bağımlılık kümesini ve çalışma süresini nasıl koruduğuna dikkat edin. Burada, Ürün microservice'in farklı sürümlerinin aynı ana bilgisayarda çalıştığını görüyoruz. Her kapsayıcı, temel ana bilgisayar işletim sisteminin, belleğin ve işlemcinin bir dilimini paylaşır, ancak birbirinden yalıtılmıştır.

Konteyner modelinin [On iki faktörlü uygulamadan](https://12factor.net/)"Bağımlılıklar" ilkesini ne kadar iyi benimsediklerine dikkat edin.

> *Faktör \#2, "Her mikro hizmet, tüm sistemi etkilemeden değişiklikleri kucaklayarak kendi bağımlılıklarını izole eder ve paketler."*

Kapsayıcılar hem Linux hem de Windows iş yüklerini destekler. Azure bulutu her ikisini de açıkça kucaklar. İlginçtir ki, Azure'un en popüler işletim sistemi haline gelen Windows Server değil Linux'dur.

Birkaç konteyner satıcıları varken, Docker pazarın aslan payını ele geçirdi. Şirket yazılım konteyner hareketi sürüş olmuştur. Bulut ayarı uygulamaları paketleme, dağıtma ve çalıştırma için fiili standart haline gelmiştir.

### <a name="why-containers"></a>Neden konteynerler?

Kapsayıcılar taşınabilirlik sağlar ve ortamlar arasında tutarlılığı garanti eder. Her şeyi tek bir pakete sığdırarak, mikro hizmeti ve bağımlılıklarını temel altyapıdan *yalıtabilirsiniz.*

Aynı kapsayıcıyı Docker çalışma zamanı motoruna sahip herhangi bir ortama dağıtabilirsiniz. Kapsayıcılaştırılmış iş yükleri, her ortamı çerçeveler, yazılım kitaplıkları ve çalışma zamanı motorları ile önceden yapılandırma giderini de ortadan kaldırır.

Temel işletim sistemi ve ana bilgisayar kaynaklarını paylaşarak, kapsayıcılar tam bir sanal makineden çok daha küçük bir ayak izine sahiptir. Daha küçük boyut, belirli bir ana bilgisayarda çalıştırılabilen mikro hizmetlerin *yoğunluğunu*veya sayısını artırır.

### <a name="container-orchestration"></a>Kapsayıcı düzenleme

Docker gibi araçlar görüntüler oluşturur ken ve kapsayıcıları çalıştırırken, bunları yönetmek için araçlara da ihtiyacınız vardır. Konteyner yönetimi, konteyner orkestratoradı adı verilen özel bir yazılım programı ile yapılır. Ölçekte çalışırken, konteyner orkestrasyonu esastır.

Şekil 1-6, konteyner orkestratörlerin sağladığı yönetim görevlerini gösterir.

![Konteyner orkestratörleri ne yapar?](./media/what-container-orchestrators-do.png)

**Şekil 1-6**. Konteyner orkestratörleri ne yapar?

Aşağıdaki tabloda ortak orkestrasyon görevleri açıklanmaktadır.

|  Görevler | Açıklama  |
| :-------- | :-------- |
| Zamanlama | Konteyner örneklerini otomatik olarak sağlama.|
| Yakınlık/anti-yakınlık | Yakın veya birbirinden uzak kapları sağlama, kullanılabilirlik ve performansa yardımcı olur. |
| Sistem durumunu izleme | Hataları otomatik olarak algılar ve düzeltin.|
| Yük devretme | Başarısız örneğini sağlıklı makinelere otomatik olarak yeniden sağlama.|
| Ölçeklendirme | Talebi karşılamak için kapsayıcı örneğini otomatik olarak ekleyin veya kaldırın.|
| Ağ | Kapsayıcı iletişimi için ağ kaplaması yönetin.|
| Hizmet Bulma | Kapsayıcıların birbirini bulmasını etkinleştirin.|
| Haddeleme Yükseltmeleri | Sıfır kapalı kalma süresi dağıtımıyla artımlı yükseltmeleri koordine edin. Sorunlu değişiklikleri otomatik olarak geri ala.r'a getirin.|

Orkestratörlerin, daha önce bölümde tartışılan [Twelve-Factor Uygulaması'ndaki](https://12factor.net/)tek kullanımlık ve eşzamanlılık ilkelerini nasıl benimsediklerine dikkat edin.

> *Faktör \#9, "Hizmet örnekleri tek kullanımlık olmalı, ölçeklenebilirlik fırsatlarını ve düzgün kapatmaları artırmak için hızlı başlatmaları tercih eder. Docker konteynerleri ve bir orkestratör doğal olarak bu gereksinimi karşılar."*

> *Faktör \#8, "Hizmetler, mevcut en güçlü makinede tek bir büyük örneği ölçeklendirmenin aksine çok sayıda küçük özdeş işlem (kopya) arasında ölçeklendirilir." belirtir.*

Çeşitli konteyner orkestratörleri mevcut olsa da, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) bulut-yerli dünya için fiili standart haline gelmiştir. Konteynerleştirilmiş iş yüklerini yönetmek için taşınabilir, genişletilebilir, açık kaynak kodlu bir platformdur.

Kendi Kubernetes örneğini barındırabilirsin, ama o zaman kaynaklarının sağlanması ve yönetilmesinden sorumlu olursun - ki bu karmaşık olabilir. Azure bulutu, Yönetilen bir hizmet olarak Kubernetes'i, [Azure Kubernetes Hizmetini (AKS)](https://azure.microsoft.com/services/kubernetes-service/)özellikleri. Yönetilen bir hizmet, yüklemek ve korumak zorunda kalmadan özelliklerini tam olarak uygulamanızı sağlar.

Azure Kubernetes Hizmetleri ayrıntılı Bölüm 2, *Ölçekleme Bulut-Yerel Uygulamalar*kaplıdır.

## <a name="backing-services"></a>Destek hizmetleri

Bulut tabanlı sistemler, veri depoları, ileti aracıları, izleme ve kimlik hizmetleri gibi birçok farklı yardımcı kaynağa bağlıdır. Bu hizmetler [destek hizmetleri](https://12factor.net/backing-services)olarak bilinir.

 Şekil 1-7, bulut ayarı sistemlerin intisaettiği birçok yaygın destek hizmeti gösterir.

![Ortak destek hizmetleri](./media/common-backing-services.png)

**Şekil 1-7**. Ortak destek hizmetleri

Destek hizmetleri [on iki faktör uygulamadan](https://12factor.net/)"Devletsizlik" ilkesini teşvik , bölümde daha önce tartışıldı.

>*Faktör \#6,* "Her microservice diğer çalışan hizmetlerden izole, kendi sürecinde yürütmek gerekir. Dağıtılmış önbellek veya veri deposu gibi bir destek hizmetiiçin gerekli durumu dışsallaştırma."

Kendi destek hizmetlerinizi barındırabilirsiniz, ancak o zaman bu kaynakların lisanslanmasından, sağlanmasından ve yönetiminden siz sorumlu olursunuz.

Bulut sağlayıcıları, yönetilen destek *hizmetlerinin* zengin bir ürün yelpazesine sunuyoruz. Hizmete sahip olmak yerine, yalnızca onu tüketirsiniz. Sağlayıcı kaynağı ölçekte çalışır ve performans, güvenlik ve bakım sorumluluğunu üstleniyor. İzleme, artıklık ve kullanılabilirlik hizmete dahil edilmiştir. Sağlayıcılar yönetilen hizmetlerini tam olarak destekler - bir bilet açın ve sorununuzu giderirler.

Bulut ait sistemler, bulut satıcılarının yönetilen destek hizmetlerini tercih ediyor. Zaman ve emek tasarrufu harika. Kendi barındırma ve sorun yaşıyor operasyonel risk pahalı hızlı alabilirsiniz.

En iyi yöntem, bir destek hizmetini harici bir yapılandırmada depolanan bilgilerle (URL ve kimlik bilgileri) dinamik olarak bir mikro hizmete bağlı *bağlı bağlı*bir kaynak olarak ele almaktır. Bu kılavuz, bölümde daha önce tartışılan [On iki faktörlü uygulamada](https://12factor.net/)hecelenmiştir.

>*Faktör \#4,* destek hizmetlerinin "adreslenebilir bir URL üzerinden ortaya kaldırılması gerektiğini" belirtir. Bunu yapmak, kaynağı uygulamadan ayırarak değiştirilebilir olmasını sağlar."

>*Faktör \#3,* "Yapılandırma bilgileri mikro hizmetin dışına taşınır ve kodun dışındaki bir yapılandırma yönetim aracı aracılığıyla dışsallaştırılır" olarak belirtir.

Bu desenle, kod değişikliği olmadan bir destek hizmeti eklenebilir ve ayrılabilir. Bir mikro hizmeti QA'dan evreleme ortamına yükseltebilirsiniz. Mikrohizmet yapılandırmasını evrelemedeki destek hizmetlerini işaret etmek için günceller ve ayarları bir ortam değişkeni aracılığıyla kapsayıcınıza enjekte edersiniz.

Bulut satıcıları, özel destek hizmetleriyle iletişim kurmanız için API'ler sağlar. Bu kütüphaneler sıhhi tesisatı ve karmaşıklığı kapsüller. Bu API'lerle doğrudan iletişim kurmak, kodunuzu destek hizmetiyle sıkı bir şekilde çifte bağlayacaktır. Satıcı API'sinin uygulama ayrıntılarını yalıtmak daha iyi bir uygulamadır. Genel işlemleri hizmet kodunuza teşhir ederek bir ara işlem katmanı veya ara API tanıtın. Bu gevşek bağlantı, bir destek hizmetini başka bir hizmetle değiştirmenize veya ana hat hizmet kodunda değişiklik yapmak zorunda kalmadan kodunuzu farklı bir genel buluta taşımanızı sağlar.

Destek hizmetleri ayrıntılı Bölüm 5, *Bulut-Yerel Veri Desenleri*ve Bölüm 4, *Bulut-Yerel İletişim Desenleri ele alınmıştır.*

## <a name="automation"></a>Otomasyon

Gördüğünüz gibi, bulut-yerli sistemler hız ve çeviklik elde etmek için mikro hizmetleri, konteynerleri ve modern sistem tasarımını benimser. Ama bu hikayenin sadece bir parçası. Bu sistemlerin çalıştırıldığı bulut ortamlarını nasıl sağlarsınız? Uygulama özelliklerini ve güncellemelerini nasıl hızla dağıtAbilirsiniz? Resmin tamamını nasıl tamamlarsın?

[Altyapının](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)yaygın olarak kabul edilen uygulamaını Kod veya IaC olarak girin.

IaC ile platform sağlama ve uygulama dağıtımını otomatikleştirebilirsiniz. Aslında DevOps uygulamaları için test ve sürüm gibi yazılım mühendisliği uygulamaları uygulayın. Altyapınız ve dağıtımlarınız otomatik, tutarlı ve yinelenebilir.

### <a name="automating-infrastructure"></a>Altyapıyı otomatikleştirmek

Azure [Kaynak Yöneticisi](https://azure.microsoft.com/documentation/articles/resource-group-overview/), Terraform ve [Azure CLI](https://docs.microsoft.com/cli/azure/)gibi araçlar, gereksinim duyduğunuz bulut altyapısını açıklayıcı bir şekilde komut dosyasına göre yazabilmenizi sağlar. Kaynak adları, konumları, kapasiteleri ve sırları parametreli ve dinamiktir. Komut dosyası sürülür ve projenizin bir artemi olarak kaynak denetimine denetlenir. Komut dosyasını, QA, evreleme ve üretim gibi sistem ortamları arasında tutarlı ve yinelenebilir bir altyapı sağlamak için çağırırsınız.

Kaputun altında, IaC idempotent, yan etkileri olmadan tekrar tekrar aynı komut dosyası çalıştırabilirsiniz anlamına gelir. Takımın bir değişiklik yapması gerekiyorsa, komut dosyasını ve yeniden çalıştırılır. Yalnızca güncelleştirilen kaynaklar etkilenir.

Makalede, [Kod olarak Altyapı nedir](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Yazar Sam Guckenheimer nasıl açıklar, "IaC uygulayan takımlar hızlı ve ölçekte istikrarlı ortamlar sunabilir. Takımlar ortamların el ile yapılandırmasını önler ve ortamlarının istenilen durumunu kod la temsil ederek tutarlılığı zorlar. IaC ile altyapı dağıtımları yinelenebilir ve yapılandırma kayması veya eksik bağımlılıklardan kaynaklanan çalışma zamanı sorunlarını önler. DevOps ekipleri, uygulamaları ve destekleyici altyapılarını hızlı, güvenilir ve ölçekte sunmak için birleştirilmiş bir uygulama ve araç seti ile birlikte çalışabilir."

### <a name="automating-deployments"></a>Dağıtımları otomatikleme

Daha önce tartışılan [On iki Faktörlü Uygulama,](https://12factor.net/)tamamlanmış kodu çalışan bir uygulamaya dönüştürürken ayrı adımlar için çağrıda bulunur.

> *Faktör \#5,* "Her sürüm, yapı, serbest bırakma ve çalıştırma aşamaları arasında katı bir ayrım uygulamalıdır. Her biri benzersiz bir kimlikle etiketlenmeli ve geri dönme yeteneğini desteklemelidir."

Modern CI/CD sistemleri bu ilkeyi gerçekleştirmeye yardımcı olur. Bunlar ayrı dağıtım adımları sağlar ve kullanıcılar tarafından kolayca kullanılabilen tutarlı ve kaliteli kodlar sağlamaya yardımcı olur.

Şekil 1-8 dağıtım işlemi arasında ayırma gösterir.

![CI/CD Pipeline'da Dağıtım Adımları](./media/build-release-run-pipeline.png)

**Şekil 1-8**. CI/CD Ardışık Alanda dağıtım adımları

Önceki şekilde, görevlerin ayrılmasına özel dikkat edin.

Geliştirici, kod, çalıştırma ve hata ayıklamanın "iç döngüsü" olarak adlandırılan aracılığıyla bir geliştirme ortamında bir özellik oluşturur. Tamamlandığında, bu kod GitHub, Azure DevOps veya BitBucket gibi bir kod deposuna *itilir.*

Itme, kodu ikili bir artifretiğe dönüştüren bir yapı aşamasını tetikler. Çalışma [sürekli entegrasyon (CI)](https://martinfowler.com/articles/continuousIntegration.html) boru hattı ile yürütülmaktadır. Uygulamayı otomatik olarak oluşturur, sınar ve paketler.

Sürüm aşaması ikili yapıyı alır, dış uygulama ve ortam yapılandırma bilgilerini uygular ve değişmez bir sürüm üretir. Sürüm belirli bir ortama dağıtılır. Çalışma [sürekli teslimat (CD)](https://martinfowler.com/bliki/ContinuousDelivery.html) boru hattı ile yürütülmaktadır. Her sürüm tanımlanabilir olmalıdır. "Bu dağıtım uygulamanın 2.1.1 sürümünde çalışıyor." diyebilirsiniz.

Son olarak, yayımlanan özellik hedef yürütme ortamında çalıştırılır. Sürümler, herhangi bir değişikliğin yeni bir sürüm oluşturması gerektiği anlamına gelir.

Bu uygulamaları uygulayan kuruluşlar, yazılım ları nasıl sevk ettiklerini kökden geliştirmiştir. Pek çoğu üç aylık sürümlerden isteğe bağlı güncelleştirmelere geçti. Amaç, sorunları geliştirme döngüsünün başlarında, düzeltilmesi daha ucuz olduğunda yakalamaktır. Entegrasyonlar arasındaki süre ne kadar uzun olursa, sorunların çözülmesi o kadar pahalı olur.  Tümleştirme sürecinde tutarlılık sayesinde, takımlar kod değişikliklerini daha sık gerçekleştirebilir ve bu da daha iyi işbirliği ve yazılım kalitesine yol açabilir.

### <a name="azure-pipelines"></a>Azure Pipelines

Azure bulutu, Şekil 1-9'da gösterilen [Azure DevOps](https://azure.microsoft.com/services/devops/) teklifinin bir parçası olan [Azure Boru Hatları](https://azure.microsoft.com/services/devops/pipelines/)adlı yeni bir CI/CD hizmetini içerir.

![DevOps'ta Azure Boru Hatları](./media/devops-components.png)

**Şekil 1-9**. Azure DevOps teklifleri

Azure Pipelines, sürekli tümleştirme (CI) ve sürekli teslimatı (CD) birleştiren bir bulut hizmetidir. Kodunuzu otomatik olarak test edebilir, oluşturabilir ve herhangi bir hedefe sevk edebilirsiniz.

Ardınız, uygulamanızın geri kalanıyla birlikte bir YAML dosyasında kod olarak boru hattınızı tanımlarsınız.

- Ardışık etki hattı kodunuzla birlikte sürülür ve aynı dallanma yapısını izler.
- Çekme isteklerinde ve şube oluşturma ilkelerinde kod incelemeleri yoluyla değişikliklerinizin doğrulanmasını elde elabilirsiniz.
- Kullandığınız her dal, azure-pipelines.yml dosyasını değiştirerek yapı ilkesini özelleştirebilir.
- Ardışık hatlar dosyası sürüm denetiminde denetlenir ve bir sorun olup olmadığı araştırılabilir.

Azure Pipelines hizmeti çoğu Git sağlayıcısını destekler ve Linux, macOS veya Windows platformlarında yazılmış uygulamalar için dağıtım ardışık lıkları oluşturabilir. Java, .NET, JavaScript, Python, PHP, Go, XCode ve C++ desteğini içerir.

>[!div class="step-by-step"]
>[Önceki](introduction.md)
>[Sonraki](candidate-apps.md)
