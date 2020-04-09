---
title: Giriş - WCF geliştiricileri için gRPC
description: Giriş
ms.date: 09/02/2019
ms.openlocfilehash: 41f470eb02a77b1b6a26a7d4c2ca347ad07d828d
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988940"
---
# <a name="introduction"></a>Giriş

Makinelerin birbirleriyle iletişim kurmasına yardımcı olmak dijital çağın başlıca kaygılarından biri olmuştur. Özellikle, mevcut altyapının birlikte çalışabilirlik taleplerine uyacak en uygun uzaktan iletişim mekanizmasını belirlemek için devam eden bir çaba vardır. Tahmin edebileceğiniz gibi, bu mekanizma ya talepler ya da altyapı geliştikçe değişiyor.

.NET Core 3.0'ın piyasaya sürülmesi, Microsoft'un çeşitli platformlarda hizmet sunmak isteyen geliştiricilere uzaktan iletişim çözümleri sunma şeklinde bir değişimi işaret eder. .NET Core, Windows Communication Foundation'ı (WCF) kutunun dışında sunmaz, ancak ASP.NET Core 3.0 sürümüyle yerleşik gRPC işlevselliği sağlar.

gRPC daha geniş yazılım topluluğunda popüler bir çerçevedir. Modern RPC senaryoları için birçok programlama dilinde geliştiriciler tarafından kullanılır. Toplum ve ekosistem canlı ve aktiftir. Kubernetes, servis ağları, yük dengeleyicileri ve daha fazlası gibi altyapı bileşenlerine gRPC protokolü desteği ekleniyor. Bu faktörler, performansı, verimliliği ve platform ötesi uyumluluğuyla birlikte, gRPC'yi .NET Core'a taşınan yeni uygulamalar ve WCF uygulamaları için doğal bir seçim haline getirir.

## <a name="history"></a>Geçmiş

Bir bilgisayar ağının, birbiriyle ilişkili bir dizi görevi gerçekleştirmek için birbirleriyle veri alışverişi kuran bir grup bilgisayardan başka bir şey olmadığı temel ilkesi, kuruluşundan bu yana değişmemiştir. Ama karmaşıklık, ölçek ve beklentiler katlanarak büyüdü.  

1990'larda, vurgu daha çok aynı dil ve platformları kullanan iç ağların geliştirilmesi üzerindeydi. TCP/IP bu tür iletişimiçin altın standart haline geldi.

Odak noktası, dil-agnostik bir yaklaşımı teşvik ederek iletişimi birden çok platformda en iyi şekilde optimize etmek için çok daha iyi bir şekilde değişti. Hizmet odaklı mimari (SOA), bir uygulamaya sağlanabilecek geniş bir hizmet koleksiyonunu gevşek bir şekilde birliş için bir yapı sağladı.

*Web hizmetlerinin* geliştirilmesi, tüm büyük platformlar internete erişebildiği, ancak yine de birbirleriyle etkileşime giremedikleri nde meydana geldi. Web hizmetlerinin açık standartları ve protokolleri şunlardır:

- XML etiketleme ve kod verileri.
- Veri aktarmak için Basit Nesne Erişim Protokolü (SOAP).
- Web Hizmetlerini Tanım Dili (WSDL), web hizmetlerini açıklamak ve istemci uygulamalarına bağlamak için.
- Web hizmetlerini diğer hizmetler tarafından keşfedilebilir hale getirmek için Evrensel Açıklama, Bulma ve Tümleştirme (UDDI).

SOAP, bir uygulamanın dağıtılmış öğelerinin farklı platformlarda olsalar bile birbirleriyle iletişim kurabileceği kuralları tanımlar. SOAP XML dayanmaktadır, bu yüzden insan tarafından okunabilir. SOAP'ı kolayca anlamanın fedakarlığı boyutdur; SOAP iletileri karşılaştırılabilir protokoldeki iletilerden daha büyüktür. SOAP, güvenlik veya kontrolü kaybetmeden monolitik uygulamaları çok bileşenli bir forma dönüştürmek için tasarlanmıştır. Yani WCF, dağıtılmış bir sistem olarak başlayan gRPC'nin aksine, bu tür bir sistemle çalışmak üzere tasarlandı. WCF, SOAP yığını için özel genişletme protokolleri geliştirerek ve belgeleyerek bu sınırlamaların bazılarını ele aldı, ancak diğer platformlardan destek almaması pahasına.

Windows Communication Foundation, hizmet oluşturmak için bir çerçevedir. 2000'li yılların başında, SOAP ile çalışmanın karmaşıklığını yönetmek için soa'nın erken dönemlerini kullanan geliştiricilere yardımcı olmak için tasarlanmıştır. Geliştiricilerin kendi SOAP protokollerini yazma gereksinimini ortadan kaldırsa da, WCF diğer sistemlerle birlikte çalışabilirliği sağlamak için SOAP'ı kullanır. WCF ayrıca birden fazla protokol (HTTP/1.1, Net.TCP vb.) genelinde çözümler sunmak üzere tasarlanmıştır.

## <a name="microservices"></a>Mikro hizmetler

Mikro hizmet mimarilerinde, büyük uygulamalar daha küçük modüler hizmetler koleksiyonu olarak oluşturulur. Her bileşen belirli bir görev veya işlem yapar ve bileşenler birlikte çalışacak şekilde tasarlanmıştır, ancak gerektiğinde yalıtılabilir.

Mikro hizmetlerin avantajları şunlardır:

- Değişiklikler ve yükseltmeler bağımsız olarak işlenebilir.
- Hatalar işleme, sorunlar daha sonra yalıtılmış, yeniden yapılandırılan, sınanan ve diğer hizmetlerden bağımsız olarak yeniden dağıtılan belirli hizmetlere izlenebileceğinden daha verimli hale gelir.
- Ölçeklenebilirlik, uygulamanın tamamı yerine belirli örnekler veya hizmetlerle sınırlı olabilir.
- Geliştirme, birden çok takım tek bir kod tabanı üzerinde çalışırken ortaya çıkandan daha az sürtünmeyle birden çok takım arasında gerçekleşebilir.

Artan sanallaştırma, bulut bilgi işlem, kapsayıcılar ve Nesnelerin İnterneti'ne doğru olan hareket, mikro hizmetlerin sürekli yükselişine katkıda bulunmuştur. Ama mikro hizmetler zorlukları olmadan değildir. Parçalanmış/merkezi olmayan altyapı, hizmetler arasında iletişim kurarken basitlik ve hıza duyulan ihtiyaca daha fazla önem vermektedir. Bu da SOAP'ın bazen zahmetli ve çarpık doğasına dikkat çekti.

Microsoft'un WCF'yi ilk piyasaya sürmeden 10 yıl sonra gRPC bu ortamda kullanıma sunuldu. Doğrudan Google'ın dahili altyapısı RPC (Stubby) gelişti, gRPC birçok önceki RPCs parametreleri bilgilendirdi aynı standartlar ve protokoller dayalı değildi. Ve gRPC sadece hiç HTTP / 2 dayanmaktadır. Bu yüzden gelişmiş taşıma protokolünün sağladığı yeni yeteneklerden yararlanabiliyordu. Özellikle, çift yönlü akış, ikili mesajlaşma ve çoklama.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, gRPC'nin temel özelliklerini kapsar. İlk bölümler, WCF'nin ana özelliklerine üst düzey bir göz atabilir ve bunları gRPC ile karşılaştırın. WCF ve gRPC arasında doğrudan korelasyonların nerede olduğunu ve gRPC'nin avantaj sağladığı yeri tanımlar. WCF ve gRPC arasında bir ilişki olmadığında veya gRPC WCF'ye eşdeğer bir çözüm sunamıyorsa, bu kılavuz geçici çözüm önerecek veya daha fazla bilgi için nereye gidilecek.

Örnek WCF uygulamaları kümesini kullanarak, Bölüm 5, wcf hizmetinin ana türlerini (basit istek-yanıt, tek yönlü ve akış) gRPC'deki eşdeğerlerine dönüştürmeye yönelik derin bir bakıştır.

Kitabın son bölümünde pratikte gRPC en iyi almak için nasıl bakar. Bu bölümde, gRPC'nin verimliliğinden yararlanmak için Docker konteynerleri veya Kubernetes gibi ek araçların kullanılmasına ilişkin bilgiler yer almaktadır. Ayrıca, günlük, ölçümler ve dağıtılmış izleme ile izleme ayrıntılı bir görünüm içerir.

## <a name="who-this-guide-is-for"></a>Bu kılavuz kimin için

Bu kılavuz, .NET Framework veya .NET Core'da çalışan ve WCF kullanan ve uygulamalarını .NET Core 3.0 ve sonraki sürümler için modern bir RPC ortamına geçirmek isteyen geliştiriciler için yazılmıştır. Kılavuz, .NET Core 3.0'ı yükseltmeyi düşünen veya geliştiren ve yerleşik gRPC araçlarını kullanmak isteyen geliştiriciler için de daha genel olarak yararlı olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](grpc-overview.md)
