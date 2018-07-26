---
title: Sunucusuz mimari - sunucusuz uygulamalar
description: Çeşitli mimarileri ve web uygulamaları, mobil ve IOT gibi sunucusuz mimarileri tarafından desteklenen uygulamaların incelenmesi.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: ea944a172154a1cff2b8f830cb8fc3fa24a15028
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37405027"
---
# <a name="serverless-architecture"></a>Sunucusuz mimari

Sunucusuz mimarileri kullanarak birçok yaklaşım vardır. Bu bölümde, sunucusuz tümleştirme yaygın mimarileri örnekleri inceler. Ayrıca, ek zorluklarına neden olur veya ek göz önünde bulundurarak sunucusuz uygularken gerektiren sorunları da kapsar. Çeşitli tasarım örnekleri son olarak, çeşitli sunucusuz kullanım durumları göstermek sağlanır.

Sunucusuz konakları genellikle bir kapsayıcı tabanlı varolan veya PaaS katman sunucusuz örneğini yönetmek için kullanın. Örneğin, Azure işlevleri üzerinde temel [Azure App Service](https://docs.microsoft.com/azure/app-service/). App Service, örnekleri ölçeklendirme ve Azure işlevleri kodu yürüten çalışma zamanının yönetmek için kullanılır. Windows tabanlı işlevler için PaaS ve ölçekler konak çalışırken out .NET çalışma zamanı. Linux tabanlı işlevler için ana bilgisayar kapsayıcıları yararlanır.

![Azure işlevleri mimarisi](./media/azure-functions-architecture.png)

WebJobs çekirdek işlevi için bir yürütme bağlamı sağlar. Dil çalışma zamanı kitaplıkları yürütür betikleri çalıştırır ve hedef dil için framework barındırır. Örneğin, Node.js, JavaScript işlevleri çalıştırmak için kullanılır ve .NET Framework, C# işlevleri çalıştırmak için kullanılır. Bu bölümde daha sonra dil ve platform seçenekleri hakkında daha fazla bilgi edinin.

Bazı projeler için "tamamen" bir yaklaşım için sunucusuz fotoğrafını çekmenizi avantajlı olabilir. Mikro hizmetler üzerinde yoğun dayanan uygulamalar, sunucusuz bir teknolojiyi kullanarak tüm mikro Hizmetleri uygulayabilir. Uygulamaları etkinleştirildiklerinde karma, N katmanlı bir tasarım aşağıdaki ve bileşenleri modüler ve bağımsız olarak ölçeklenebilir olduğundan, anlamlı bileşenleri için sunucusuz kullanma. Bu senaryolarda anlamlı yardımcı olmak için bu bölümde sunucusuz kullanın bazı yaygın mimari örneklerle size yol gösterir.

## <a name="full-serverless-back-end"></a>Tam sunucusuz bir arka uç

Özellikle yeni oluştururken tam sunucusuz bir arka uç çeşitli senaryolar için ideal olan ya da "Yeşil alan" uygulamaları. API'lerden oluşan geniş bir yüzey alanı ile bir uygulama, her API bir sunucusuz işlev olarak uygulamadan gelen avantajlı olabilir. Mikro hizmet mimarisini temel alan tam sunucusuz bir arka uç uygulanabileceğine başka bir örnek uygulamalardır. Mikro hizmetler birbiriyle çeşitli protokoller üzerinden iletişim kurar. Belirli senaryolar şunlardır:

* API tabanlı SaaS ürünlerini (örnek: finansal ödeme işlemci).
* İleti güdümlü uygulamaları (örnek: izleme çözümüne cihaz).
* Uygulamaları odaklanmış hizmetleri arasında tümleştirme (örnek: Havayolu kayıt uygulama).
* Düzenli aralıklarla çalışan işler (örnek: Zamanlayıcı tabanlı veritabanı temizleme).
* Uygulamaları odaklı veri dönüşümü (örnek: karşıya dosya yükleme tarafından tetiklenen içeri aktarma).
* Dönüştürme ve yükleme (ETL) işlemleri ayıklayın.

Bu belgenin sonraki bölümlerinde ele alınmaktadır diğer, daha özel kullanım örnekleri vardır.

## <a name="monoliths-and-starving-the-beast"></a>Hamleye olanak ve "beast Kaynaksız"

Ortak bir challenge, mevcut tek parça bir uygulamayı buluta geçiriyor. Az riskli "kaldırma ve kaydırma" tamamen sanal makineleri bir yaklaşımdır. Birçok mağazasında kendi kod tabanının modernize etme fırsatı geçiş kullanmayı tercih eder. Geçiş için pratik bir yaklaşım "beast Kaynaksız." olarak adlandırılır Bu senaryoda, tek "olduğu gibi" geçirilir başlamak. Ardından, seçili hizmetlere modernleştirdiğini. Bazı durumlarda, aynı imza hizmeti: yalnızca bir işlev olarak barındırılır. İstemciler yeni hizmet yerine tek uç noktasını kullanacak şekilde güncelleştirildi. Bu arada, veritabanı çoğaltma gibi adımları da işlem tarafından tek hala işlenir, kendi depolama barındırmak üzere mikro hizmetlerini etkinleştirin. Sonuç olarak, tüm istemcilerin yeni Hizmetleri'ni geçirilir. "Tek starved" (kendi Hizmetleri artık denir) kadar tüm işlevselliği değiştirilmiştir. Sunucusuz birleşimi ve proxy'ler bu geçiş çoğunu kolaylaştırmak.

![Sunucusuz tek geçiş](./media/serverless-monolith-migration.png)

Bu yaklaşımı hakkında daha fazla bilgi edinmek için videoyu izleyin: [bulutta olan sunucusuz Azure işlevleri ile uygulamanızı taşıyın](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Web uygulamaları

Web apps, sunucusuz uygulamalar için mükemmel adaylardır. İki ortak yaklaşım vardır web Apps'e Bugün: sunucu tabanlı ve istemci odaklı (örneğin, tek sayfalı uygulama veya SPA). Sunucu tabanlı web uygulamaları, ara yazılım katmanı genellikle web kullanıcı Arabirimi oluşturmak için API çağrıları için kullanılır. SPA uygulamaları REST API çağrıları, doğrudan tarayıcıdan oluşturun. Her iki senaryoda, sunucusuz bir ara yazılım ya da REST API isteği gerekli iş mantığı sağlayarak barındırabilir. Basit statik web sunucusu bekleme sık karşılaşılan bir mimaridir. Tek sayfa uygulama (SPA), HTML, CSS, JavaScript ve diğer tarayıcı varlıklar işlevi görür. Web uygulaması, ardından bir mikro hizmetler arka ucuna bağlanır.

## <a name="mobile-back-ends"></a>Mobil arka Uçlar

Sunucusuz uygulamalar, olay temelli paradigma bunları mobil arka uçları ideal hale getirir. Mobil cihaz olaylarını tetikler ve istekleri karşılamak için sunucusuz bir kod yürütür. Sunucusuz bir modelin faydalanarak iş mantığı tam uygulama güncelleştirmesi dağıtmak zorunda kalmadan geliştiren geliştiricilerin sağlar. Sunucusuz bir yaklaşım da ekiplerin uç noktaları paylaşmak ve paralel şekilde çalışmasını sağlar.

Mobil uygulama geliştiricileri, sunucu tarafında uzmanı olmak olmadan iş mantığı oluşturabilirsiniz. Geleneksel olarak, şirket içi hizmetler için bağlı mobil uygulamalar. Hizmet katmanı oluşturma, sunucu platformunu anlama ve paradigma programlama gereklidir. Geliştiriciler, sunucuları sağlama ve bunları uygun şekilde yapılandırmak için işlemleriyle çalışmıştır. Bazen bir gün veya hafta bile bir dağıtım işlem hattı oluşturmaya harcanan. Tüm bu zorluklar sunucusuz tarafından ele alınır.

Sunucusuz, sunucu tarafı bağımlılıkları soyutlar ve geliştirici iş mantığına odaklanırsınız sağlar. Örneğin, bir JavaScript çerçevesini kullanarak uygulamalar oluşturur bir mobil Geliştirici de JavaScript ile sunucusuz işlevler oluşturabilirsiniz. Sunucusuz konak işletim sistemi, kod, Paket bağımlılıklarını ve daha fazlasını barındırmak için bir Node.js örneği yönetir. Geliştirici bir Basit dizi girişleri ve standart şablon çıktıları için sağlanır. Ardından oluşturmak ve test iş mantığı üzerinde odaklanabilir. Bu nedenle yeni platformlar öğrenin veya bir "sunucu tarafı geliştiricisi." olun gerekmeden mobil uygulama arka uç mantığını oluşturmak için mevcut becerilerini kullanabilir

![Sunucusuz mobil arka bitiş](./media/serverless-mobile-backend.png)

Çoğu bulut sağlayıcıları tüm mobil geliştirme yaşam döngüsü basitleştirmek mobile tabanlı sunucusuz ürünleri sunar. Ürünler, veriyi kalıcı hale getirmek, DevOps konuları ele, bulut tabanlı derlemeler ve tercih edilen dil test çerçeveleri ve komut dosyası iş süreçlerini geliştiricinin kullanma olanağı sağlayan veritabanlarının sağlanması otomatikleştirebilir. Mobil odaklı, sunucusuz bir yaklaşımı izleyerek sürecini kolaylaştırır. Sunucusuz, sağlama, yapılandırma ve mobil arka uç sunucularını koruma Bilim insanları için inanılmaz yükünü kaldırır.

## <a name="internet-of-things-iot"></a>Nesnelerin interneti (IOT)

IOT birlikte ağa fiziksel nesnelere başvurur. Bunlar bazen "bağlı cihazlar" veya "Akıllı cihazlar." olarak adlandırılır Her şeyi arabalar ve satış makineler bağlanabilir ve envanterinden, sıcaklık ve nem gibi sensör verilerini arasında değişen bilgi gönder. Kurumsal IOT iş izleme ve Otomasyon aracılığıyla işlem geliştirmeleri sağlar. IOT verilerini büyük ambardaki iklim düzenleyen veya tedarik zinciri stoktan izlemek için kullanılabilir. IOT, kimyasal sızıntılar algılayacak ve yangın departmanı Duman algılandığında çağırın.

Çalıştırmaları birimin cihazlar genellikle bilgi ve bir olay denetimli mimari rota ve işlem iletileri belirler. İdeal bir çözüm, çeşitli nedenlerle sunucusuz:

* Etkinleştirir, cihazlar ve veriler arttıkça birimi olarak ölçeklendirin.
* Yeni cihazlardan ve sensörlerden desteklemek için yeni uç nokta ekleme kapsar.
* Geliştiriciler tüm sistem dağıtmak zorunda kalmadan belirli bir cihaz için iş mantığı güncelleştirebileceğiniz bağımsız sürüm oluşturmayı kolaylaştırır.
* Dayanıklılık ve daha az çalışmama süresi.

IOT kapsamlılığıyla sunucusuz çeşitli ürünleri, IOT sorunları, özel olarak odaklanan gibi sonuçlandı [Azure IOT hub'ı](https://docs.microsoft.com/azure/iot-hub). Sunucusuz, cihaz kaydı, ilke zorlaması, izleme ve kod cihazlara bile dağıtım gibi görevleri otomatik hale getiren *edge*. Edge sensörlerden ve bağlı çalıştırıcılar, ancak bir active parçası değil, Internet gibi cihazları ifade eder.

>[!div class="step-by-step"]
[Önceki](architecture-approaches.md)
[İleri](serverless-architecture-considerations.md)
