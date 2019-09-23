---
title: Cloud Native DevOps
description: Azure için Cloud Native .NET uygulamaları tasarlama | Cloud Native DevOps
ms.date: 06/30/2019
ms.openlocfilehash: a056da833d7c6da11ab956337b77deab5e9bd159
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183191"
---
# <a name="cloud-native-devops"></a>Cloud Native DevOps

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Yazılım danışmanlarına yönelik sık kullanılan mantradır, ortaya çıkar. Yazılım danışmanları bir konum olmadığı için bu değildir. Bunun nedeni, yazılımdaki sorulara hiç bir doğru yanıt olmaması nedeniyle oluşur. Mutlak doğru ve yanlış yoktur, ancak Opposites arasında bir denge vardır.

Web uygulamaları geliştirmesinin iki ana okulu gibi gerçekleştirin: Tek sayfalı uygulamalar (maça 'Lar) sunucu tarafı uygulamalara karşı. Tek bir yandan, Kullanıcı deneyimi, maça ile daha iyi bir şekilde eğilimlidir ve Web sunucusuna giden trafik miktarı en aza indirilmesine olanak tanır ve bunları statik barındırma olarak basit bir şekilde barındırabilirsiniz. Diğer yandan, maça geliştirme ve test etme konusunda daha zor olmaya zorlar. Doğru seçim hangisi? Ayrıca, durumunuza bağlıdır.

Bulutta yerel uygulamalar aynı dichotomy öğesine etkilenmez. Geliştirme, kararlılık ve ölçeklenebilirlik hızı açısından açık avantajlar vardır ancak bunları yönetmek oldukça zor olabilir.

Yıl önce, bir uygulamayı geliştirmede bir ay veya daha fazlasını yapmak için geliştirme sürecinden üretime taşıma sürecinde yaygın olmayan bir durumdur. Şirketler 6 ayda, hatta her yıl temposunda için yazılım yayımlamıştır. Windows 10 ' un hiç yeşil günden önce kabul edilebilir olan yayınların temposunda için bir fikir almak üzere Microsoft Windows 'dan başka bir bakması gerekir. Windows XP ve Vista arasında geçen beş yıl, Vista ve Windows 7 arasında daha fazla 3.

Bu aşamada, yazılımı hızlı bir şekilde kullanıma sunabilmeniz oldukça iyi bir şekilde, daha fazla slotaya benzer rakipler üzerinden çok büyük bir pazar avantajı sunuyor. Bu nedenle, Windows 10 ' un önemli güncelleştirmelerinin hemen her altı ayda bir olması neden olur.

Daha hızlı ve iş için değer sunmaya yönelik daha güvenilir yayınları etkinleştiren desenler ve uygulamalar, her topluca DevOps olarak bilinir. Tüm yazılım geliştirme yaşam döngüsünün, uygulamayı sunmak ve çalıştırmak için bir uygulama belirtmekten oluşan çok çeşitli fikirler içerirler.

DevOps, mikro hizmetlerden önce ortaya çıktı ve büyük olasılıkla daha küçük bir hareket haline gelir, ancak üretim aşamasındaki çok sayıda uygulama daha kolay hale getirmek ve çalıştırmak için DevOps 'a daha fazla uyum sağlamaktır. 

![Şekil 11-0 arama eğilimleri, mikro hizmetlerdeki büyümenin, DevOps oldukça iyi bir fikir olana kadar başlamadığını gösterir.](./media/microservices-vs-devops.png)

İyi DevOps uygulamaları sayesinde, uygulamaları gerçekten test eden bir dağ 'ın altında yeterli olara sahip olmayan bulut Yerel uygulamalarının avantajlarından yararlanmak mümkündür.

DevOps 'a geldiğinde altın bir hayosız yoktur. Hiç kimse, yüksek kaliteli uygulamaları serbest bırakmak ve çalıştırmak için tam ve kapsamlı bir çözüm satmaya yöneliktir. Bunun nedeni, her uygulamanın diğerlerinden tamamen farklı olmasından kaynaklanır. Ancak, DevOps 'u çok daha az bir işlem teklifi haline getirmek için araçlar vardır. Bu araçlardan biri Azure DevOps olarak bilinir.

## <a name="azure-devops"></a>Azure DevOps

Azure DevOps 'ın uzun bir Pedigree vardır. Team Foundation Server ilk olarak çevrimiçi taşındığında ve çeşitli ad değişikliklerinden, köklerinin geri izini yapabilir: Visual Studio Online ve Visual Studio Team Services. Ancak, yıl boyunca öncüllerinden çok daha fazla hale geldi.

Azure DevOps, beş ana bileşene ayrılmıştır:

![Şekil 11-1 Azure DevOps 'ın beş ana alanı](./media/devops-components.png)

**Azure boards** -kullanıcıların kendileri için en iyi şekilde çalışan iş akışlarını seçmesini sağlayan bir sorun ve iş öğesi izleme aracı sağlar. Bu, geliştirmede SCRUM ve Kanban stillerini desteklemeye yönelik bir dizi önceden yapılandırılmış şablon içerir. 

Venerable Team Foundation Sürüm Denetimi (TFVC) ve sektör ile sık kullanılan git 'i destekleyen **Azure Repos** kaynak kodu yönetimi. Çekme istekleri, değişiklikler yapıldıktan sonra tartışarak sosyal kodlamayı etkinleştirmek için bir yol sağlar.

**Azure Pipelines** -Azure ile sıkı tümleştirmeyi destekleyen bir derleme ve sürüm yönetim sistemi. Derlemeler, Windows 'dan Linux 'a ve MacOS 'a kadar çeşitli platformlarda çalıştırılabilir. Derleme aracıları bulutta veya şirket içinde sağlanabilir.

**Azure test Plans** -test Plans özelliği tarafından sunulan test yönetimi ve keşif testi desteğiyle soru-cevap yok.

**Azure Artifacts** -şirketlerin kendi, dahili, NuGet, NPM ve diğer sürümlerini oluşturmalarına olanak tanıyan bir yapıt akışı. Merkezi bir depoda hata oluşursa, yukarı akış paketleri önbelleği görevi gören iki amaca hizmet eder.

Azure DevOps 'daki en üst düzey kuruluş birimi bir proje olarak bilinir. Her proje içinde Azure Artifacts gibi çeşitli bileşenler açılabilir ve kapatılabilir. Kullanıcılar kendi kaynak kodlarını GitHub 'da yönetmek istiyorsam, ancak Azure Pipelines avantajlarından yararlanıyorsa, bu kadar kusursuz olabilir. Aslında, çok sayıda açık kaynaklı proje, Azure DevOps tarafından sunulan [ücretsiz derlemelerin](https://azure.microsoft.com/blog/announcing-azure-pipelines-with-unlimited-ci-cd-minutes-for-open-source/) üzerinden, GitHub 'da kaynak kodu tutulması sırasında faydalanır. [Visual Studio Code](https://code.visualstudio.com/), [Yarn](https://yarnpkg.com/en/), [Gulp](https://gulpjs.com/)ve [sayısal tuş y](https://www.numpy.org/) gibi bazı önemli açık kaynaklı projeler geçişi yaptı.

Bu bileşenlerin her biri, bulutta yerel uygulamalar için bazı avantajlar sağlar, ancak kaynak denetimi, panolar ve işlem hatları en çok yararlı olan üç seçenektir.  

## <a name="source-control"></a>Kaynak denetimi

Bulutu yerel bir uygulama için kodu düzenleme zor olabilir. Tek bir çok büyük paketlerini uygulaması yerine, bulutta yerel uygulamalar birbirleriyle iletişim kuran küçük uygulamalardan oluşan bir Web 'den oluşmuştur. Bilgi işlem ile ilgili tüm işlemler sayesinde kodun en iyi düzenlenmesi açık bir soru kalır. Farklı tür düzenleri kullanan başarılı uygulamalara örnekler vardır, ancak iki çeşit en popülerliği olan şekilde görünür.

Gerçek kaynak denetimini açmadan önce, büyük olasılıkla kaç projenin uygun olduğuna karar verdik. Tek bir proje içinde birden çok depo için destek ve işlem hatları oluşturma. Panolar biraz daha karmaşıktır ancak tek bir projede birden çok takıma kolayca atanabilir. Tek bir Azure DevOps projesi dışında yüzlerce, hatta binlerce geliştiricisi desteklemek kesinlikle mümkündür. Bunun yapılması, tüm geliştiricilerin dışında çalışması için tek bir yer sağladığı ve geliştiricilerin hangi projede bulunduğu konusunda emin olduğu durumlarda bir uygulamayı bulmanın karışmasını azaltan en iyi yaklaşım olabilir.

Azure DevOps projesi içindeki mikro hizmetler için kod bölmek biraz daha zor olabilir.

![Şekil 11-2 tek ve birden çok depo](./media/single-repository-vs-multiple.png)

### <a name="repository-per-microservice"></a>Mikro hizmet başına depo

İlk bakışta, bu, mikro hizmetlere yönelik kaynak kodu bölmek için en mantıksal yaklaşım gibi görünüyor. Her depo, bir mikro hizmeti oluşturmak için gereken kodu içerebilir. Bu yaklaşımın avantajları kolayca görülebilir:

1. Uygulamanın oluşturulması ve sürdürülmesi için yönergeler, her deponun kökündeki bir BENIOKU dosyasına eklenebilir. Depolarda geçiş yaparken, bu yönergeleri kolayca bulabilir ve geliştiriciler için dönüş süresini azaltır.
2. Her hizmet mantıksal bir yerde bulunur ve hizmetin adı bilinerek kolayca bulunur.
3. Derlemeler, yalnızca sahip olan depoda bir değişiklik yapıldığında tetiklenmeleri için kolayca ayarlanabilir.
4. Bir depoya gelen değişiklik sayısı, projede çalışan az sayıda geliştiriciyle sınırlıdır.
5. Güvenlik, geliştiricilerin okuma ve yazma izinlerine sahip olduğu depoları kısıtlayarak kolayca ayarlanabilir.
6. Depo düzeyi ayarları, sahip olan takım tarafından, diğer kullanıcılarla en az tartışma ile değiştirilebilir.

Mikro hizmetlerin arkasındaki önemli fikirlerden biri, hizmetlerin yığılıyor ve birbirinden ayrılması gerekir. Hizmetin sınırlarına karar vermek için etki alanı odaklı tasarım kullanırken hizmetler işlem sınırları olarak davranır. Veritabanı güncelleştirmeleri birden çok hizmete yayılmamalıdır. İlgili verilerin bu koleksiyonu, sınırlanmış bir bağlam olarak adlandırılır.  Bu fikir, mikro hizmet verilerinin, hizmetlerin geri kalanından ayrı ve otonom bir veritabanına yalıtımına göre yansıtılmıştır. Bu fikri, kaynak koda kadar tüm şekilde taşımak için harika bir fikir sunar.

Ancak, bu yaklaşım sorunları olmadan değildir. Bizim için daha fazla ölçülü geliştirme sorunlarından biri bağımlılıkları yönetiyor. Ortalama `node_modules` dizini oluşturan dosya sayısını göz önünde bulundurun. Yeni bir yüklemenin, binlerce paket `create-react-app` ile karşılaşmanı olasıdır. Bu bağımlılıkların nasıl yönetileceği sorusu zor bir olaydır. 

Bir bağımlılık güncelleştirilirse, aşağı akış paketleri de bu bağımlılığı güncelleştirmelidir. Ne yazık ki, her ne kadar `node_modules` , geliştirme işini sağlayan, dizin, tek bir paketin birden çok sürümü ile sona erirken, her biri farklı bir temposunda sürümü sürümlü diğer bir paketin bağımlılığı. Bir uygulama dağıtıldığında, hangi bağımlılık sürümü kullanılmalıdır? Şu anda üretimde olan sürüm mi? Şu anda beta sürümünde olan, ancak müşterinin üretime yaptığı zamana göre üretimde olma olasılığı yüksektir mi? Yalnızca mikro hizmetler kullanılarak çözümlenmeyen zor sorunlar.

Çok çeşitli projeler tarafından bağımlı olan kitaplıklar vardır. Mikro hizmetleri her bir depodaki bir biriyle ayırarak iç bağımlılıklar, Azure Artifacts iç depo kullanılarak en iyi şekilde çözülebilir. Kitaplıklar için derlemeler, en son sürümlerini iç tüketim için Azure Artifacts içine gönderir. Yeni güncellenen paketlere bağımlılığı almak için aşağı akış projesi yine de el ile güncellenmelidir.

Diğer bir dezavantajı ise kodu hizmetler arasında taşırken kendisini gösterir. Bir uygulamanın mikro hizmetlere ilk bölümünün% 100 doğru olduğunu düşünmesinin iyi hale getirilememesine karşın, gerçekliği nadiren bir hizmet bölme hatası yapmakla karşılaşıyoruz. Bu nedenle, işlevleri ve bunu destekleyen kodun hizmetten hizmete: depodan depoya taşınması gerekir. Bir depodan diğerine, kod, geçmişi kaybeder. Özellikle bir denetim durumunda, kod parçası üzerinde tam geçmişin çok değerli olduğu birçok durum vardır.

Son ve belki de en önemli dezavantajı değişiklikleri koordine etme. Doğru bir mikro hizmet uygulamasında hizmetler arasında dağıtım bağımlılığı olmamalıdır. Hizmet bir, B ve C 'nin gevşek bir şekilde, her türlü sırada dağıtılması mümkün olmalıdır. Bununla birlikte, aynı anda birden çok depodan geçen bir değişikliği yapmak istenen durumlar da vardır. Bazı örnekler, bir güvenlik deliği kapatmak veya tüm hizmetler tarafından kullanılan bir iletişim protokolünü değiştirmek için bir kitaplığı güncelleştirmeyi içerir.

Bir çapraz depo değişikliği yapmak için her bir depoya yönelik bir işlemenin art arda yapılması gerekir. Her depodaki her bir değişikliğin çekme isteğinde bulunulması ve ayrı olarak incelenmesi gerekir. Bu, koordine etmek ve genellikle sinir bozucu olması zor olabilir.

Birçok havuzun kullanılmasına alternatif olarak, tüm kaynak kodları bir Giant, tüm bil, tek depolarda birlikte koyulamıyor.

### <a name="single-repository"></a>Tek depo

Bu yaklaşımda, bazen [monorepository](https://danluu.com/monorepo/)olarak anılan her hizmet için tüm kaynak kodları aynı depoya konur. İlk olarak, bu durum, kaynak kodu en iyi şekilde ilgilendirmesi muhtemel bir fikir gibi görünüyor. Ancak, bu şekilde çalışmanın bazı işaretlenmiş avantajları vardır.

Birinci avantaj, projeler arasında bağımlılıkları yönetmenin daha kolay olması. Bazı dış yapıt akışına güvenmek yerine, projeler bir başkasına doğrudan içeri aktarabilir. Bu, güncelleştirmelerin anında olduğu ve çakışan sürümlerin geliştiricilerin iş istasyonundaki derleme zamanında bulunmasından kaynaklanıyor demektir. Aslında, bazı tümleştirme testlerini sola kaydırın.

Projeler arasında kod taşırken, dosyalar yeniden yazılmaları yerine taşınmış olarak algılandıkları için geçmişi korumak artık daha kolay olur.

Diğer bir avantajı da, çapraz hizmet sınırlarının tek bir yürütmede yapılabilmesi için bu geniş çaplı değişikliktir. Bu, tek yapmanız gereken düzinelerce değişikliklere sahip olma yükünü azaltır.

Güvenli olmayan programlama uygulamalarını veya bu API 'lerin sorunlu kullanımını algılamak için kodun statik analizini gerçekleştirebilen birçok araç vardır. Birden çok depolu bir dünyada, her deponun, içindeki sorunları bulmak için tekrarlandırılır olması gerekir. Tek bir depo, çözümlemenin tümünü tek bir yerde çalıştırmaya izin verir.

Tek depo yaklaşımının pek çok olumsuz yanı vardır. En çok endişelenmeden biri, tek bir deponun güvenlik konusundaki kaygıları oluşturur. Bir deponun içeriği hizmet modeli başına bir depoda sızsa, kayıp kod miktarı en az olur. Tek bir depoyla şirkete ait olan her şey kaybolabilir. Bu durumda çok sayıda örnek vardı ve oyun geliştirme çabalarının tamamını derler. Birden çok havuza sahip olmak daha az yüzey alanı sunar. Bu, çoğu güvenlik uygulamalarında çok tercih edilir.

Tek Deponun boyutu büyük olasılıkla yönetilebilir hale gelir. Bu, bazı ilginç performans etkilerini gösterir. İlk olarak, Windows ekibindeki geliştiriciler için deneyimi geliştirmek üzere tasarlanan [Git Için sanal dosya sistemi](https://vfsforgit.org/)gibi özelleştirilmiş araçların kullanılması gerekebilir.

Genellikle tek bir depoyu kullanmanın bağımsız değişkeni, Facebook veya Google tarafından bu yöntemi kaynak kodu düzenlemesi için kullanan bir bağımsız değişkene aşağı doğru bir şekilde kullanır. Yaklaşım bu şirketler için yeterince iyi ise, sugüvenin tüm şirketler için doğru yaklaşımdır. Bu konuyla ilgili gerçeği, çok az şirketin Facebook veya Google ölçeği gibi her şey üzerinde çalışır. Bu ölçeklerde oluşan sorunlar, çoğu geliştiriciden farklı olur. Kaz için uygun olan şey, ganıra için iyi olmayabilir.

Sonunda, mikro hizmetler için kaynak kodu barındırmak üzere çözüm kullanılabilir. Ancak çoğu durumda, tek bir depoda çalışan yönetim ve mühendislik ek yükü, Meager avantajlarına değer vermez. Kodu birden çok depoda bölmek, kaygıların daha iyi ayrılmasını ve geliştirme ekipleri arasında bağımsız çalışma sınırı teşvik eder.  

### <a name="standard-directory-structure"></a>Standart dizin yapısı

Tek ve birden çok depolardan bağımsız olarak, her hizmetin kendi dizini olur. Geliştiricilerin projeler arasında hızla çapraz geçiş yapmasına izin veren en iyi iyileştirmelerin biri, standart bir dizin yapısını sürdürmektedir.

![Şekil 11-3 hem e-posta hem de oturum açma hizmetleri için standart bir dizin yapısı](./media/dir-struct.png)

Yeni bir proje oluşturulduğunda, doğru yapıyı yerine koyan bir şablon kullanılmalıdır. Bu şablon, bir iskelet BENIOKU dosyası ve olan `azure-pipelines.yml`bu kullanışlı öğeleri de içerebilir. Herhangi bir mikro hizmet mimarisinde, projeler arasında yüksek ölçüde fark, hizmetlere karşı toplu işlemler yapar ve daha zordur.

Çeşitli kaynak kodu dizinleri içeren tüm dizin için şablon oluşturma sağlayabilen birçok araç vardır. [Yeumman](https://yeoman.io/) JavaScript dünyasında popüler ve GitHub, yakın zamanda aynı işlevselliğin çoğunu sağlayan [Depo şablonları](https://github.blog/2019-06-06-generate-new-repositories-with-repository-templates/)yayımlamıştır.

## <a name="task-management"></a>Görev yönetimi

Herhangi bir projede görevleri yönetmek zor olabilir. En iyi geliştirici üretkenliğini sağlamak için ayarlanacak iş akışı sıralaması hakkında yanıtlanmaya yönelik sayaçtan daha az soru vardır.

Bulutta yerel uygulamalar, geleneksel yazılım ürünlerinden daha küçük olma eğilimindedir veya en azından daha küçük hizmetlere bölünmüştür. Bu hizmetlerle ilgili sorunları veya görevleri izlemek, diğer herhangi bir yazılım projesiyle olduğu kadar önemli olmaya devam eder. Hiç kimse, bazı iş öğelerini izlemeyi kaybetmek veya bir müşteriye, sorununun düzgün şekilde günlüğe kaydedilmez. Panolar proje düzeyinde yapılandırılır, ancak her bir proje içinde, alan tanımlanabilir. Bunlar, çeşitli bileşenlerin tamamında sorunları ortadan kaldırma izni verir. Tüm işleri tek bir yerde tutmanın avantajı, iş öğelerini bir ekipten diğerine daha iyi anlaşıldığında daha kolay bir şekilde taşımanın avantajlarından biridir.

Azure DevOps, önceden yapılandırılmış bir dizi popüler şablonlarla birlikte gelir. En temel yapılandırmada, tüm kullanıcılar kapsam içinde, hangi kişilerin üzerinde çalıştığı ve ne yapılması gerektiği hakkında bilgi verilir. Bu, yazılım oluşturma işleminin bu görünürlüğe sahip olması önemlidir. böylece iş, müşteriye bildirilen Önceliklendirmeleri ve tamamlanmış görevleri gerçekleştirebilir. Kuşkusuz, çok az sayıda yazılım projesi bir işlemi, ve `to do` `done`gibi `doing`basit bir şekilde kolaylaştırır. Kullanıcıların işleme veya `QA` `Detailed Specification` işleme gibi adımları eklemeye başlaması uzun sürmez.

Çevik yöntemlerden daha önemli parçalarından biri, düzenli aralıklarla kendi kendine iç denetim. Bu incelemeler, takımın karşılaştığı sorunlar ve nasıl iyileştirilen hakkında öngörü sağlamak için tasarlanmıştır. Bu, genellikle geliştirme sürecinde sorun ve özellik akışını değiştirmenin anlamı anlamına gelir. Bu nedenle, pano düzenlerini ek aşamalarla genişletmek mükemmel bir durumda.

Panolardaki aşamalar tek kurumsal araç değildir. Panonun yapılandırmasına bağlı olarak, iş öğelerinin bir hiyerarşisi vardır. Panoda görünebilen en ayrıntılı öğe bir görevdir. Bir görev, bir başlık, açıklama, öncelik, kalan iş miktarı tahmini ve diğer iş öğelerine veya geliştirme öğelerine (dallar, işlemeler, çekme istekleri, yapılar vb.) bağlantı için alanlar içerir. İş öğeleri, daha kolay bulabilmek için uygulamanın farklı alanlarında ve farklı yinelemelerde (sprintler) sınıflandırılabilirler.

![Şekil 11-4 Azure DevOps 'ta örnek bir görev](./media/task-details.png)

Açıklama alanı, bekleeceğiniz normal stilleri (kalın, italik alt çizgi ve çizili) ve görüntü ekleyebilme özelliğini destekler. Bu, iş veya hata belirtirken kullanımı çok güçlü bir araç haline getirir.

Görevler, daha büyük bir iş birimini tanımlayan özelliklerle birleştirilebilir. Özellikler, sırasıyla, [estane](https://docs.microsoft.com/azure/devops/boards/backlogs/define-features-epics?view=azure-devops)eklenebilir. Bu hiyerarşideki görevlerin sınıflandırılması, büyük bir özelliğin nasıl kullanıma sunulduklarını anlamak için çok daha kolay hale gelir.

![Şekil 11-5 temel işlem şablonunda varsayılan olarak yapılandırılmış Iş öğesi türleri](./media/board-issue-types.png)

Azure Boards sorunlarda farklı türde görünümler vardır. Henüz zamanlanmamış öğeler biriktirme listesinde görünür. Buradan, bir sprint 'e atanabilir. Sprint, beklenen bir iş miktarı için bir saat kutusudur. Bu iş, aynı zamanda bilet çözünürlüğünü de içerebilir. Bu şekilde, Sprint 'in tamamı Sprint panosu bölümünden yönetilebilir. Bu görünüm, çalışmanın nasıl ilerlediğini gösterir ve Sprint 'in başarılı olup olmadığını sürekli güncelleyen bir tahmin sağlamak için bir yazma grafiği içerir.

![Şekil 11-6 Sprint tanımlı bir pano](./media/sprint-board.png)

Şimdi, Azure DevOps 'daki panolarda harika bir güce sahip olması gerekir. Geliştiriciler için üzerinde ne kadar çalıştıysanız ilgili kolay görünümler vardır. Proje yöneticileri için, mevcut çalışmanın yanı sıra yaklaşan çalışmalarda da görünümler. Yöneticiler için kaynak ve kapasite hakkında çok sayıda rapor vardır. Ne yazık ki, işi izleme gereksinimini ortadan kaldıran, bulutta yerel uygulamalarla ilgili hiçbir şey yoktur. Ancak çalışmayı izlemeniz gerekiyorsa, bu deneyimin Azure DevOps 'dan daha iyi olduğu birkaç yer vardır.

## <a name="cicd-pipelines"></a>CI/CD işlem hatları

Yazılım geliştirme yaşam döngüsünde neredeyse hiçbir değişiklik, sürekli tümleştirme (CI) ve sürekli teslim (CD) gibi bir ad olarak Devrim niteliğinde. Bir değişiklik hataları erken yakalandığında, bir projenin kaynak kodunda otomatik testler oluşturma ve çalıştırma. Sürekli tümleştirme derlemelerinden daha önce, depodan kod çekmek ve testlerin aşılmadığı ya da derlenmemiş olduğunu bulmaları yaygın olmayan bir durumdur. Bu, ayırıcıın kaynağını izlemek için çok büyük bir sonuçlanmıştır.

Genellikle üretim ortamına yazılım dağıtımı, kapsamlı belgeler ve bir adım listesi gerektirir. Bu adımların her biri, çok sayıda hataya yol açık bir işlemde el ile tamamlanması gerekir.

![Şekil 11-7 bir denetim listesi](./media/checklist.png)

Sürekli tümleştirmenin dağılması, yerleşik paketlerin bir ortama dağıtıldığı sürekli teslim olur. El ile gerçekleştirilen işlem, geliştirme hızına uyacak şekilde ölçeklendiremez, bu sayede Otomasyon daha önemli hale gelir. Denetim listeleri, aynı görevleri daha hızlı ve insandan daha doğru yürütebilen betikler tarafından değiştirilmiştir.

Sürekli teslimi sağlayan ortam bir test ortamı olabilir veya birçok büyük teknoloji şirketi tarafından yapıldığı gibi, üretim ortamı olabilir. İkincisi, bir değişikliğin kullanıcılara yönelik üretimi bozmaduymamaları için güven veren yüksek kaliteli testlerde bir yatırım gerektirir. Sürekli tümleştirmenin, kodun erken sürekli teslimi, dağıtım işlemindeki sorunları erken yakaladığı şekilde yakalar.

Derleme ve teslim sürecini otomatikleştirmeye önem derecesi, bulutta yerel uygulamalar tarafından accentuated. Dağıtımlar daha sık gerçekleşir ve daha fazla ortam için daha fazla ortam sağlar.

### <a name="azure-builds"></a>Azure derlemeleri

Azure DevOps, sürekli tümleştirme ve dağıtımı her zamankinden daha kolay hale getirmek için bir araç kümesi sağlar. Bu araçlar Azure Pipelines altında bulunur. Birincisi, YAML tabanlı derleme tanımlarını bir ölçekte çalıştırmaya yönelik bir araç olan Azure Derlemeleriyle yapılır. Kullanıcılar kendi derleme makinelerini getirebilir (derleme için çok dikkatli bir kurulum ortamı gerektiriyorsa) veya Azure 'da barındırılan sanal makinelerin sürekli yenilenmiş havuzundan bir makine kullanabilirsiniz. Bu barındırılan derleme aracıları, yalnızca .NET geliştirmesi değil, Java 'dan Python 'a kadar her şey için çok çeşitli geliştirme araçlarıyla önceden yüklenmiş olarak gelir.

DevOps, her derleme için özelleştirilebilen çok sayıda kullanıma hazır derleme tanımları içerir. Yapı tanımları, kaynak kodla birlikte sürümlendiribilecekleri `azure-pipelines.yml` şekilde, adlı bir dosyada tanımlanır ve depoya iade edilir. Bu, değişiklikler yalnızca o dala iade edilebilir olduğundan, bir dalda derleme ardışık düzeninde değişiklik yapmayı çok daha kolay hale getirir. Şekil 11-8 `azure-pipelines.yml` ' de, tam çerçeve üzerinde ASP.NET Web uygulaması oluşturmaya yönelik bir örnek gösterilmektedir.

```yml
name: $(rev:r)

variables:
  version: 9.2.0.$(Build.BuildNumber)
  solution: Portals.sln
  artifactName: drop
  buildPlatform: any cpu
  buildConfiguration: release
  
pool:
  name: Hosted VS2017
  demands:
  - msbuild
  - visualstudio
  - vstest

steps:
- task: NuGetToolInstaller@0
  displayName: 'Use NuGet 4.4.1'
  inputs:
    versionSpec: 4.4.1

- task: NuGetCommand@2
  displayName: 'NuGet restore'
  inputs:
    restoreSolution: '$(solution)'
    
- task: VSBuild@1
  displayName: 'Build solution'
  inputs:
    solution: '$(solution)'
    msbuildArgs: '/p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.artifactstagingdirectory)\\"'
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

- task: VSTest@2
  displayName: 'Test Assemblies'
  inputs:
    testAssemblyVer2: |
     **\$(buildConfiguration)\**\*test*.dll
     !**\obj\**
     !**\*testadapter.dll
    platform: '$(buildPlatform)'
    configuration: '$(buildConfiguration)'

- task: CopyFiles@2
  displayName: 'Copy UI Test Files to: $(build.artifactstagingdirectory)'
  inputs:
    SourceFolder: UITests
    TargetFolder: '$(build.artifactstagingdirectory)/uitests'

- task: PublishBuildArtifacts@1
  displayName: 'Publish Artifact'
  inputs:
    PathtoPublish: '$(build.artifactstagingdirectory)'
    ArtifactName: '$(artifactName)'
  condition: succeededOrFailed()
```

**Şekil 11-8** -örnek bir Azure-Pipelines. yıml

Bu derleme tanımı, bir LEGO kümesi oluşturma (çok büyük paketlerini Millenium 'dan daha basit) kadar basit derlemeler oluşturmayı sağlayan bir dizi yerleşik görevi kullanır. Örneğin, NuGet görevi NuGet paketlerini geri yükler, ancak VSBuild görevi, gerçek derlemeyi gerçekleştirmek için Visual Studio derleme araçları 'nı çağırır. Azure DevOps 'da, topluluk tarafından sürdürülen binlerce daha fazla farklı görev mevcuttur. Çalıştırmak istediğiniz derleme görevleri ne olduğuna bakılmaksızın, birisinin zaten bir tane oluşturmuş olması olasıdır.

Derlemeler el ile, bir iade veya bir zamanlamaya göre ya da başka bir yapı tarafından tamamlanarak tetiklenebilir. Çoğu durumda, her iadede oluşturma işlemi tercih edilir. Derlemeler, farklı derlemelerin deponun farklı bölümlerine veya farklı dallara karşı çalışmasını sağlayacak şekilde filtrelenebilir. Bu, çekme isteklerinde daha az test ile hızlı derlemeler çalıştırmaya ve bir gece temelinde bir tam regresyon paketi çalıştırmaya yönelik senaryolar sağlar.

Yapının nihai sonucu, derleme yapıtları olarak bilinen bir dosya koleksiyonudur. Bu yapıtlar, derleme sürecinde bir sonraki adıma geçirilebilir veya bir Azure yapıt akışına eklenebilir, bu nedenle diğer derlemeler tarafından tüketilebilir.

### <a name="azure-devops-releases"></a>Azure DevOps yayınları

Yapılar, yazılımın teslim edilebilir bir pakette derlenmesinden, ancak sürekli teslimi tamamlamaya yönelik yapıların hala bir test ortamına gönderilmesi gerekir. Azure DevOps bu şekilde yayınlar adlı ayrı bir araç kullanır. Yayınlar, derleme için kullanılabilir olan ancak "aşamalar" kavramı sunan aynı görevler kitaplığını kullanır. Aşama, paketin yüklendiği yalıtılmış bir ortamdır. Örneğin, bir ürün bir geliştirme, QA ve bir üretim ortamı kullanabilir. Kod, otomatik testlerin üzerinde çalıştırılabileceği geliştirme ortamına sürekli olarak dağıtılır. Bu testler, Yayını başarılı olduktan sonra el ile test etmek için QA ortamına geçer. Son olarak, kod, herkes tarafından görünür olduğu üretime gönderilir.

![Şekil 11-9 geliştirme, QA ve üretim aşamalarıyla örnek bir yayın işlem hattı](./media/release-pipeline.png)

Derlemedeki her aşama, önceki aşamanın tamamlanmasına göre otomatik olarak tetiklenebilir. Ancak çoğu durumda bu istenmez. Kodu üretime taşımak, birisinin onayını gerektirebilir. Yayınlar, yayın işlem hattının her adımında onaylayanlara izin vererek bunu destekler. Kurallar, belirli bir kişi veya kişi grubunun üretime başlamadan önce bir yayında oturumu kapatması gereken şekilde ayarlanabilir. Bu kapıları el ile kalite denetimleri ve ayrıca üretime neyin gireceğini denetleme ile ilgili herhangi bir düzenleme gereksinimiyle uyumluluk sağlar.

### <a name="everybody-gets-a-build-pipeline"></a>Herkes gövdesi bir derleme işlem hattı alır

Çok sayıda derleme işlem hattı yapılandırmanın bir maliyeti yoktur, bu nedenle mikro hizmet başına en az bir derleme işlem hattı olması avantajlıdır. En ideal olarak, mikro hizmetler her bir ortama bağımsız olarak dağıtılabilir, böylece her birinin, ilgisiz bir kod üreten bir toplu işlem olmadan kendi işlem hattı aracılığıyla serbest bırakılması gerekir. Her bir işlem hattının, her hizmet için derleme işlemindeki çeşitliliğe izin veren kendi onay kümesi olabilir.

### <a name="versioning-releases"></a>Sürüm oluşturma sürümleri

Yayınlar işlevini kullanmanın bir dezavantajı, iade edilmiş `azure-pipelines.yml` dosyada tanımlanamıyoruz. Proje şablonunuzda bir yayın iskeçine dahil etmek için dal başına sürüm tanımlarının olmasını sağlamak isteyebileceğiniz birçok neden vardır. Neyse ki, bazı aşamalar desteğini yapı bileşenine kaydırmak için iş devam etmektedir. Bu, çok aşamalı derleme olarak bilinir ve [ilk sürüm şimdi kullanılabilir](https://devblogs.microsoft.com/devops/whats-new-with-azure-pipelines/)olacaktır!

>[!div class="step-by-step"]
>[Önceki](azure-security.md)
>[İleri](infrastructure-as-code.md)
