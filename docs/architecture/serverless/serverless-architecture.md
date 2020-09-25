---
title: Sunucusuz mimari-sunucusuz uygulamalar
description: Web uygulamaları, mobil ve IoT gibi sunucusuz mimariler tarafından desteklenen çeşitli mimarilerin ve uygulamaların araştırmasına yönelik araştırma.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: f7d80ce3957c2ad90a67ae6ba1fc2786af30fcc1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171721"
---
# <a name="serverless-architecture"></a>Sunucusuz mimari

[Sunucusuz](https://azure.com/serverless) mimarilerin kullanılmasına yönelik birçok yaklaşım vardır. Bu bölümde sunucusuz 'i tümleştiren ortak mimarilerin örnekleri incelenmektedir. Ayrıca, daha fazla zorluk oluşturabilecek veya sunucusuz uygularken ek bir dikkat gerektiren sorunlar ele alınmaktadır. Son olarak, çeşitli sunucusuz kullanım durumlarını gösteren çeşitli tasarım örnekleri verilmiştir.

Sunucusuz konaklar genellikle sunucusuz örnekleri yönetmek için mevcut bir kapsayıcı tabanlı veya PaaS katmanını kullanır. Örneğin, Azure Işlevleri [Azure App Service](/azure/app-service/)tabanlıdır. App Service, örnekleri ölçeklendirmek ve Azure Işlevleri kodunu yürüten çalışma zamanını yönetmek için kullanılır. Windows tabanlı işlevlerde, ana bilgisayar PaaS olarak çalışır ve .NET çalışma zamanının ölçeğini ölçeklendirir. Linux tabanlı işlevlerde, ana bilgisayar kapsayıcılardan yararlanır.

![Azure Işlevleri mimarisi](./media/azure-functions-architecture.png)

WebJobs Core, işlev için bir yürütme bağlamı sağlar. Dil çalışma zamanı betikleri çalıştırır, kitaplıkları yürütür ve hedef dilin çerçevesini barındırır. Örneğin, Node.js JavaScript işlevlerini çalıştırmak için kullanılır ve .NET Framework C# işlevlerini çalıştırmak için kullanılır. Bu bölümde daha sonra dil ve platform seçenekleri hakkında daha fazla bilgi edineceksiniz.

Bazı projeler, sunucusuz 'e "hepsini bir" yaklaşımı alma avantajına sahip olabilir. Mikro hizmetleri yoğun bir şekilde kullanan uygulamalar, sunucusuz teknoloji kullanan tüm mikro hizmetleri uygulayabilir. Uygulamaların çoğunluğu bir N katmanlı tasarımı izleyerek ve bileşenler modüler ve bağımsız olarak ölçeklendirilebilir olduğundan anlamlı bileşenler için sunucusuz kullanılarak karma hale getirir. Bu senaryolar hakkında fikir sahibi olmak için, bu bölümde sunucusuz kullanan bazı yaygın mimari örnekleri gösterilmektedir.

## <a name="full-serverless-back-end"></a>Tam sunucusuz arka uç

Tam sunucusuz arka ucu, özellikle yeni veya "yeşil alan" uygulamaları oluştururken çeşitli türlerde senaryolar için idealdir. API 'lerin büyük bir yüzey alanına sahip bir uygulama, her API 'YI sunucusuz bir işlev olarak uygulamalarından yararlanabilir. Mikro hizmet mimarisini temel alan uygulamalar, tam sunucusuz arka uç olarak uygulanabilecek başka bir örnektir. Mikro hizmetler birbirleriyle çeşitli protokoller üzerinden iletişim kurar. Belirli senaryolar şunlardır:

- API tabanlı SaaS ürünleri (örnek: finansal ödemeler işlemcisi).
- İleti temelli uygulamalar (örnek: cihaz izleme çözümü).
- Hizmetler arasındaki tümleştirmeye odaklanan uygulamalar (örnek: hava yolu kayıt uygulaması).
- Düzenli aralıklarla çalışan süreçler (örnek: Zamanlayıcı tabanlı veritabanı temizleme).
- Veri dönüşümüne odaklanan uygulamalar (örnek: içeri aktarma işlemi dosya yükleme tarafından tetiklendi).
- Dönüştürme ve yükleme (ETL) süreçlerini ayıklayın.

Bu belgede daha sonra ele alınan başka, daha belirgin kullanım durumları vardır.

## <a name="monoliths-and-starving-the-beast"></a>Tek tek altı ve "Beast 'yi kanıtlama"

Yaygın bir sınama, mevcut bir tek parçalı uygulamayı buluta geçirmektir. En az riskli yaklaşım, tamamen sanal makinelere "yükseltme ve kaydırma" kullanmaktır. Birçok yükseltme, kendi kod tabanlarını modernleştirin için bir fırsat olarak geçişi kullanmayı tercih eder. Geçişe pratik bir yaklaşım, "Beast 'yi kanıtlama" olarak adlandırılır. Bu senaryoda, mimariden "olduğu gibi", ile başlamak için geçirilir. Ardından, seçilen hizmetler modernlanmış. Bazı durumlarda hizmetin imzası orijinaliyle aynıdır: yalnızca bir işlev olarak barındırılır. İstemciler, tek bir uç nokta yerine yeni hizmeti kullanacak şekilde güncelleştirilir. Geçici olarak, veritabanı çoğaltma gibi adımlar, mikro hizmetleri, işlemler hala tek bir işlem tarafından işlense bile kendi depolama alanını barındırmak üzere etkinleştirir. Sonuç olarak, tüm istemciler yeni hizmetlere geçirilir. Tek tek, tüm işlevler değiştirilene kadar "başlatılıyor" (hizmetleri artık çağrılmayacaktır). Sunucusuz ve proxy 'ler birleşimi, bu geçişin çoğunu kolaylaştırabilir.

![Sunucusuz mimariden geçişi](./media/serverless-monolith-migration.png)

Bu yaklaşım hakkında daha fazla bilgi edinmek için videoyu izleyin: [sunucusuz Azure işlevleri ile Uygulamanızı buluta taşıyın](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Web uygulamaları

Web Apps, sunucusuz uygulamalar için harika adaylardır. Günümüzde Web Apps 'e yönelik iki yaygın yaklaşım vardır: sunucu odaklı ve istemci odaklı (tek sayfalı uygulama veya SPA gibi). Sunucu tabanlı Web uygulamaları, genellikle Web Kullanıcı arabirimini işlemek için API çağrıları yayınlamak üzere bir ara yazılım katmanı kullanır. SPA uygulamaları doğrudan tarayıcıdan REST API çağrısı yapar. Her iki senaryoda da sunucusuz, gerekli iş mantığını sağlayarak ara yazılım veya REST API isteğine uyum sağlayabilir. Yaygın bir mimari, hafif bir statik Web sunucusu kurmak için kullanılır. Tek sayfalı uygulama (SPA), HTML, CSS, JavaScript ve diğer tarayıcı varlıklarını sunar. Web uygulaması daha sonra mikro hizmetler arka ucuna bağlanır.

## <a name="mobile-back-ends"></a>Mobil arka uçlar

Sunucusuz uygulamaların olay odaklı paradigması, bunları mobil arka uçlar olarak ideal hale getirir. Mobil cihaz olayları tetikler ve istekleri karşılamak için sunucusuz kod yürütülür. Sunucusuz bir modelden yararlanmak, geliştiricilerin tam bir uygulama güncelleştirmesi dağıtmak zorunda kalmadan iş mantığını geliştirmesini sağlar. Sunucusuz yaklaşım ayrıca ekiplerin uç noktaları paylaşmasını ve paralel olarak çalışmasını sağlar.

Mobil geliştiriciler sunucu tarafında uzman olmadan iş mantığı oluşturabilir. Geleneksel olarak, şirket içi hizmetlere bağlanan mobil uygulamalar. Sunucu platformunu ve programlama paradigmasını anlamak için gereken hizmet katmanını oluşturma. Geliştiriciler, sunucuları sağlamak ve bunları uygun şekilde yapılandırmak için işlemlerle çalıştık. Bazen bir dağıtım işlem hattı oluşturmak için günler veya hatta haftalar harcanmıştı. Bu güçlüklerin hepsi sunucusuz tarafından ele alınır.

Sunucu tarafı bağımlılıklarını sunucusuz soyutlar ve geliştiricinin iş mantığına odaklanmalarını sağlar. Örneğin, JavaScript çerçevesini kullanarak uygulamalar oluşturan bir mobil geliştirici, JavaScript ile sunucusuz işlevler de oluşturabilir. Sunucusuz ana bilgisayar işletim sistemini, kodu barındırmak için bir Node.js örneğini, paket bağımlılıklarını ve daha fazlasını yönetir. Geliştirici basit bir giriş kümesi ve çıktılar için standart bir şablon sağlamıştır. Daha sonra iş mantığını oluşturmaya ve test etmeye odaklanabilirler. Bu nedenle, yeni platformları öğrenmeniz veya "sunucu tarafı geliştiricisi" olması gerekmeden mobil uygulama için arka uç mantığı oluşturmak üzere mevcut becerileri kullanabiliyor.

![Sunucusuz mobil arka uç](./media/serverless-mobile-backend.png)

Çoğu bulut sağlayıcısı, mobil geliştirme yaşam döngüsünün tamamını basitleştiren mobil tabanlı sunucusuz ürünler sunar. Ürünler, verileri kalıcı hale getirmek, DevOps sorunlarını işlemek, bulut tabanlı derlemeler ve test çerçeveleri sağlamak ve geliştiricinin tercih ettiği dili kullanarak iş süreçlerine komut dosyası vermek için veritabanlarının sağlanması işlemini otomatikleştirebilir. Mobil merkezli sunucusuz bir yaklaşımdan sonra işlem kolaylaştırılmasına devam edebilirsiniz. Sunucusuz, mobil arka uç için sunucuların sağlanması, yapılandırılması ve sürdürülmesi için inanılmaz yükü ortadan kaldırır.

## <a name="internet-of-things-iot"></a>Nesnelerin İnterneti (IoT)

IoT, birbirine bağlı fiziksel nesneleri ifade eder. Bunlar bazen "bağlı cihazlar" veya "akıllı cihazlar" olarak anırlar. Araba ve havalandırma makinelerinden her şey bağlı olabilir ve stoktan sıcaklık ve nem gibi algılayıcı verilerine kadar bilgi gönderebilir. , IoT, izleme ve otomasyon aracılığıyla iş süreci iyileştirmeleri sağlar. IoT verileri, büyük bir ambardaki kliizini düzenlemek ya da tedarik zinciri aracılığıyla envanteri izlemek için kullanılabilir. IoT, her ne kadar yasal sıvı duygusu ve duman algılandığında yangın departmanı çağırabilirler.

Cihazların ve bilgilerin yerleşik hacmi genellikle iletileri yönlendirmek ve işlemek için olay odaklı bir mimariyi belirler. Sunucusuz, çeşitli nedenlerle ideal bir çözümdür:

- Cihazların ve verilerin hacmi arttıkça ölçeklendirmeyi izin vermez.
- Yeni cihazları ve algılayıcıları desteklemek için yeni uç noktalar eklemeye uyum sağlar.
- Geliştiricilerin sistemin tamamını dağıtmaya gerek kalmadan belirli bir cihaz için iş mantığını güncelleştirebilmesi için bağımsız sürüm oluşturmayı kolaylaştırır.
- Dayanıklılık ve daha az kapalı kalma süresi.

IoT 'nin kullanılabilirliği, [Azure IoT Hub](/azure/iot-hub)gibi IoT kaygılarıyla ilgili olarak çok sayıda sunucusuz ürüne neden oldu. Sunucusuz, cihaz kaydı, ilke zorlama, izleme ve hatta kodun *kenarda*cihazlara dağıtılması gibi görevleri otomatikleştirir. Sınır, Internet 'e bağlı ancak etkin bir parçası değil, algılayıcı ve erişim gibi cihazlara başvurur.

>[!div class="step-by-step"]
>[Önceki](architecture-approaches.md) 
> [Sonraki](serverless-architecture-considerations.md)
