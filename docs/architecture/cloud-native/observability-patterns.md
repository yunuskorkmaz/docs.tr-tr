---
title: Observability desenleri
description: Bulutta yerel uygulamalar için Observability desenleri
ms.date: 09/23/2019
ms.openlocfilehash: 23320144c03278d631b8a1fcc1d1c0954e907296
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184878"
---
# <a name="observability-patterns"></a>Observability desenleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aynı şekilde, uygulamalarda kod düzeninde yardımcı olacak desenler geliştirildiği gibi, güvenilir bir şekilde işletim uygulamaları için desenler de vardır. Uygulamaları muhafaza etmek için üç kullanışlı düzen ortaya çıktı: günlüğe kaydetme, izleme ve uyarılar.

## <a name="when-to-use-logging"></a>Günlüğe kaydetme ne zaman kullanılır?

Ne kadar dikkatli oluruz, uygulamalar üretimde beklenmedik yollarla neredeyse her zaman davranır. Kullanıcılar bir uygulamayla ilgili sorunları raporlayabilir, sorun oluştuğunda uygulamayla neler olduğunu görmeniz son derece yararlıdır. Uygulamanın çalışırken ne yaptığını öğrenmek için en az denek ve gerçek yol, uygulamanın ne yaptığını yazalım. Bu işlem günlüğe kaydetme olarak bilinir. Üretimde her zaman veya sorun oluştuğunda, amaç, üretim dışı bir ortamda, hataların oluştuğu koşulları yeniden oluşturmak olmalıdır. İyi bir şekilde oturum açmak, geliştiricilerin test edilmesi ve denedik bir ortamda sorunları yinelemek için izlenmesi için bir yol haritası sağlar.

### <a name="logging-in-cloud-native-applications"></a>Bulutta yerel uygulamalarda günlüğe kaydetme

Her programlama dili, günlüklerin yazılmasına izin veren araçları içerir ve genellikle bu günlükleri yazma yükü düşüktür. Günlüğe kaydetme kitaplıklarının birçoğu, çalışma zamanında ayarlanabilir farklı tür CriticalHandle 'ların günlüğe kaydedilmesini sağlar. Örneğin, Serilog kitaplığı, aşağıdaki günlük düzeylerini sağlayan, .NET için popüler bir yapılandırılmış günlük kitaplığıdır

* Ayrıntılı
* Hata ayıklama
* Bilgiler
* Uyarı
* Hata
* Hataya

Bu farklı günlük düzeyleri günlüğe kaydetme sırasında ayrıntı düzeyi sağlar. Uygulama üretimde düzgün şekilde çalıştığında yalnızca önemli iletileri günlüğe kaydetmek üzere yapılandırılabilir. Uygulama yanlış davrandıktan sonra, daha ayrıntılı günlüklerin toplanması için günlük düzeyi artırılabilir. Bu, performansı hata ayıklamaya karşı dengeler.

Günlük araçlarının yüksek performansı ve ayrıntı düzeyi, geliştiricilerin sıklıkla günlüğe kaydedilmesini teşvik etmelidir. Birçok yöntem, her yöntemin giriş ve çıkış kaydını günlüğe kaydetme düzenlerini tercih. Bu yaklaşım, fazla sonlandırma gibi bir işlem olabilir, ancak geliştiricilerin daha az günlük kaydına istedikleri kadar seyrek görünür. Aslında, sorunlu bir yöntem etrafında günlük kaydı eklemenin tek amacı için dağıtımları gerçekleştirmek yaygın olmayan bir durumdur. Çok fazla günlüğe kaydetme ve çok az bir şey olmadığı tarafında hata. Bu tür bir günlüğe kaydetme işleminin otomatik olarak sağlanması için bazı araçların kullanılabileceğini unutmayın.

Geleneksel uygulamalarda, günlük dosyaları genellikle yerel makinede depolanmıştı. Aslında, UNIX benzeri işletim sistemlerinde, genellikle altında `/var/log`tüm günlükleri tutmak için tanımlanmış bir klasör yapısı vardır. Tek bir makinedeki düz bir dosyaya kaydetmenin yararlılığı, bir bulut ortamında büyük ölçüde azaltılır. Günlüklerin fiziksel makinelere göre karıştırılır, Günlükler üreten uygulamaların yerel diske erişimi olmayabilir veya yerel disk çok daha geçici olabilir.

Mikro hizmetler mimarisi kullanılarak geliştirilen bulutta yerel uygulamalar Ayrıca dosya tabanlı Günlükçüler için bazı zorluklar ortaya çıkarabilir. Kullanıcı istekleri artık farklı makinelerde çalışan birden fazla hizmete yayılabilir ve herhangi bir yerel dosya sistemine erişimi olmayan sunucusuz işlevler içerebilir. Günlükleri bir kullanıcı veya bu çok sayıda hizmet ve makine üzerindeki bir oturumla ilişkilendirmek çok zor olabilir.

Son olarak, bazı bulut yerel uygulamalardaki kullanıcı sayısı yüksektir. Her kullanıcının bir uygulamada oturum açtıklarında yüz satırlık günlük iletileri üretmediğini düşünün. Yalıtımlı, ancak 100.000 ' den fazla Kullanıcı ve günlük hacmi büyük hale gelir.

Neyse ki, dosya sistemi tabanlı günlük kaydı kullanmanın bazı harika alternatifleri vardır. Tüm günlüklerin gönderildiği merkezi bir günlük sunucusu, tüm bu sorunları düzeltir. Günlükler, uygulamalar tarafından toplanır ve günlükleri dizinleyen ve depolayan merkezi bir günlüğe kaydetme uygulamasına gönderilir. Bu sistem sınıfı her gün on binlerce günlük alabilir.

Birçok hizmeti kapsayan günlük oluşturma sırasında bazı standart uygulamaları izlemek da faydalı olur. Örneğin, uzun bir etkileşimin başlangıcında bir [BAĞıNTı kimliği](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/) oluşturma ve ardından bu etkileşime ilişkin her iletide günlüğe kaydetme, tüm ilgili iletileri aramanızı kolaylaştırır. Tek bir ileti bulur ve ilgili tüm iletileri bulmak için bağıntı KIMLIĞINI ayıklar. Diğer bir örnek, günlük biçiminin her hizmet için aynı olduğundan ve kullandığı dil ya da günlüğe kaydetme kitaplığının her ne kadar aynı olmasını sağlamaktır. Bu Standartlaştırma, okuma günlüklerini çok daha kolay hale getirir. Şekil 7-1, mikro hizmet mimarisinin iş akışının bir parçası olarak Merkezi günlük kaydını nasıl yükseltebileceğinizi gösterir.

![Çeşitli kaynaklardaki Günlükler merkezi bir günlük deposuna alınır. **Şekil 7-1**. ](./media/centralized-logging.png)
 Çeşitli kaynaklardaki Günlükler merkezi bir günlük deposuna alınır.

## <a name="when-to-use-monitoring"></a>İzlemenin ne zaman kullanılacağı

Bazı uygulamalar görev açısından kritik değildir. Belki de yalnızca dahili olarak kullanılıyor ve bir sorun ortaya çıktığında, Kullanıcı takımdan sorumlu ile iletişim kurabilme ve uygulamanın yeniden başlatılması olabilir. Ancak, müşteriler genellikle kullandıkları uygulamalar için daha yüksek beklentileri vardır. Kullanıcılarınız *başlamadan önce* uygulamanızdaki sorunları ne zaman meydana geldiğinde veya kullanıcıların sizi bilgilendirmesi durumunda, geçerli durumunu izlemeniz gerekir. Düzgün şekilde uygulandığında, sorun ortaya çıkan koşullar hakkında bilgi edinmek için herhangi bir Kullanıcı etkisine girmeden önce temel koşulları ele almanız gerekir.

## <a name="monitoring-considerations"></a>İzleme konuları

Bazı Merkezi günlük sistemleri,, saf günlüklerin dışında telemetri toplamanın ek bir rolünü alır. Veritabanı sorgusu çalıştırma zamanı, bir Web sunucusundan ortalama yanıt süresi ve hatta işletim sistemi tarafından bildirilen CPU yükü ortalamaları ve bellek baskısı gibi ölçümleri toplayabilirler. Bu sistemler, Günlükler ile birlikte sistemdeki ve uygulamadaki düğümlerin sistem durumunun bir bütün olarak bütünsel görünümünü sağlayabilir.

İzleme araçlarının ölçüm toplama özellikleri, uygulamanın içinden el ile de dağıtılabilir. Yeni kullanıcılar için kaydolan ve yerleştirilmiş siparişler gibi belirli iş akışları, merkezi izleme sisteminde bir sayacı artırmaları gibi belgelenmiş olabilir. Bu, izleme araçlarının kilidini yalnızca uygulamanın sistem durumunu, ancak iş durumunu izlemek için kaldırır.

Sorgular, özel panolar üzerinde grafik biçiminde görüntülenebilen belirli istatistikleri veya desenleri aramak için günlük toplama araçları ' nda oluşturulabilir. Genellikle takımlar, bir uygulamayla ilgili istatistikte geçen büyük, duvara takılan ekranlarda yatırım yapar. Bu şekilde, sorunları ortaya çıktığında görmek basittir.

## <a name="when-to-use-alerts"></a>Uyarılar ne zaman kullanılır?

Uygulamanızla ilgili sorunlara yanıt vermek gerekirse, doğru personeli uyarmak için bir yol gerekir. Bu, üçüncü bulut Yerel uygulama Observability deseninin yanı sıra günlüğe kaydetme ve izlemeye bağlıdır. Uygulamanın, sorunların tanılanabileceği ve bazı durumlarda izleme araçlarına akışını sağlamak için oturum açması gerekir. Uygulama ölçümlerini ve sistem durumu verilerini tek bir yerde toplamak için izlemeye ihtiyaç duyuyor. Bu bir kez kurulduktan sonra, belirli ölçümler kabul edilebilir düzeylerin dışına düşecek şekilde uyarı tetiklenecek kurallar oluşturulabilir.

## <a name="alerts"></a>Uyarılar

Bilinen hata koşullarını aramak için izleme araçlarına karşı sorgular oluşturabilirsiniz. Örneğin, sorgular, Web sunucusundaki bir sorunu belirten HTTP durum kodu 500 göstergeleri için gelen günlüklerde arama sağlayabilir. Bunlardan biri algılandıktan hemen sonra, araştırmaya başlayabilen kaynak hizmetin sahibine e-posta veya SMS gönderilebilir.

Genellikle, bir sorun oluştuğunu belirleyebilmek için tek 500 hatası yeterli değildir. Kullanıcı parolasını yanlış yazmış veya bazı hatalı biçimlendirilmiş veriler girdiği anlamına gelebilir. Uyarı sorguları yalnızca ortalama 500 hata sayısından daha büyük bir hata algılandığında tetiklenebilir.

Uyarı verme sırasında en zararlı desenlerden biri, insanların araştırılması için çok fazla uyarı tetikleyemedi. Hizmet sahipleri, daha önce araştırdıkları ve zararsız olmaya bulduğu hatalara hızla Desensitized. Doğru hatalar oluştuğunda, yüzlerce hatalı pozitif sonuç gürültüsüne karşı kaybolacaktır. [Wolf 'Yi düşünen erkek](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf) 'nın, bu çok tehlike altında bunları uyarmak için sık sık alt öğe olduğunu söyledi. Yangın gerektiren uyarıların gerçek bir sorunu belirttiğinden emin olmak önemlidir.

>[!div class="step-by-step"]
>[Önceki](monitoring-health.md)
>[İleri](logging-with-elastic-stack.md)
