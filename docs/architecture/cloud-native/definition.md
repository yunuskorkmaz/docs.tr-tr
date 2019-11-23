---
title: Bulutta Yerel'i tanımlama
description: Bulutta yerel sistemler için yatak odası sağlayan temel sütunlar hakkında bilgi edinin
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 27191a67b2964ac2e1636a4d7dc55d5314b78439
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087540"
---
# <a name="defining-cloud-native"></a>Cloud Native 'i tanımlama

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Yaptığımız şeyi ve iş arkadaşlarınızın 10. kısmını durdurun. "Cloud native" terimini tanımlamanızı isteyin. Sekiz farklı yanıt elde etmenizde yarar vardır. Şimdiye kadar, bulutta yerel teknolojiler ve uygulamalar geliştikçe, bu nedenle bu aşamada altı ay sonra tanımları olur.

Cloud Native, önemli iş sistemlerini oluşturma hakkında düşündüğünüzden daha fazla değişiklik yaptığımız bir yöntemdir.

Bulutta yerel sistemler, hızlı değişim, büyük ölçek ve esnekliği için tasarlanmıştır.

Bulut Yerel Bilgi Işlem altyapısı resmi bir [tanım](https://github.com/cncf/foundation/blob/master/charter.md)sağlar:

> *Bulutta yerel teknolojiler, kuruluşların modern, genel, özel ve karma bulutlar gibi dinamik ortamlarda ölçeklenebilir uygulamalar oluşturup çalıştırmasına olanak sağlar. Kapsayıcılar, hizmet kafesleri, mikro hizmetler, sabit altyapı ve bildirim temelli API 'Ler bu yaklaşımı benimseme.*

> *Bu teknikler dayanıklı, yönetilebilir ve observable olan gevşek olarak bağlanmış sistemleri etkinleştirir. Güçlü otomasyon ile birlikte, mühendislerin yüksek düzeyde etkili değişiklikler yapmasına ve en az sayıda küçük bir şekilde öngörülere olanak tanır.*

Uygulamalar daha fazla ve daha fazla yoğun Kullanıcı tarafından daha fazla karmaşık hale gelmiştir. Kullanıcılar hızlı yanıt verme, yenilikçi özellikler ve sıfır kapalı kalma süresi bekler. Performans sorunları, yinelenen hatalar ve hızlı taşınmama artık kabul edilemez. Bunlar kolayca rakibe taşıyacağız.

Cloud Native, *hız* ve *çeviklik*hakkında çok daha fazla. İş sistemleri, iş yeteneklerini stratejik dönüşümlerle etkinleştirmeye, iş hızını hızlandırmanıza ve büyümeye kadar gelişmesini sağlar. Hemen pazara yönelik fikirler almak zorunludur.

Bu teknikleri uygulayan bazı şirketler aşağıda verilmiştir. Elde ettikleri hız, çeviklik ve ölçeklenebilirlik hakkında düşünün.

| Şirket | Deneyimleri |
| :-------- | :-------- |
| [Netflix](https://www.infoq.com/news/2013/06/netflix/) | Üretimde 600 ' dür ve hizmet vardır. Günde yüz kez dağıtır. |
| [Uber](https://eng.uber.com/micro-deploy/) | Üretimde 1000 + hizmet bulunur. Her hafta birkaç bin derleme dağıtır. |
| [WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf) | Üretimde 300 ' den fazla hizmet vardır. Günde neredeyse 1.000 değişiklik yapar. |

Gördüğünüz gibi, Netflix, Uber ve WeChat yüzlerce bağımsız mikro hizmetten oluşan sistemleri kullanıma sunar. Bu mimari stili, pazar koşullarına hızlı yanıt vermesini sağlar. Canlı, karmaşık bir uygulamanın küçük alanlarında anında güncelleştirebilir ve bu alanların gerektiği şekilde ölçeklendirilmesini sağlayabilirsiniz.

Cloud Native 'in hızı ve çevikliği, bir dizi faktörden daha fazla bilgi gelir. Foremost, bulut altyapısıdır. Şekil 1-3 ' de gösterilen ek temel sütunlar, bulutta yerel sistemler için yatak odası da sağlar.

![Bulutta yerel temel sütunlar](./media/cloud-native-foundational-pillars.png)

**Şekil 1-3**. Bulutta yerel temel sütunlar

Her bir birimin önemini daha iyi anlamak için biraz zaman atalım.

## <a name="the-cloud"></a>Bulut...

Bulut Yerel sistemleri, bulut hizmeti modelinin tam avantajlarından yararlanır.

Dinamik, sanallaştırılmış bir bulut ortamında Misyonumuz için tasarlanan bu sistemler, [hizmet olarak platform (PaaS)](https://azure.microsoft.com/overview/what-is-paas/) işlem altyapısı ve yönetilen hizmetler için kapsamlı bir kullanım sağlar. Temel altyapıyı dakikalar içinde *atılabilir* tarafından sağlanır ve yeniden boyutlandırılıp, ölçeklendirildiğinde veya isteğe bağlı olarak, Otomasyon aracılığıyla kabul edilir.

[Pets ve Cattle](https://medium.com/@Joachim8675309/devops-concepts-pets-vs-cattle-2380b5aab313)'ın yaygın olarak kabul edilen DevOps kavramını göz önünde bulundurun. Geleneksel bir veri merkezinde sunucular, anlamlı bir ad verilen bir fiziksel *makine olan ve*için kalan olarak değerlendirilir. Aynı makineye daha fazla kaynak ekleyerek ölçeklendirebilirsiniz (ölçeği büyütme). Sunucu hasta olursa, sistem durumuna geri dönebilirsiniz. Sunucu kullanılamaz hale gelirse herkes bildirimler.

*Cattle* hizmet modeli farklı. Her örneği bir sanal makine veya kapsayıcı olarak temin edersiniz. Bunlar aynıdır ve hizmet-01, hizmet-02 vb. gibi bir sistem tanımlayıcısı atanır. Daha fazlasını oluşturarak ölçeklendirebilirsiniz (ölçeği genişletme). Biri kullanılamaz duruma geldiğinde hiçbir zaman bildirim.

Cattle modeli, *sabit altyapıyı*kaþken. Sunucular onarılamamakta veya değiştirilmez. Bir hata olursa veya güncelleştirme gerektiriyorsa, bu yok edilir ve yeni bir tane sağlanır; hepsi Otomasyon aracılığıyla yapılır.

Bulut Yerel sistemleri, cattle hizmet modelini benimseyin. Bunlar, çalıştırıldıkları makinelerle ilgili olmayan şekilde, altyapının ölçeklendirilirken veya çıkarken çalışmaya devam eder.

Azure bulut platformu, otomatik ölçeklendirme, kendiliğinden düzeltme ve izleme özellikleri ile bu düzeyde esnek altyapıyı destekler.

## <a name="modern-design"></a>Modern tasarım

Bulutta yerel bir uygulamayı nasıl tasarlıyorsunuz? Mimariniz nasıl görünür? Hangi ilkelere, desenlere ve en iyi uygulamalara uydunuz? Hangi altyapı ve işlemsel sorunlar önemli olacaktır?

### <a name="the-twelve-factor-application"></a>On Iki öğeli uygulama

Bulut tabanlı uygulamalar oluşturmak için yaygın olarak kabul edilen bir metodolojide, [on Iki öğeli uygulama](https://12factor.net/)vardır. Geliştiricilerin modern bulut ortamları için iyileştirilmiş uygulamalar oluşturmak üzere izlediği bir ilkeler ve uygulamalar kümesini açıklar. Ortamlar ve bildirim temelli Otomasyon genelinde taşınabilirliği için özel dikkat edilmelidir.

Web tabanlı herhangi bir uygulama için geçerli olsa da birçok uygulama, buluta yerel uygulamalar oluşturmaya yönelik sağlam bir temel olarak kabul etmesidir. Bu kurallara göre oluşturulan sistemler hızla dağıtabilir ve ölçeklendirebilir ve Pazar değişikliklerine hızlı bir şekilde tepki vermek için özellikler ekleyebilir.

Aşağıdaki tablo, on Iki öğeli yöntemi vurgular:

|    |  faktörü | Açıklama  |
| :-------- | :-------- | :-------- |
| 1 | Kod tabanı | Her mikro hizmet için kendi deposunda depolanan tek bir kod tabanı. Sürüm denetimiyle izlenen, birden çok ortama (QA, hazırlama, üretim) dağıtılabilir. |
| 2 | Bağımlılıkları | Her mikro hizmet, sistemin tamamını etkilemeden değişiklikler yapmadan kendi bağımlılıklarını yalıtır ve paketler. |
| 3 | Yapılandırmalar  | Yapılandırma bilgileri, mikro hizmetten ve externalized kod dışında bir yapılandırma yönetim aracı aracılığıyla taşınır. Aynı dağıtım, doğru yapılandırma uygulanmış ortamlar arasında yayabilir.  |
| 4 | Hizmetleri yedekleme | Anormal kaynaklar (veri depoları, önbellekler, ileti aracıları) adreslenebilir bir URL aracılığıyla gösterilmelidir. Bunu yapmak, kaynağı uygulamadan ayırır ve bu sayede, bunu değiştirilebilir hale gelir.  |
| 5 | Oluşturma, yayınlama, çalıştırma | Her sürüm, derleme, yayın ve çalıştırma aşamaları genelinde katı ayrımı zorlaması gerekir. Her birinin benzersiz bir KIMLIKLE etiketlenmesi ve geri alma özelliğini desteklemesi gerekir. Modern CI/CD sistemleri bu ilkeyi karşılamanın sağlanmasına yardımcı olur. |
| 6 | İşlemler | Her mikro hizmet kendi sürecinde yürütülecektir ve çalışan diğer hizmetlerden yalıtılmalıdır. Externalize, dağıtılmış önbellek veya veri deposu gibi bir yedekleme hizmetine gerekli durumu sağlar. |
| 7 | Bağlantı noktası bağlama | Her mikro hizmet, kendi bağlantı noktasında kullanıma sunulan arabirimleri ve işlevleri ile birlikte bulunmalıdır. Bunun yapılması, diğer mikro hizmetlerden yalıtımı sağlar. |
| 8 | Eşzamanlılık | Hizmetler, en güçlü makinede bulunan tek bir büyük örneği ölçeklendirmenin aksine çok sayıda küçük özdeş işleme (kopya) arasında ölçeği genişleme. |
| 9 | Disposability | Hizmet örnekleri, sistem doğru bir durumda kalacak şekilde ölçeklenebilirlik fırsatlarını ve düzgün kapanmaların artırılmasını sağlamak için atılabilir, favoring hızlı başlatmalar olmalıdır. Doğal olarak bu gereksinimi karşılayan Docker kapsayıcıları ve bir Orchestrator ile birlikte. |
| 10 | Geliştirme ve üretim eşliği | Ortamları uygulama yaşam döngüsü genelinde mümkün olduğunca benzer şekilde tutun, maliyetli kısayollardan kaçının. Burada, kapsayıcıları benimseme, aynı yürütme ortamını yükselterek büyük ölçüde katkıda bulunabilir. |
| 11 | Günlüğe Kaydetme | Mikro hizmetler tarafından oluşturulan günlükleri olay akışları olarak değerlendirin. Bunları bir Olay Toplayıcısı ile işleyin ve verileri Azure Izleyici veya splunk gibi veri madenciliği/günlük yönetim araçlarına ve sonuçta uzun süreli arşivleme ' ye yayın. |
| 12 | Yönetici süreçler | Yönetim/Yönetim görevlerini tek bir işlem olarak çalıştırın. Görevler, bir rapor için veri temizleme ve çekme analizlerini içerebilir. Bu görevleri yürüten araçlar, üretim ortamından, ancak uygulamadan ayrı olarak çağrılmalıdır. |

Kitapta, [on Iki öğeli uygulamanın ötesinde](https://content.pivotal.io/blog/beyond-the-twelve-factor-app), ilk 12 faktörün (2011 ' de yazılmıştır) her biri Için Kevin Hoffman ayrıntılarına bakın. Ayrıca, kitap, günümüzün modern bulut uygulaması tasarımını yansıtan üç ek etken de sağlar.

|    |  Yeni faktör | Açıklama  |
| :-------- | :-------- | :-------- |
| 13 | Önce API | Her şeyi bir hizmet yapın. Kodunuzun bir ön uç istemci, ağ geçidi veya başka bir hizmet tarafından tüketildiğini varsayalım. |
| 14 | Telemetri | Bir iş istasyonunda, uygulamanız ve davranışı hakkında ayrıntılı görünürlük vardır. Bulutta yok. Tasarımınızın izleme, etki alanına özgü ve sağlık/sistem verileri koleksiyonunu içerdiğinden emin olun. |
| 15 | Kimlik doğrulama/yetkilendirme  | Baştan itibaren kimlik uygulayın. Genel bulutlarda bulunan [RBAC (rol tabanlı erişim denetimi)](https://docs.microsoft.com/azure/role-based-access-control/overview) özelliklerini göz önünde bulundurun.  |

Bu bölümde ve kitabın tamamında 12 ' nin birçoğuna başvuracağız.

### <a name="critical-design-considerations"></a>Kritik tasarım konuları

On iki öğeli metodolojide sunulan yönergelerin ötesinde, dağıtılmış sistemler oluştururken yapmanız gereken birkaç kritik tasarım kararı vardır.

*Kurulan*

Ön uç istemci uygulamaları, desteklenen son çekirdek hizmetleriyle nasıl iletişim kurar? Doğrudan iletişime izin vermek ister misiniz? Veya, arka uç hizmetlerini esneklik, denetim ve güvenlik sağlayan bir ağ geçidi ile soyutlıyor musunuz?

Arka uç Çekirdek Hizmetleri birbirleriyle nasıl iletişim kuracaktır? Bağlantısı yapılan ve performans ve çeviklik sağlayan doğrudan HTTP çağrılarına izin veriyor musunuz? Ya da kuyruk ve konu teknolojileri ile birlikte mesajlaşmayı düşünebileceğiniz bir durum var mı?

İletişim, ayrıntılı Bölüm 4, *bulutta yerel Iletişim desenlerinde*ele alınmıştır.

*Resiliency*

Mikro hizmetler mimarisi, sisteminizi işlemden işlemden ağ iletişimine taşıtan. Dağıtılmış bir ortamda, B hizmeti A hizmetinden bir çağrıya yanıt vermediğinde ne olur? Service C geçici olarak kullanılamaz duruma geldiğinde ve BT yığınını çağıran ve sistem performansını azaldıkça ne olur?

Esneklik Bölüm 6, *bulutta yerel dayanıklılık*kapsamında ele alınmıştır.

*Dağıtılmış veriler*

Tasarıma göre, her mikro hizmet kendi verilerini kapsüller ve bu işlem ortak arabirimi aracılığıyla işlemleri ortaya çıkarlar. Bu durumda, verileri nasıl sorgulayabilir veya birden çok hizmet arasında bir işlem nasıl uygulayabilirim?

Dağıtılmış veriler ayrıntı bölümü 5, *bulutta yerel veri desenleri*kapsamında ele alınmıştır.

*Kimlik*

Hizmetinize kimin eriştiğini ve sahip oldukları izinleri nasıl tanımlayacaksınız?

Kimlik, ayrıntı Bölüm 8, *kimlik*kapsamında ele alınmıştır.

## <a name="microservices"></a>Mikro hizmetler

Modern uygulamalar oluşturmak için popüler bir mimari stili olan bulut Yerel sistemleri, mikro hizmetler 'i ördir.

Paylaşılan bir yapı aracılığıyla etkileşen, bir dağıtılmış küçük ve bağımsız hizmetler olarak oluşturulan mikro hizmetler aşağıdaki özellikleri paylaşır:

- Her biri daha büyük bir etki alanı bağlamı içinde belirli bir iş yeteneği uygular.

- Her biri olarak çalışabilen geliştirilmiştir ve bağımsız olarak dağıtılabilir.

- Her biri kendi veri depolama teknolojisini (SQL, NoSQL) ve programlama platformunu kapsülleyerek içerir.

- Her biri kendi sürecinde çalışır ve HTTP/HTTPS, WebSockets veya [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)gibi standart iletişim protokollerini kullanarak başkalarıyla iletişim kurar.

- Bir uygulama oluşturmak için bir araya alırlar.

Şekil 1-4, mikro hizmetler yaklaşımına sahip tek parçalı bir uygulama yaklaşımını karşıttır. Tek bir işlemde yürütülen bir katmanlı mimariden tek tek nasıl oluştuğunu aklınızda yapın. Genellikle ilişkisel bir veritabanını kullanır. Ancak mikro hizmet yaklaşımı, işlevleri Logic ve verileri içeren bağımsız hizmetlere ayırır. Her mikro hizmet kendi veri deposunu barındırır.

![Tek parçalı dağıtım ve mikro hizmetler karşılaştırması](./media/monolithic-vs-microservices.png)

**Şekil 1-4.** Tek parçalı dağıtım ve mikro hizmetler karşılaştırması

Mikro hizmetlerin "bir kod temeli, bir uygulama" ilkesini, daha önce bölümünde açıklanan [on Iki öğeli uygulamadan](https://12factor.net/)nasıl yükseltileceğini aklınızda edin.

> *Faktör \#1, kendi deposunda depolanan her bir mikro hizmet için tek bir kod temeli belirler. Sürüm denetimiyle izlenen, birden çok ortama dağıtabilir. "*

### <a name="why-microservices"></a>Mikro hizmetlerdeki neden?

Mikro hizmetler çeviklik sağlar.

Bu bölümde daha önce, mikro hizmetler ile tek bir şekilde oluşturulmuş bir eticaret uygulamasını karşılaştırdık. Örnekte, bazı açık avantajlar gördük:

- Her mikro hizmetin bir özerk yaşam döngüsü vardır ve bu, bağımsız olarak geliştirebilir ve sık sık dağıtabilir. Yeni bir özellik veya güncelleştirme dağıtmak için üç ayda bir sürüm beklemeniz gerekmez. Karmaşık bir uygulamanın küçük bir alanını, tüm sistemi kesintiye uğratmadan daha az riske sahip bir şekilde güncelleştirebilirsiniz.

- Her mikro hizmet bağımsız olarak ölçeklendirilebilen. Tüm uygulamanın tek bir birim olarak ölçeklendirilmesi yerine, yalnızca daha fazla işlem gücü veya ağ bant genişliği gerektiren hizmetleri ölçeklendirebilirsiniz. Ölçeklendirmeye yönelik bu ayrıntılı yaklaşım sisteminizin daha fazla denetimini sağlar ve sisteminizin bölümlerini ölçeklendirirken, her şeyi değil, genel maliyetleri azaltmaya yardımcı olur.

Mikro hizmetleri anlamak için harika bir başvuru kılavuzu [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](https://docs.microsoft.com/dotnet/standard/microservices-architecture/). Book derin, mikro hizmetler tasarımı ve mimarisine sahiptir. Microsoft 'tan ücretsiz bir indirme olarak sunulan [tam yığın mikro hizmet başvuru mimarisi](https://github.com/dotnet-architecture/eShopOnContainers) için bir yardımcı olur.

### <a name="developing-microservices"></a>Mikro hizmetler geliştirme

Mikro hizmetler, herhangi bir modern geliştirme platformunda oluşturulabilir.

Microsoft .NET Core platformu harika bir seçimdir. Ücretsiz ve açık kaynak olmak üzere, mikro hizmet geliştirmeyi basitleştirmek için birçok yerleşik özelliği vardır. .NET Core platformlar arası bir platformdur. Uygulamalar Windows, macOS ve Linux 'un birçok özellikleri üzerinde oluşturulabilir ve çalıştırılabilir.

.NET Core yüksek performans düzeyine sahiptir ve Node. js ve diğer rekabet platformları karşılaştırmayla iyi bir şekilde puanlanır. Interest, [Techempower](https://www.techempower.com/) birçok Web uygulaması platformu ve çerçevesinde çok sayıda [performans karşılaştırmalı olarak kıyaslamalarından](https://www.techempower.com/benchmarks/#section=data-r17&hw=ph&test=plaintext) oluşur. .NET Core, Node. js ve diğer rekabet platformları üzerinde en iyi 10 ' un üzerinde puanlanır.

.NET Core, GitHub 'da Microsoft ve .NET Community tarafından korunur.

## <a name="containers"></a>Kapsayıcılar

Günümüzde, *bulut Native*ile ilgili herhangi bir konuşmada bahsedilen terim *kapsayıcısını* dinlemek doğal bir terimdir. Bu kitapta, [bulutta yerel desenler](https://www.manning.com/books/cloud-native-patterns), yazar Cornelia Davis, "kapsayıcı, bulutta yerel yazılımın harika bir etkinleştiricisidir." Cloud Native Bilgi Işlem altyapısı, mikro hizmet kapsayıcılarını, bulut Yerel ız yolculuğuna başlayan kuruluşlar için kendi [bulut Yerel izleme](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) kılavuzlarındaki ilk adım olarak koyar.

Mikro hizmeti kapsayıcı basit ve basittir. Kod, bağımlılıkları ve çalışma zamanı, [kapsayıcı görüntüsü](https://docs.docker.com/glossary/?term=image)adlı bir ikiliye paketlenmiştir. Görüntüler, görüntüler için bir depo veya kitaplık görevi gören bir [kapsayıcı kayıt defterinde](https://caylent.com/container-registries/)saklanır. Kayıt defteri, geliştirme bilgisayarınızda, veri merkezinizde veya genel bir bulutta bulunabilir. Docker, [Docker Hub](https://hub.docker.com/)aracılığıyla ortak bir kayıt defteri tutar. Azure bulutu, kapsayıcı görüntülerinin depolandığı bir [kapsayıcı kayıt defterinin](https://azure.microsoft.com/services/container-registry/) özelliklerini çalıştıracak bulut uygulamalarına yakın bir şekilde depolar.

Gerektiğinde, görüntüyü çalışan bir kapsayıcı örneğine dönüştürürler. Örnek, [kapsayıcı çalışma zamanı](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) altyapısı yüklü olan herhangi bir bilgisayarda çalışır. Kapsayıcı hizmeti için gereken birçok örneğe sahip olabilirsiniz.

Şekil 1-5, her biri kendi kapsayıcısında tek bir konakta çalışan üç farklı mikro hizmeti gösterir.

![Kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı](./media/hosting-mulitple-containers.png)

**Şekil 1-5**. Kapsayıcı ana bilgisayarında çalışan birden çok kapsayıcı

Her kapsayıcının kendi bağımlılık ve çalışma zamanı kümesini nasıl koruduğu ve bu farklılık fark edebilirsiniz. Burada, ürün mikro hizmetinin aynı konakta çalışan farklı sürümlerini görüyoruz. Her kapsayıcı, temel ana bilgisayar işletim sisteminin, belleğin ve işlemcinin bir dilimini paylaşır, ancak bir diğerinden yalıtılır.

Kapsayıcı modelinin, [on Iki öğeli uygulamadan](https://12factor.net/)"bağımlılıklar" ilkesini ne kadar iyi kapsayıyacağını göz önünde ayırın.

> *Faktör \#2, "her mikro hizmet kendi bağımlılıklarını yalıtır ve paketler, tüm sistemi etkilemeden değişiklikleri benimsemesini belirtir."*

Kapsayıcılar hem Linux hem de Windows iş yüklerini destekler. Azure bulutu her ikisi de birlikte yer açar. Bu, Azure 'da en popüler işletim sistemi haline gelen Windows Server değil, bu Linux.

Çeşitli kapsayıcı satıcıları mevcut olsa da Docker, Market 'in payını yakalamaktadır. Şirket, yazılım kapsayıcısı hareketini yönlendirmiştir. Bulut Yerel uygulamalarının paketlenmesi, dağıtımı ve çalıştırılması için de standart haline gelmiştir.

### <a name="why-containers"></a>Neden kapsayıcılar?

Kapsayıcılar, ortamlar genelinde taşınabilirlik ve tutarlılık sağlar. Her şeyi tek bir pakette kapsülleyerek mikro hizmeti ve onun bağımlılıklarını temeldeki altyapıdan *yalıtabilirsiniz* .

Aynı kapsayıcıyı Docker Runtime altyapısına sahip herhangi bir ortamda dağıtabilirsiniz. Kapsayıcılı iş yükleri, her ortamı çerçeveler, yazılım kitaplıkları ve çalışma zamanı altyapılarıyla önceden yapılandırma masrafına de ortadan kaldırır.

Temel işletim sistemi ve konak kaynaklarını paylaşarak, kapsayıcıların tam bir sanal makineden çok daha küçük bir parmak izine sahip olması gerekir. Daha küçük boyut, belirli bir konağın aynı anda çalıştırılabir şekilde *yoğunluğu*veya mikro hizmet sayısını artırır.

### <a name="container-orchestration"></a>Kapsayıcı düzenlemesi

Docker görüntüleri oluşturma ve kapsayıcıları çalıştırma gibi araçlar da bunları yönetmek için araçlara ihtiyacınız vardır. Kapsayıcı yönetimi, kapsayıcı Orchestrator adlı özel bir yazılım programıyla yapılır. Ölçek üzerinde çalışırken, kapsayıcı düzenlemesi gereklidir.

Şekil 1-6 kapsayıcı düzenleyicilerinin sağladığı yönetim görevlerini gösterir.

![Kapsayıcı yöneticileri](./media/what-container-orchestrators-do.png)

**Şekil 1-6**. Kapsayıcı yöneticileri

Aşağıdaki tabloda, yaygın düzenleme görevleri açıklanmaktadır.

|  Görevler | Açıklama  |
| :-------- | :-------- |
| Planlama | Kapsayıcı örneklerini otomatik olarak sağlayın.|
| Benzeşim/benzeşim önleme | Kullanılabilirlik ve performansa yardımcı olmak için, birbirleriyle yakın veya uzak kapsayıcıları sağlayın. |
| Sistem durumu izleme | Sorunları otomatik olarak algıla ve düzelt.|
| Yük devretme | Başarısız örneği sağlıklı makinelere otomatik olarak yeniden sağlayın.|
| Ölçeklendirme | Talebi karşılamak için kapsayıcı örneğini otomatik olarak ekleyin veya kaldırın.|
| Ağ Oluşturma | Kapsayıcı iletişimi için bir ağ kaplamasını yönetin.|
| Hizmet bulma | Kapsayıcıları, birbirini bulacak şekilde etkinleştirin.|
| Çalışırken yükseltmeler | Sıfır kesinti dağıtımıyla artımlı yükseltmeleri koordine edin. Sorunlu değişiklikleri otomatik olarak geri alma.|

Düzenleyen 'in elden atılan ve eşzamanlılık ilkelerini, daha önce bölümünde tartışılan [on Iki öğeli uygulamadan](https://12factor.net/)nasıl anlayacağını aklınızda edin.

> *Faktör \#9 "hizmet örneklerinin atılabilir olması gerektiğini belirtir, ölçeklenebilirlik fırsatlarını artırmak için hızlı başlatmalar favoring ve sistemi doğru bir durumda bırakmak için düzgün kapatmalar. Doğal olarak bu gereksinimi karşılayan Docker kapsayıcıları ve bir Orchestrator ile birlikte. "*

> *Faktör \#8, "hizmetlerin çok sayıda küçük özdeş işleme (kopya) arasında ölçeğini, en güçlü makinede bulunan tek bir büyük örneği ölçeklendirmenin aksine belirtir."*

Birçok kapsayıcı grubu mevcut olsa da, [Kubernetes](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/) , bulutta yerel dünya için de standart hale geldi. Kapsayıcılı iş yüklerini yönetmek için taşınabilir, genişletilebilir ve açık kaynaklı bir platformdur.

Kendi Kubernetes örneğinizi barındırabilmeniz, ancak kaynaklarını sağlamaktan ve yönetmekten siz sorumlusunuz ve bu karmaşık olabilir. Azure bulut özellikleri, Azure [Kubernetes hizmeti (AKS)](https://azure.microsoft.com/services/kubernetes-service/)ile yönetilen bir hizmet olarak Kubernetes. Yönetilen bir hizmet, özelliklerini yüklemenize ve sürdürmenize gerek kalmadan özelliklerinden tamamen yararlanmanızı sağlar.

Azure Kubernetes Hizmetleri ayrıntılı Bölüm 2 ' de ele alınmıştır, *bulutta yerel uygulamaları ölçeklendirin*.

## <a name="backing-services"></a>Hizmetleri yedekleme

Bulutta yerel sistemler, veri depoları, ileti aracıları, izleme ve kimlik hizmetleri gibi birçok farklı yardımcı kaynağa bağlıdır. Bu hizmetler, [yedekleme hizmetleri](https://12factor.net/backing-services)olarak bilinir.

 Şekil 1-7, bulutta yerel sistemlerin kullandığı birçok ortak yedekleme hizmetini gösterir.

![Ortak destek hizmetleri](./media/common-backing-services.png)

**Şekil 1-7**. Ortak destek hizmetleri

Yedekleme Hizmetleri, "Statelesstik" ilkesini, bu bölümde daha önce açıklanan [on Iki öğeli uygulamadan](https://12factor.net/)yükseltir.

>*\#6 faktörü* , "her mikro hizmetin kendi sürecinde yürütülmesi gerektiğini, çalışan diğer hizmetlerden yalıtılmış olduğunu belirtir. Externalize, dağıtılmış önbellek veya veri deposu gibi bir yedekleme hizmetine gerekli durumu. "

Kendi destek hizmetlerinizi barındırabilmeniz, ancak bu kaynakları lisanslamayı, sağlamaktan ve yönetmekten siz sorumlusunuz.

Bulut sağlayıcıları, *yönetilen destek hizmetleri* için zengin bir sınıflama sunar. Hizmete sahip olmak yerine, yalnızca onu kullanabilirsiniz. Sağlayıcı, kaynağı ölçeklendirerek çalışır ve performans, güvenlik ve bakım sorumluluğunu üstlenir. İzleme, yedeklilik ve kullanılabilirlik, hizmette yerleşik olarak bulunur. Sağlayıcılar yönetilen hizmetlerini tamamen destekler-bir bilet açın ve sorununuzu düzeltir.

Bulutta yerel sistemler, yönetilen destek hizmetlerini bulut satıcılarından tercih etmek için. Zaman ve işçilik tasarrufları harika. Kendi kendinize ve sorun yaşamaya yönelik işlemsel risk pahalı bir hızlı olabilir.

Bir yedekleme hizmetini, bir dış yapılandırmada depolanan bilgiler (URL ve kimlik bilgileri) ile bir mikro hizmete dinamik olarak bağlı bir *kaynak*olarak değerlendirmek en iyi uygulamadır. Bu kılavuz, bölümünde daha önce açıklanan [on Iki öğeli uygulamada](https://12factor.net/)yer alınmıştır.

>*\#4 faktörü* , "BIR adreslenebilir URL aracılığıyla" yedekleme hizmetleri 'nin sunulduğunu belirtir. Bunu yapmak, kaynağı uygulamadan ayırır ve bu sayede, bunu değiştirilebilir olarak etkinleştirir. "

>*Faktör \#3* "yapılandırma bilgilerinin, kod dışında bir yapılandırma yönetim aracı aracılığıyla mikro hizmetten ve externalized dışına taşındığını belirtir."

Bu düzende, bir yedekleme hizmeti kod değişikliği yapılmadan iliştirilebilir ve ayrılabilir. Bir mikro hizmeti QA 'den hazırlama ortamına yükseltebilirsiniz. Mikro hizmet yapılandırmasını, hazırlama ' daki yedekleme hizmetlerini işaret etmek ve bir ortam değişkeni aracılığıyla kapsayıcınıza eklemek için güncelleştirin.

Bulut satıcıları, kendi özel destek hizmetleriyle iletişim kurması için API 'Ler sağlar. Bu kitaplıklar, sıhhi tesisat ve karmaşıklığı kapsüller. Doğrudan bu API 'lerle iletişim kurmak, kodunuzu Yedekleme hizmetine sıkı bir şekilde ister. Bu, satıcı API 'sinin uygulama ayrıntılarını tahmin etmek için daha iyi bir uygulamadır. Hizmet kodunuza genel işlemleri ortaya çıkaran bir intermediation katmanını veya ara API 'yi tanıtın. Bu gevşek bir geçiş, bir yedekleme hizmetini başka bir şekilde takabilmenizi veya ana hat hizmet kodunda değişiklik yapmanıza gerek kalmadan kodunuzu farklı bir genel buluta taşımanızı sağlar.

Yedekleme Hizmetleri, ayrıntılı Bölüm 5, *bulutta yerel veri desenleri*ve Bölüm 4, *bulutta yerel iletişim desenlerinde*ele alınmıştır.

## <a name="automation"></a>Otomasyon

Gördüğünüz gibi, bulut Yerel sistemleri, hızlı ve çeviklik sağlamak için mikro hizmetleri, kapsayıcıları ve modern sistem tasarımını imine dönüştürür. Ancak bu yalnızca hikayenin bir parçasıdır. Bu sistemlerin üzerinde çalıştığı bulut ortamlarını nasıl sağlayacaksınız? Uygulama özelliklerini ve güncelleştirmelerini hızlı bir şekilde nasıl dağıtırsınız? Tam resmi nasıl yuvarlıyorsunuz?

[Altyapı olarak, kod olarak](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)kabul edilen yaygın olarak kullanılan uygulama veya IAC girin.

IAC ile platform sağlamayı ve uygulama dağıtımını otomatikleştirin. Aslında DevOps uygulamalarınıza test ve sürüm oluşturma gibi yazılım mühendisliği uygulamalarını uygularsınız. Altyapınız ve dağıtımlarınız otomatik, tutarlı ve yinelenebilir.

### <a name="automating-infrastructure"></a>Altyapıyı otomatikleştirme

[Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/), teraform ve [Azure CLI](https://docs.microsoft.com/cli/azure/)gibi araçlar, ihtiyacınız olan bulut altyapısını bildirimli olarak betiğe olanak sağlar. Kaynak adları, konumlar, kapasiteler ve gizlilikler parametreleştirilenir ve dinamik. Betik sürümlenmiş ve projenizin yapıtı olarak kaynak denetimine iade edildi. Sistem ortamlarında QA, hazırlık ve üretim gibi tutarlı ve yinelenebilir bir altyapı sağlamak için betiği çağırılır.

IAC, ıdempotent ' dir. Bu, yan etkileri olmadan aynı betiği çalıştırabilmeniz anlamına gelir. Ekibin bir değişiklik yapması gerekiyorsa betiği düzenleyip yeniden çalıştırır. Yalnızca güncelleştirilmiş kaynaklar etkilenir.

Makalesinde [kod olarak altyapı nedir](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Sam Guckenheimer yazar, "IAC 'Yı uygulayan ekipler, kararlı ortamları hızla ve ölçekte teslim edebilir. Takımlar ortamların el ile yapılandırılmasını önler ve ortamları kod aracılığıyla istenen durumunu temsil ederek tutarlılığı zorlar. IAC ile altyapı dağıtımları tekrarlanabilir ve yapılandırma DRIP veya eksik bağımlılıklara neden olan çalışma zamanı sorunlarını önler. DevOps ekipleri, uygulamaları ve destekleyici altyapıyı hızlı, güvenilir ve ölçeklenebilir bir şekilde sunmak için birleştirilmiş bir uygulama ve araç kümesiyle birlikte çalışabilir. "

### <a name="automating-deployments"></a>Dağıtımları otomatikleştirme

Daha önce bahsedilen [on Iki öğeli uygulama](https://12factor.net/), tamamlanan kodu çalışan bir uygulamaya dönüştürürken ayrı adımlar çağırır.

> *Faktör \#5* , "her sürümün derleme, yayın ve çalıştırma aşamaları genelinde katı ayrımı zorunlu kılacak olduğunu belirtir. Her birinin benzersiz bir KIMLIKLE etiketlenmesi ve geri alma özelliğini desteklemesi gerekir. "

Modern CI/CD sistemleri bu ilkeyi karşılamanın sağlanmasına yardımcı olur. Bunlar ayrı dağıtım adımları sağlar ve kullanıcılar için hazır olan tutarlı ve kalite kodu sağlanmasına yardımcı olur.

Şekil 1-8, dağıtım işlemi genelinde ayrımı gösterir.

![CI/CD ardışık düzeninde dağıtım adımları](./media/build-release-run-pipeline.png)

**Şekil 1-8**. CI/CD ardışık düzeninde dağıtım adımları

Önceki şekilde, görevlerin ayrılmasındaki özel bir dikkat ödeyin.

Geliştirici geliştirme ortamlarında bir özellik oluşturur, kod, çalıştırma ve hata ayıklama "iç döngüsü" olarak adlandırılır. İşlem tamamlandığında, bu kod GitHub, Azure DevOps veya BitBucket gibi bir kod deposuna *gönderilir* .

Gönderim, kodu ikili yapıtlara dönüştüren bir derleme aşamasını tetikler. İş bir [sürekli tümleştirme (CI)](https://martinfowler.com/articles/continuousIntegration.html) işlem hattı ile uygulanır. Uygulamayı otomatik olarak oluşturur, sınar ve paketler.

Yayın aşaması ikili yapıtı seçer, dış uygulama ve ortam yapılandırma bilgilerini uygular ve sabit bir yayın oluşturur. Yayın belirtilen bir ortama dağıtılır. İş, [sürekli teslim (CD)](https://martinfowler.com/bliki/ContinuousDelivery.html) işlem hattı ile uygulanır. Her sürüm tanımlanabilir olmalıdır. "Bu dağıtım, uygulamanın Release 2.1.1 çalıştırıyor" diyebilirsiniz.

Son olarak, yayınlanan özellik hedef yürütme ortamında çalıştırılır. Yayınlar, herhangi bir değişikliğin yeni bir yayın oluşturması gereken anlamına gelir.

Bu uygulamalar uygulandığında kuruluşlar yazılımın nasıl sevk ettikleri konusunda önemli ölçüde gelişmiştir. Çoğu üç aylık sürümlerden isteğe bağlı güncelleştirmelere taşınmıştır. Amaç, düzeltilmesi daha ucuz olan sorunları geliştirme döngüsünün başlarında yakalar. Tümleştirmeler arasındaki süre arttıkça, daha pahalı olan sorunlar çözülmekte hale gelir.  Tümleştirme sürecinde tutarlılık sayesinde takımlar, kod değişikliklerini daha sık işleyebilir, daha iyi işbirliği ve yazılım kalitesine göre önde olur.

### <a name="azure-pipelines"></a>Azure işlem hatları

Azure bulutu, Şekil 1-9 ' de gösterilen [Azure DevOps](https://azure.microsoft.com/services/devops/) teklifi 'nin bir parçası olan [Azure Pipelines](https://azure.microsoft.com/services/devops/pipelines/)adlı yenı bir CI/CD hizmeti içerir.

![DevOps 'da Azure Pipelines](./media/devops-components.png)

**Şekil 1-9**. Azure DevOps teklifleri

Azure Pipelines, sürekli tümleştirme (CI) ve sürekli teslimi (CD) birleştiren bir bulut hizmetidir. Kodunuzu otomatik olarak test edebilir, oluşturabilir ve herhangi bir hedefe gönderebilirsiniz.

İşlem hattınızı, uygulamanız için kodun geri kalanı ile birlikte bir YAML dosyasında tanımlarsınız.

- İşlem hattı, kodunuzla birlikte sürümlüdür ve aynı dallanma yapısına uyar.
- Çekme isteklerindeki ve dal derleme ilkelerindeki kod İncelemeleri aracılığıyla değişikliklerinizin doğrulanmasını alırsınız.
- Kullandığınız her dal, Azure-Pipelines. yıml dosyasını değiştirerek yapı ilkesini özelleştirebilir.
- İşlem hattı dosyası sürüm denetimine denetlenir ve bir sorun varsa araştırılır.

Azure Pipelines hizmeti, çoğu git sağlayıcısını destekler ve Linux, macOS veya Windows platformlarında yazılan uygulamalar için dağıtım işlem hatları oluşturabilir. Java, .NET, JavaScript, Python, PHP, Go, XCode ve C++için destek içerir.

>[!div class="step-by-step"]
>[Önceki](introduction.md)
>[İleri](candidate-apps.md)
