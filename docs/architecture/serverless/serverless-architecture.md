---
title: Sunucusuz mimari - Sunucusuz uygulamalar
description: Web uygulamaları, mobil cihazlar ve IoT gibi sunucusuz mimariler tarafından desteklenen çeşitli mimarilerin ve uygulamaların araştırılması.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 838dcd7b41df0d8297e1ae10f9c04a8d5b83b332
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522401"
---
# <a name="serverless-architecture"></a>Sunucusuz mimari

[Sunucusuz](https://azure.com/serverless) mimarileri kullanmak için birçok yaklaşım vardır. Bu bölümde, sunucusuz tümleştiren ortak mimariörnekleri incelemektedir. Ayrıca, ek zorluklar oluşturabilecek veya sunucusuz uygulama yaparken ekstra dikkate alınması gereken endişeleri de kapsar. Son olarak, çeşitli sunucusuz kullanım örneklerini gösteren çeşitli tasarım örnekleri sağlanır.

Sunucusuz ana bilgisayarlar, sunucusuz örnekleri yönetmek için genellikle varolan kapsayıcı tabanlı veya PaaS katmanını kullanır. Örneğin, Azure İşlevler [Azure Uygulama Hizmeti'ni](https://docs.microsoft.com/azure/app-service/)temel alır. Uygulama Hizmeti, örnekleri ölçeklendirmek ve Azure İşlevler kodunu çalıştıran çalışma zamanını yönetmek için kullanılır. Windows tabanlı işlevler için ana bilgisayar PaaS olarak çalışır ve .NET çalışma süresini ölçekler. Linux tabanlı işlevler için ana bilgisayar kapsayıcılardan yararlanır.

![Azure İşlevler mimarisi](./media/azure-functions-architecture.png)

Webİşler Core işlev için bir yürütme bağlamı sağlar. Dil Çalışma Zamanı komut dosyalarını çalıştırıyor, kitaplıkları yürütür ve hedef dilin çerçevesini barındırıyor. Örneğin, Node.js JavaScript işlevlerini çalıştırmak için kullanılır ve .NET Framework C# işlevlerini çalıştırmak için kullanılır. Bu bölümde dil ve platform seçenekleri hakkında daha fazla bilgi edineceksiniz.

Bazı projeler sunucusuz bir "all-in" yaklaşımı alarak yararlanabilir. Mikro hizmetlere büyük ölçüde dayanan uygulamalar, sunucusuz teknolojiyi kullanarak tüm mikro hizmetleri uygulayabilir. Bileşenler modüler ve bağımsız ölçeklenebilir olduğundan, uygulamaların çoğu n katmanlı bir tasarımı takip ederek ve anlamlı bileşenler için sunucusuz kullanarak karmadır. Bu senaryoları anlamlandırmaya yardımcı olmak için, bu bölüm sunucusuz kullanan bazı ortak mimari örnekleri arasında yürür.

## <a name="full-serverless-back-end"></a>Tam sunucusuz arka uç

Tam sunucusuz arka uç, özellikle yeni veya "yeşil alan" uygulamaları inşa ederken, çeşitli senaryo türleri için idealdir. API'lerin geniş bir yüzey alanına sahip bir uygulama, her API'nin sunucusuz bir işlev olarak uygulanmasından yararlanabilir. Mikro hizmetler mimarisine dayanan uygulamalar, tam sunucusuz arka uç olarak uygulanabilecek başka bir örnektir. Mikro hizmetler birbirleriyle çeşitli protokoller üzerinden iletişim kurarlar. Belirli senaryolar şunlardır:

- API tabanlı SaaS ürünleri (örnek: finansal ödemeler işlemci).
- İleti odaklı uygulamalar (örnek: aygıt izleme çözümü).
- Uygulamalar hizmetler arasındaki entegrasyona odaklanmıştır (örneğin: havayolu rezervasyon uygulaması).
- Düzenli olarak çalışan işlemler (örnek: zamanlayıcı tabanlı veritabanı temizleme).
- Uygulamalar veri dönüşümüne odaklanmıştır (örnek: dosya yükleme tarafından tetiklenen içe aktarma).
- Dönüştürme ve Yükleme (ETL) işlemlerini ayıklayın.

Bu belgede daha sonra kapsanan başka, daha özel kullanım örnekleri vardır.

## <a name="monoliths-and-starving-the-beast"></a>Monolitler ve "canavarı açlıktan ölmek"

Yaygın bir sorun buluta mevcut bir monolitik uygulama geçiştir. En az riskli yaklaşım tamamen sanal makineler üzerine "asansör ve kaydırma" etmektir. Birçok mağaza kendi kod tabanını modernize etmek için bir fırsat olarak göç kullanmayı tercih. Göçe pratik bir yaklaşıma "canavarı aç bırakması" denir. Bu senaryoda, monolit ile başlamak için "olduğu gibi" geçirilir. Ardından, seçilen hizmetler modernize edilir. Bazı durumlarda, hizmetin imzası orijinalle aynıdır: yalnızca bir işlev olarak barındırılır. İstemciler, monolit bitiş noktası yerine yeni hizmeti kullanacak şekilde güncelleştirilir. Bu arada, veritabanı çoğaltma gibi adımlar, hareketler monolit tarafından hala işlenirken bile mikro hizmetlerin kendi depolama alanını barındırmasını sağlar. Sonunda, tüm istemciler yeni hizmetlere geçirilir. Monolit, tüm işlevler değiştirilene kadar "aç" (hizmetleri artık çağrılmamaktadır). Sunucusuz ve yakınlıkların birleşimi bu geçişin çoğunu kolaylaştırabilir.

![Sunucusuz monolit geçişi](./media/serverless-monolith-migration.png)

Bu yaklaşım hakkında daha fazla bilgi edinmek için videoyu izleyin: [Sunucusuz Azure Fonksiyonları ile uygulamanızı buluta getirin.](https://channel9.msdn.com/Events/Connect/2017/E102)

## <a name="web-apps"></a>Web uygulamaları

Web uygulamaları sunucusuz uygulamalar için harika adaylardır. Bugün web uygulamalarına iki yaygın yaklaşım vardır: sunucu odaklı ve istemci odaklı (Tek Sayfa uygulaması veya SPA gibi). Sunucu tarafından yönlendirilen web uygulamaları genellikle web Web Ara Birimi'ni işlemek için API çağrıları vermek için bir ara yazılım katmanı kullanır. SPA uygulamaları REST API aramalarını doğrudan tarayıcıdan yapar. Her iki senaryoda da, sunucusuz, gerekli iş mantığını sağlayarak ara yazılım veya REST API isteğini barındırabilir. Ortak bir mimari hafif statik web sunucusu ayağa kalkmaktır. Tek Sayfa Uygulaması (SPA) HTML, CSS, JavaScript ve diğer tarayıcı varlıklarına hizmet vermektedir. Web uygulaması daha sonra bir microservices arka uç bağlanır.

## <a name="mobile-back-ends"></a>Mobil arka uçlar

Sunucusuz uygulamaların olay odaklı paradigması, mobil arka uçlar olarak onları ideal hale getirir. Mobil aygıt olayları tetikler ve sunucusuz kod isteklerini karşılamak için yürütür. Sunucusuz bir modelden yararlanmak, geliştiricilerin tam bir uygulama güncelleştirmesi dağıtmak zorunda kalmadan iş mantığını geliştirmelerine olanak tanır. Sunucusuz yaklaşım, ekiplerin uç noktaları paylaşmasına ve paralel olarak çalışmasını da sağlar.

Mobil geliştiriciler, sunucu tarafında uzman olmadan iş mantığı oluşturabilir. Geleneksel olarak, şirket içi hizmetlere bağlı mobil uygulamalar. Hizmet katmanının oluşturulması, sunucu platformunun ve programlama paradigmasının anlaşılmasını gerektiriyor. Geliştiriciler, sunucuları sağlamak ve uygun şekilde yapılandırmak için işlemlerle birlikte çalıştı. Bazen günler hatta haftalar dağıtım boru hattı oluşturmak için harcanır. Tüm bu sorunlar sunucusuz tarafından ele alınır.

Sunucusuz, sunucu tarafındaki bağımlılıkları soyutlar ve geliştiricinin iş mantığına odaklanmasını sağlar. Örneğin, JavaScript çerçevesi kullanarak uygulama oluşturan bir mobil geliştirici, JavaScript ile de sunucusuz işlevler oluşturabilir. Sunucusuz ana bilgisayar, kodu, paket bağımlılıklarını ve daha fazlasını barındırmak için işletim sistemini, bir Düğüm.js örneğini yönetir. Geliştiriciye basit bir girdi kümesi ve çıktılar için standart bir şablon sağlanır. Daha sonra iş mantığını oluşturmaya ve sınaya odaklanabilirler. Bu nedenle, yeni platformlar öğrenmek veya "sunucu tarafı geliştiricisi" olmak zorunda kalmadan mobil uygulama için arka uç mantığını oluşturmak için mevcut becerileri kullanabilirler.

![Sunucusuz mobil arka uç](./media/serverless-mobile-backend.png)

Çoğu bulut sağlayıcısı, tüm mobil geliştirme yaşam döngüsünü basitleştiren mobil tabanlı sunucusuz ürünler sunar. Ürünler, verileri sürdürmek, DevOps endişelerini işlemek, bulut tabanlı yapılar ve test çerçeveleri sağlamak ve geliştiricinin tercih ettiği dili kullanarak iş süreçlerini komut dosyası na sahip olmak için veritabanlarının sağlanmasını otomatikleştirebilir. Mobil merkezli sunucusuz bir yaklaşım izleyerek işlemi kolaylaştırabilir. Serverless, mobil arka uç için sunucusağlama, yapılandırma ve bakım muazzam yükü kaldırır.

## <a name="internet-of-things-iot"></a>Nesnelerin İnterneti (IoT)

IoT, birbirine ağa sahip fiziksel nesneleri ifade eder. Bunlar bazen "bağlı aygıtlar" veya "akıllı aygıtlar" olarak adlandırılır. Arabalar ve otomatlar arasında her şey bağlanabilir ve envanterden sıcaklık ve nem gibi sensör verilerine kadar çeşitli bilgiler gönderebilir. İşletmede, IoT izleme ve otomasyon yoluyla iş süreci iyileştirmeleri sağlar. IoT verileri, büyük bir depodaki iklimi düzenlemek veya tedarik zinciri aracılığıyla envanteri izlemek için kullanılabilir. IoT kimyasal sızıntıları algılayabilir ve duman tespit edildiğinde itfaiyeyi arayabilir.

Aygıtların ve bilgilerin hacmi genellikle iletileri yönlendirmek ve işlemek için olay odaklı bir mimari belirler. Serverless çeşitli nedenlerle ideal bir çözümdür:

- Aygıtların ve verilerin hacmi arttıkça ölçeklendirmesağlar.
- Yeni aygıtları ve sensörleri desteklemek için yeni uç noktaları eklemeyi barındırır.
- Bağımsız sürüm, geliştiricilerin tüm sistemi dağıtmak zorunda kalmadan belirli bir aygıtın iş mantığını güncelleştirebilmeleri için kolaylaştırır.
- Esneklik ve daha az kapalı kalma süresi.

IoT'nin yaygınlığı, Azure [IoT Hub](https://docs.microsoft.com/azure/iot-hub)gibi özellikle IoT endişelerine odaklanan birçok sunucusuz ürünle sonuçlanmıştır. Sunucusuz, aygıt kaydı, ilke zorlama, izleme ve hatta kodun *kenardaki*aygıtlara dağıtılması gibi görevleri otomatikleştirir. Kenar, Internet'e bağlı olan ancak etkin olmayan sensörler ve aktüatörler gibi aygıtları ifade eder.

>[!div class="step-by-step"]
>[Önceki](architecture-approaches.md)
>[Sonraki](serverless-architecture-considerations.md)
