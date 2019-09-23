---
title: WCF geliştiricileri için giriş-gRPC
description: Giriş
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 2782f28e8a99fa7c0bde69f757d14e96e91f5cd4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184423"
---
# <a name="introduction"></a>Giriş

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Makinelerin birbirleriyle iletişim kurmasına yardımcı olmak, dijital Age 'in birincil ön mesleklerden biridir. Özellikle, geçerli altyapının birlikte çalışabilirlik taleplerini karşılayacak olan en iyi uzaktan iletişim mekanizmasını tespit etmek için devam eden bir çaba vardır. Imagine de olduğu gibi, bu mekanizma talep veya altyapı geliştikçe değişir.

.NET Core 3,0 sürümü, Microsoft 'un bir dizi platformda hizmet sunmak isteyen geliştiricilere uzaktan iletişim çözümleri sunacak şekilde bir kaydırma işaretini işaretler. .NET Core, kutudan Windows Communication Foundation (WCF) sunmaz, ancak sürüm ASP.NET Core 3,0 sürümü ile yerleşik gRPC işlevselliği sağlar.

gRPC, modern RPC senaryolarında birçok programlama dilinde geliştiriciler tarafından kullanılan geniş yazılım topluluğu 'nda popüler bir çerçevedir. Topluluk ve ekosistem, Kubernetes, hizmet kafesleri, yük dengeleyiciler ve daha fazlası gibi altyapı bileşenlerine eklenmekte olan gRPC protokolünün desteğiyle canlı ve etkindir. Bu faktörlerin yanı sıra performans, verimlilik ve platformlar arası uyumluluk, .NET Core 'a taşınan yeni uygulamalar ve WCF uygulamaları için gRPC 'yi doğal bir seçenek haline getirir.

## <a name="history"></a>Geçmiş

Bir bilgisayar ağının temel prensibi, birbiriyle ilişkili bir görev kümesini elde etmek için birbirleriyle verileri değiş tokuş eden bir bilgisayar grubundan daha fazla şey değiştirmemiştir. Ancak karmaşıklık, ölçek ve beklentiler üstel olarak artmıştır.  

1990s sırasında, vurgu genellikle aynı dil ve platformları kullanarak iç ağların geliştirilmesine odaklanmıştı. TCP/IP, bu tür iletişim için altın standart haline geldi.

Ancak, odak yakında çok sayıda platformda iletişimin en iyi şekilde iyileştirilmesi, dilden bağımsız bir yaklaşımı yükseltmekte. Hizmet odaklı mimari (SOA), bir uygulamaya sağlanbir çok çeşitli hizmetler koleksiyonunu gevşekme için bir yapı sağladı.

*Web Hizmetleri* geliştirmesi, tüm büyük platformlar Internet 'e erişebildikten sonra oluştu, ancak yine de birbirleriyle etkileşim kuramadık. Web hizmetlerinde aşağıdakiler de dahil olmak üzere açık standartlar ve protokoller vardır:

- XML 'i etiketleyerek ve kod verileri;
- Verileri aktarmak için basit nesne erişim Protokolü (SOAP);
- Web Hizmetleri tanım dili (WSDL) – Web hizmetini tanımlar ve istemci uygulamasına bağlar; *ve*
- Evrensel Açıklama bulma tümleştirmesi (UDDI)-Web hizmetlerinin diğer hizmetler tarafından keşfedilmesini sağlar

SOAP, bir uygulamanın dağıtılan öğelerinin farklı platformlarda olsalar bile birbirleriyle iletişim kurabildiği kuralları tanımlar. SOAP, XML 'yi temel alır, bu nedenle insanlar okunabilir. SOAP 'yi kolayca anlamış hale getirme feice boyutudur. SOAP iletileri karşılaştırılabilir protokollerdeki iletilerden daha büyüktür. SOAP, güvenlik veya denetim kaybı olmadan tek parçalı uygulamaları çok bileşen biçimine bölmek için tasarlandı. Bu nedenle, WCF, dağıtılmış sistem olarak başlayan gRPC 'nin aksine bu tür bir sistemle çalışmak üzere tasarlanmıştır. WCF, SOAP yığını için özel uzantı protokolleri geliştirip belgeleme, ancak diğer platformlardan destek olmaması açısından bu sınırlamaların bazılarını giderilmiştir.

Windows Communication Foundation, hizmet oluşturmaya yönelik bir çerçevedir. İlk adımda, geliştiricilerin SOAP ile çalışan karmaşıklıkları yönetmesi için erken SOA kullanan geliştiricilere yardımcı olması için tasarlanmıştır. Geliştiricinin kendi SOAP protokollerini yazmasının gereksinimini ortadan kaldırmakla birlikte, WCF yine de diğer sistemlerle birlikte çalışabilirliği etkinleştirmek için SOAP kullanır. WCF Ayrıca birden çok protokol (HTTP/1.1, NetTCP vb.) arasında çözümler sunacak şekilde tasarlanmıştır.

## <a name="microservices"></a>Mikro hizmetler

Mikro hizmet mimarilerinde, büyük uygulamalar daha küçük modüler hizmetler koleksiyonu olarak oluşturulmuştur. Her bileşen belirli bir görevi veya işlemi yapar ve bileşenler, her ikisi de birlikte çalışmak üzere tasarlanmıştır, ancak gerektiğinde yalıtılabilir.

Mikro hizmetlerden faydaların avantajları şunlardır:

- Değişiklikler ve yükseltmeler bağımsız olarak işlenebilir.
- Hata işleme, daha sonra yalıtılmış, yeniden oluşturulmuş, test edilmiş ve diğer hizmetlerden bağımsız olarak dağıtılan belirli hizmetlere izlenerek daha etkili hale gelir.
- Ölçeklenebilirlik, tüm uygulama yerine belirli örneklere veya hizmetlere karşı sınırlandırılan bir uygulamadır.
- Birçok ekip tek bir kod tabanında çalıştığı zaman, daha az sayıda takım tarafından daha az gelişmeden, geliştirme işlemi birden fazla ekipte meydana gelebilir.

Daha fazla sanallaştırma, bulut bilgi işlem, kapsayıcılar ve Nesnelerin İnterneti, mikro hizmetlere devam eden daha fazla katkı sağlar. Ancak, mikro hizmetler kendi güçlüklerine sahip değildir. Parçalı/merkezi olmayan altyapı, hizmetler arasında iletişim kurarken kolaylık ve hız ihtiyacını daha fazla vurgulanıyor. Bu, bazen laborious ve SOAP 'nin sürekli yapısına dikkat çekici bir şekilde dikkat çekmesini sağlar.

Bu ortam, Microsoft 'un ilk kez piyasaya sürüldü. Bu, gRPC 'nin başlatıldığı bu ortama vardı. Doğrudan Google 'ın iç altyapı RPC (Stubby) aracılığıyla, gRPC, daha önceki birçok RPC 'nin parametrelerini bilgilendiren aynı standartları ve protokolleri temel almamıştı. Ayrıca, gRPC yalnızca HTTP/2 ' ye dayalıdır ve bu nedenle gelişmiş Aktarım protokolünün sunduğu yeni yetenekler üzerinde çizim yapabilme nedeniydi. Özellikle, çift yönlü akış, ikili mesajlaşma ve çoğullama.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, gRPC 'nin temel özelliklerini içerir. İlk bölümler WCF 'nin ana özelliklerine göz atın ve bunları gRPC ile karşılaştırın. Burada, ' nin WCF ile gRPC arasında ve gRPC 'nin bir avantaj sağladığı yerde nerede olduğunu tanımlar. WCF ve gRPC arasında bağıntı yoktur veya gRPC 'nin WCF 'ye eşdeğer bir çözüm sunamayacağı durumlarda bu kılavuzda, geçici çözümler veya daha fazla bilgi için gidilecek konumlar sunulacaktır.

Örnek WCF uygulamaları kümesi kullanarak, Bölüm 5, WCF hizmetinin ana türlerini (basit istek-yanıt, tek yönlü ve akış) gRPC 'deki eşdeğerlerine dönüştürmekle yakından bir görünüm sağlar.

Kitabýn son bölümü, gRPC 'nin verimliliğine yönelik olarak Docker Kapsayıcıları veya Kubernetes gibi ek araçlar kullanmayı ve günlük, ölçüm ve dağıtılmış izlemeye ilişkin ayrıntılı bir bakış dahil olmak üzere uygulama içinde gRPC 'den en iyi şekilde nasıl yararlanacağınızı inceler. izleniyor.

## <a name="whom-this-guide-is-for"></a>Bu kılavuzun kim olduğu

Bu kılavuz, daha önce WCF kullanan ve .NET Core 3,0 ve sonraki sürümleri için uygulamalarını modern bir RPC ortamına geçirmeyi arayan .NET Framework veya .NET Core 'da çalışan geliştiriciler için yazılmıştır. Bu kılavuz, yerleşik gRPC araçlarını kullanmak isteyen geliştiriciler için .NET Core 3,0 ' a yükseltmeyi veya kullanmayı düşünürken daha genel kullanım de olabilir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](grpc-overview.md)
