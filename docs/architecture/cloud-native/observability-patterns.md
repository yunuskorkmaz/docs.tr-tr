---
title: Gözlemlenebilirlik desenleri
description: Bulutta yerel uygulamalar için Observability desenleri
ms.date: 05/13/2020
ms.openlocfilehash: db6a56358923025cbcca9478908474227e5da96d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613817"
---
# <a name="observability-patterns"></a>Gözlemlenebilirlik desenleri

Aynı şekilde, uygulamalarda kod düzeninde yardımcı olacak desenler geliştirildiği gibi, güvenilir bir şekilde işletim uygulamaları için desenler de vardır. Uygulamaları muhafaza etmek için üç kullanışlı düzen ortaya çıktı: **günlüğe kaydetme**, **izleme**ve **Uyarılar**.

## <a name="when-to-use-logging"></a>Günlüğe kaydetme ne zaman kullanılır?

Ne kadar dikkatli oluruz, uygulamalar üretimde beklenmedik yollarla neredeyse her zaman davranır. Kullanıcılar bir uygulamayla ilgili sorunları raporlayabilir, sorun oluştuğunda uygulamayla neler olduğunu görmeniz son derece yararlıdır. Uygulamanın çalışırken ne yaptığını öğrenmek için en az denek ve gerçek yol, uygulamanın ne yaptığını yazalım. Bu işlem günlüğe kaydetme olarak bilinir. Üretimde herhangi bir zaman veya sorun oluştuğunda, amaç, üretim dışı bir ortamda, hataların oluştuğu koşulları yeniden oluşturmak olmalıdır. İyi bir şekilde oturum açmak, geliştiricilerin test edilmesi ve denedik bir ortamda sorunları yinelemek için izlenmesi için bir yol haritası sağlar.

### <a name="challenges-when-logging-with-cloud-native-applications"></a>Bulutta yerel uygulamalarla günlüğe kaydetme sorunları

Geleneksel uygulamalarda, günlük dosyaları genellikle yerel makinede depolanır. Aslında, UNIX benzeri işletim sistemlerinde, genellikle altında tüm günlükleri tutmak için tanımlanmış bir klasör yapısı vardır `/var/log` .

![Tek parçalı bir uygulamadaki bir dosyaya oturum açma. ](./media/single-monolith-logging.png)
 **Şekil 7-1**. Tek parçalı bir uygulamadaki bir dosyaya oturum açma.

Tek bir makinedeki düz bir dosyaya kaydetmenin yararlılığı, bir bulut ortamında büyük ölçüde azaltılır. Günlüklerin fiziksel makinelere göre karıştırılır, Günlükler üreten uygulamaların yerel diske erişimi olmayabilir veya yerel disk çok daha geçici olabilir. Birden çok düğümdeki tek parçalı uygulamaların basit ölçeklendirilmesi, uygun dosya tabanlı günlük dosyasını bulmayı zor hale getirir.

![Ölçeklenen tek parçalı bir uygulamadaki dosyalara oturum açma. ](./media/multiple-node-monolith-logging.png)
 **Şekil 7-2**. Ölçeklenen tek parçalı bir uygulamadaki dosyalara oturum açma.

Mikro hizmetler mimarisi kullanılarak geliştirilen bulutta yerel uygulamalar Ayrıca dosya tabanlı Günlükçüler için bazı zorluklar ortaya çıkarabilir. Kullanıcı istekleri artık farklı makinelerde çalışan birden fazla hizmete yayılabilir ve herhangi bir yerel dosya sistemine erişimi olmayan sunucusuz işlevler içerebilir. Günlükleri bir kullanıcı veya bu çok sayıda hizmet ve makine üzerindeki bir oturumla ilişkilendirmek çok zor olabilir.

![Mikro hizmetler uygulamasındaki yerel dosyalara oturum açma. ](./media/local-log-file-per-service.png)
 **Şekil 7-3**. Mikro hizmetler uygulamasındaki yerel dosyalara oturum açma.

Son olarak, bazı bulut yerel uygulamalardaki kullanıcı sayısı yüksektir. Her kullanıcının bir uygulamada oturum açtıklarında yüz satırlık günlük iletileri üretmediğini düşünün. Yalıtımlı, ancak 100.000 ' den fazla Kullanıcı ve günlük hacmi, günlüklerin etkin kullanımını desteklemek için gerekli araçların yeterince büyük hale gelir.

### <a name="logging-in-cloud-native-applications"></a>Bulutta yerel uygulamalarda günlüğe kaydetme

Her programlama dili, günlüklerin yazılmasına izin veren araçları içerir ve genellikle bu günlükleri yazma yükü düşüktür. Günlüğe kaydetme kitaplıklarının birçoğu, çalışma zamanında ayarlanabilir farklı tür CriticalHandle 'ların günlüğe kaydedilmesini sağlar. Örneğin, [Serilog kitaplığı](https://serilog.net/) , aşağıdaki günlük düzeylerini sağlayan, .NET için popüler bir yapılandırılmış günlük kitaplığıdır:

* Ayrıntılı
* Hata ayıklama
* Bilgi
* Uyarı
* Hata
* Hataya

Bu farklı günlük düzeyleri günlüğe kaydetme sırasında ayrıntı düzeyi sağlar. Uygulama üretimde düzgün şekilde çalıştığında yalnızca önemli iletileri günlüğe kaydetmek üzere yapılandırılabilir. Uygulama yanlış davrandıktan sonra, daha ayrıntılı günlüklerin toplanması için günlük düzeyi artırılabilir. Bu, performansı hata ayıklamaya karşı dengeler.

Günlük araçlarının yüksek performansı ve ayrıntı düzeyi, geliştiricilerin sıklıkla günlüğe kaydedilmesini teşvik etmelidir. Birçok yöntem, her yöntemin giriş ve çıkış kaydını günlüğe kaydetme düzenlerini tercih. Bu yaklaşım, fazla sonlandırma gibi bir işlem olabilir, ancak geliştiricilerin daha az günlük kaydına istedikleri kadar seyrek görünür. Aslında, sorunlu bir yöntem etrafında günlük kaydı eklemenin tek amacı için dağıtımları gerçekleştirmek yaygın olmayan bir durumdur. Çok fazla günlüğe kaydetme ve çok az bir şey olmadığı tarafında hata. Bazı araçlar, bu tür bir günlüğe yazmayı otomatik olarak sağlamak için kullanılabilir.

Bulutta yerel uygulamalarda dosya tabanlı günlükleri kullanmayla ilişkili sorunlar nedeniyle merkezi Günlükler tercih edilir. Günlükler, uygulamalar tarafından toplanır ve günlükleri dizinleyen ve depolayan merkezi bir günlüğe kaydetme uygulamasına gönderilir. Bu sistem sınıfı her gün on binlerce günlük alabilir.

Birçok hizmeti kapsayan günlük oluşturma sırasında bazı standart uygulamaları izlemek da faydalı olur. Örneğin, uzun bir etkileşimin başlangıcında bir [BAĞıNTı kimliği](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) oluşturma ve ardından bu etkileşime ilişkin her iletide günlüğe kaydetme, tüm ilgili iletileri aramanızı kolaylaştırır. Tek bir ileti bulur ve ilgili tüm iletileri bulmak için bağıntı KIMLIĞINI ayıklar. Diğer bir örnek, günlük biçiminin her hizmet için aynı olduğundan ve kullandığı dil ya da günlüğe kaydetme kitaplığının her ne kadar aynı olmasını sağlamaktır. Bu Standartlaştırma, okuma günlüklerini çok daha kolay hale getirir. Şekil 7-4, mikro hizmet mimarisinin iş akışının bir parçası olarak Merkezi günlük kaydını nasıl yükseltebileceğinizi gösterir.

![Çeşitli kaynaklardaki Günlükler merkezi bir günlük deposuna alınır. ](./media/centralized-logging.png)
 **Şekil 7-4**. Çeşitli kaynaklardaki Günlükler merkezi bir günlük deposuna alınır.

## <a name="challenges-with-detecting-and-responding-to-potential-app-health-issues"></a>Olası uygulama sistem durumu sorunlarını algılamayla ve yanıt vermeye yönelik sorunlar

Bazı uygulamalar görev açısından önemli değildir. Belki de yalnızca dahili olarak kullanılıyor ve bir sorun ortaya çıktığında, Kullanıcı takımdan sorumlu ile iletişim kurabilme ve uygulamanın yeniden başlatılması olabilir. Ancak, müşteriler genellikle kullandıkları uygulamalar için daha yüksek beklentileri vardır. Kullanıcılarınızın uygulamadan *önce* veya kullanıcıların sizi bilgilendirmesi için ne zaman sorun olduğunu bilmeniz gerekir. Aksi takdirde, bir sorun hakkında bilmeniz için, uygulamanızı veya hatta kuruluşunuzu bir kez sağanağına, sosyal medya gönderilerinden oluşan bir fark etmeniz gerekebilir.

Göz önünde bulundurmanız gerekebilecek bazı senaryolar şunlardır:

- Uygulamanızdaki bir hizmet başarısız olarak devam eder ve yeniden başlatılır, böylece aralıklı olarak yavaş yanıtlara neden olur.
- Günün bazı saatlerinde uygulamanızın yanıt süresi düşüktür.
- Son dağıtımdan sonra, veritabanındaki yükün daha da gezinme yapılır.

Düzgün şekilde uygulandığında, sorun ortaya çıkan koşulları, önemli Kullanıcı etkilerine neden olmadan önce temel koşulları adreslendiribilmenizi sağlayan koşullar hakkında bilgi verebilir.

### <a name="monitoring-cloud-native-apps"></a>Bulutta yerel uygulamaları izleme

Bazı Merkezi günlük sistemleri,, saf günlüklerin dışında telemetri toplamanın ek bir rolünü alır. Veritabanı sorgusu çalıştırma zamanı, bir Web sunucusundan ortalama yanıt süresi ve hatta işletim sistemi tarafından bildirilen CPU yükü ortalamaları ve bellek baskısı gibi ölçümleri toplayabilirler. Bu sistemler, Günlükler ile birlikte sistemdeki ve uygulamadaki düğümlerin sistem durumunun bir bütün olarak bütünsel görünümünü sağlayabilir.

İzleme araçlarının ölçüm toplama özellikleri, uygulamanın içinden el ile de dağıtılabilir. Yeni kullanıcılar için kaydolan ve yerleştirilmiş siparişler gibi belirli iş akışları, merkezi izleme sisteminde bir sayacı artırmaları gibi belgelenmiş olabilir. Bu, izleme araçlarının kilidini yalnızca uygulamanın sistem durumunu, ancak iş durumunu izlemek için kaldırır.

Sorgular, özel panolar üzerinde grafik biçiminde görüntülenebilen belirli istatistikleri veya desenleri aramak için günlük toplama araçları ' nda oluşturulabilir. Genellikle takımlar, bir uygulamayla ilgili istatistikte geçen büyük, duvara takılan ekranlarda yatırım yapar. Bu şekilde, sorunları ortaya çıktığında görmek basittir.

Bulutta yerel izleme araçları, tek parçalı uygulamalar veya dağıtılmış mikro hizmet mimarilerinden bağımsız olarak, uygulamalar için gerçek zamanlı telemetri ve öngörüler sağlar. Bunlar uygulamadan veri toplamaya izin veren araçları ve uygulamanın sistem durumu hakkındaki bilgileri sorgulamak ve görüntülemek için araçlar içerir.

## <a name="challenges-with-reacting-to-critical-problems-in-cloud-native-apps"></a>Bulutta yerel uygulamalarda kritik sorunlara tepki verme sorunları

Uygulamanızla ilgili sorunlara yanıt vermek gerekirse, doğru personeli uyarmak için bir yol gerekir. Bu, üçüncü bulut Yerel uygulama Observability deseninin yanı sıra günlüğe kaydetme ve izlemeye bağlıdır. Uygulamanın, sorunların tanılanabileceği ve bazı durumlarda izleme araçlarına akışını sağlamak için oturum açması gerekir. Uygulama ölçümlerini ve sistem durumu verilerini tek bir yerde toplamak için izlemeye ihtiyaç duyuyor. Bu bir kez kurulduktan sonra, belirli ölçümler kabul edilebilir düzeylerin dışına düşecek şekilde uyarı tetiklenecek kurallar oluşturulabilir.

Genellikle, uyarılar, belirli koşulların takım üyelerine acil sorunları bildirmek üzere uygun uyarıları tetiklemesine benzer şekilde izlemenin üzerine katmanlıdır. Uyarı gerektirebilecek bazı senaryolar şunlardır:

- Uygulamanızın hizmetlerinden biri 1 dakikalık kapalı kalma süresi sonra yanıt vermiyor.
- Uygulamanız isteklerin %1 ' inden fazlasına başarısız HTTP yanıtları döndürüyor.
- Ana uç noktalar için uygulamanızın ortalama yanıt süresi 2000 MS 'yi aşıyor.

### <a name="alerts-in-cloud-native-apps"></a>Bulutta yerel uygulamalardaki uyarılar

Bilinen hata koşullarını aramak için izleme araçlarına karşı sorgular oluşturabilirsiniz. Örneğin, sorgular, Web sunucusundaki bir sorunu belirten HTTP durum kodu 500 göstergeleri için gelen günlüklerde arama sağlayabilir. Bunlardan biri algılandıktan hemen sonra, araştırmaya başlayabilen kaynak hizmetin sahibine e-posta veya SMS gönderilebilir.

Genellikle, bir sorun oluştuğunu belirleyebilmek için tek bir 500 hatası yeterli değildir. Kullanıcı parolasını yanlış yazmış veya bazı hatalı biçimlendirilmiş veriler girdiği anlamına gelebilir. Uyarı sorguları yalnızca ortalama 500 hata sayısından daha büyük bir hata algılandığında tetiklenebilir.

Uyarı verme sırasında en zararlı desenlerden biri, insanların araştırılması için çok fazla uyarı tetikleyemedi. Hizmet sahipleri, daha önce araştırdıkları ve zararsız olmaya bulduğu hatalara hızla Desensitized. Ardından, doğru hatalar oluştuğunda yüzlerce hatalı pozitif sonuç gürültüsünü kaybolur. [Wolf 'Yi düşünen erkek](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) 'nın, bu çok tehlike altında bunları uyarmak için sık sık alt öğe olduğunu söyledi. Yangın gerektiren uyarıların gerçek bir sorunu belirttiğinden emin olmak önemlidir.

>[!div class="step-by-step"]
>[Önceki](monitoring-health.md) 
> [Sonraki](logging-with-elastic-stack.md)
