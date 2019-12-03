---
title: WCF geliştiricileri için giriş-gRPC
description: Giriş
ms.date: 09/02/2019
ms.openlocfilehash: 2f36d6294e2c76309b051fb3af21157cbfc1087a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711230"
---
# <a name="introduction"></a>Giriş

Makinelerin birbirleriyle iletişim kurmasına yardımcı olmak, dijital Age 'in birincil ön mesleklerden biridir. Özellikle, geçerli altyapının birlikte çalışabilirlik taleplerini karşılayacak olan en iyi uzaktan iletişim mekanizmasını tespit etmek için devam eden bir çaba vardır. Imagine de olduğu gibi, bu mekanizma talep veya altyapı geliştikçe değişir.

.NET Core 3,0 sürümü, Microsoft 'un bir dizi platformda hizmet sunmak isteyen geliştiricilere uzaktan iletişim çözümleri sunacak şekilde bir kaydırma işaretini işaretler. .NET Core, kutudan Windows Communication Foundation (WCF) almaz, ancak ASP.NET Core 3,0 sürümü ile yerleşik gRPC işlevselliği sağlar.

gRPC, geniş yazılım topluluğundaki popüler bir çerçevedir. Bu, modern RPC senaryolarında birçok programlama dilinde geliştiriciler tarafından kullanılır. Topluluk ve ekosistem canlı ve etkindir. Kubernetes, hizmet kafesleri, yük dengeleyiciler ve daha fazlası gibi altyapı bileşenlerine gRPC protokolü desteği ekleniyor. Bu faktörler, performansı, verimliliği ve platformlar arası uyumlulukla birlikte, yeni uygulamalar ve WCF uygulamaları için .NET Core 'a geçiş yapmak üzere gRPC 'yi doğal olarak sunmaktadır.

## <a name="history"></a>Geçmiş

Bir bilgisayar ağının temel prensibi, birbiriyle ilişkili bir görev kümesini elde etmek için birbirleriyle verileri değiş tokuş eden bir bilgisayar grubundan daha fazla şey değiştirmemiştir. Ancak karmaşıklık, ölçek ve beklentileri üstel olarak artmıştır.  

1990s sırasında, vurgu temel olarak aynı dili ve platformları kullanan iç ağları geliştirmektir. TCP/IP, bu tür iletişim için altın standart haline geldi.

Odak yakında, dilden bağımsız bir yaklaşımı yükselterek birden çok platformda iletişimin en iyi şekilde ne kadar iyileştirileceği üzerine taşınır. Hizmet odaklı mimari (SOA), bir uygulamaya sağlanbir çok çeşitli hizmetler koleksiyonunu gevşekme için bir yapı sağladı.

*Web Hizmetleri* geliştirmesi, tüm büyük platformlar internet 'e erişebildiklerinde meydana geldi, ancak yine de birbirleriyle etkileşim kuramadık. Web hizmetlerinde aşağıdakiler de dahil olmak üzere açık standartlar ve protokoller vardır:

- XML 'i etiketleyerek ve kod verileri.
- Verileri aktarmak için basit nesne erişim Protokolü (SOAP).
- Web hizmetlerini tanımlamaya ve istemci uygulamalarına bağlamaya yönelik Web Hizmetleri tanım dili (WSDL).
- Web hizmetlerini diğer hizmetler tarafından bulunabilir hale getirmek için Evrensel Açıklama, bulma ve Tümleştirme (UDDI).

SOAP, bir uygulamanın dağıtılmış öğelerinin, farklı platformlarda olsalar bile birbirleriyle iletişim kurabildiği kuralları tanımlar. SOAP, XML 'yi temel alır, bu nedenle insanlar okunabilir. SOAP 'yi kolayca anlamış hale getirme feice boyutudur. SOAP iletileri karşılaştırılabilir protokollerdeki iletilerden daha büyüktür. SOAP, güvenlik veya denetim kaybı olmadan tek parçalı uygulamaları çok bileşen biçiminde bölmek için tasarlandı. Bu nedenle WCF, dağıtılmış bir sistem olarak başlayan gRPC 'nin aksine, bu tür bir sistemle çalışacak şekilde tasarlanmıştır. WCF, SOAP yığını için özel uzantı protokolleri geliştirip belgeleme, ancak diğer platformlardan gelen destek eksikliği maliyetinde bu sınırlamaların bazılarına değinmektedir.

Windows Communication Foundation, hizmet oluşturmaya yönelik bir çerçevedir. İlk adımda, geliştiricilerin SOAP ile çalışan karmaşıklıkları yönetmesi için erken SOA kullanan geliştiricilere yardımcı olması için tasarlanmıştır. Geliştiricilerin kendi SOAP protokollerini yazma gereksinimini ortadan kaldırmakla birlikte, WCF yine de diğer sistemlerle birlikte çalışabilirliği etkinleştirmek için SOAP kullanır. WCF Ayrıca birden çok protokol (HTTP/1.1, net. TCP vb.) arasında çözümler sunacak şekilde tasarlanmıştır.

## <a name="microservices"></a>Mikro hizmetler

Mikro hizmet mimarilerinde, büyük uygulamalar daha küçük modüler hizmetler koleksiyonu olarak oluşturulmuştur. Her bileşen belirli bir görevi veya işlemi yapar ve bileşenler, her ikisi de birlikte çalışmak üzere tasarlanmıştır, ancak gerektiğinde yalıtılabilir.

Mikro hizmetlerden faydaların avantajları şunlardır:

- Değişiklikler ve yükseltmeler bağımsız olarak işlenebilir.
- Hata işleme daha etkili hale gelir çünkü sorunlar daha sonra yalıtılmış, yeniden oluşturulmuş, test edilmiş ve diğer hizmetlerden bağımsız olarak dağıtılan belirli hizmetlere izlenebilir.
- Ölçeklenebilirlik, tüm uygulama yerine belirli örneklere veya hizmetlere karşı sınırlandırılan bir uygulamadır.
- Birçok ekip tek bir kod tabanında çalıştığı zaman, daha az sayıda takım tarafından daha az gelişmeden, geliştirme işlemi birden fazla ekipte meydana gelebilir.

Daha fazla sanallaştırma, bulut bilgi işlem, kapsayıcılar ve Nesnelerin İnterneti, mikro hizmetlere devam eden daha fazla katkıda bulunur. Ancak mikro hizmetler kendi güçlüklerine sahip değildir. Parçalı/merkezi olmayan altyapı, hizmetler arasında iletişim kurarken kolaylık ve hız ihtiyacını daha fazla vurgular. Bu, bazen laborious ve SOAP 'nin sürekli yapısına dikkat çekici bir şekilde dikkat çekmesini sağlar.

Bu ortam, Microsoft 'un ilk kez piyasaya sürüldü. Bu, gRPC 'nin başlatıldığı bu ortama vardı. Doğrudan Google 'ın iç altyapı RPC (Stubby) aracılığıyla, gRPC, daha önceki birçok RPC 'nin parametrelerini bilgilendiren aynı standartları ve protokolleri temel almamıştı. Ve gRPC yalnızca HTTP/2 ' ye dayalıdır. Bu nedenle, gelişmiş Aktarım protokolünün sunduğu yeni özellikleri nasıl çizebileceğiniz. Özellikle, çift yönlü akış, ikili mesajlaşma ve çoğullama.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, gRPC 'nin temel özelliklerini içerir. Erken bölümler, WCF 'nin ana özelliklerine göz atın ve bunları gRPC ile karşılaştırın. WCF ve gRPC arasında doğrudan eş ilişkilerini ve ayrıca gRPC 'nin bir avantaj sağladığı konumu tanımlar. WCF ve gRPC arasında bağıntı olmadığında veya gRPC, WCF 'ye eşdeğer bir çözüm sunamayacağı zaman, bu kılavuzda geçici çözümler veya daha fazla bilgi için nereye gidebileceği gösterilir.

Örnek WCF uygulamaları kümesi kullanarak, Bölüm 5, WCF hizmetinin ana türlerini (basit istek-yanıt, tek yönlü ve akış) gRPC 'deki eşdeğerlerine dönüştürmeye yönelik ayrıntılı bir bakış.

Kitabýn son bölümü, uygulama içinde gRPC 'den en iyi şekilde nasıl alınacağını inceler. Bu bölüm, gRPC 'nin verimliliğinin avantajlarından yararlanmak için Docker Kapsayıcıları veya Kubernetes gibi ek araçları kullanma hakkında bilgi içerir. Ayrıca, günlük, ölçüm ve dağıtılmış izleme ile izlemeye ayrıntılı bir bakış da içerir.

## <a name="who-this-guide-is-for"></a>Bu kılavuzun kim olduğunu

Bu kılavuz, WCF kullanan ve .NET Core 3,0 ve sonraki sürümleri için uygulamalarını modern bir RPC ortamına geçirmeyi arayan .NET Framework veya .NET Core 'da çalışan geliştiriciler için yazılmıştır. Bu kılavuz Ayrıca, .NET Core 3,0 ' e yükseltme veya yerleşik gRPC araçlarını kullanmak isteyen geliştiriciler için daha genel olarak yararlı olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](grpc-overview.md)
