---
title: İş senaryolarını örnekleyin ve sunucusuz uygulamalar için kılıfları kullanın
description: Görüntü işlemeden mobil arka uçlara ve ETL ardışık hatlara kadar değişen örneklere erişerek uygulamalı bir yaklaşımla sunucusuz öğrenin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76787889"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Sunucusuz iş senaryoları ve kullanım örnekleri

Sunucusuz uygulamalar için birçok kullanım örnekleri ve senaryolar vardır. Bu bölümde, farklı senaryoları gösteren örnekler içerir. Senaryolar, ilgili belgelere ve genel kaynak kodu depolarına bağlantılar içerir. Bu bölümdeki örnekler, kendi binanıza ve sunucusuz çözümleri uygulamaya başlamanızı sağlar.

## <a name="analyze-and-archive-images"></a>Görüntüleri analiz ve arşivleme

Bu örnek, sunucusuz olayları (Olay Izgarası), iş akışlarını (Mantık Uygulaması) ve kodu (Azure İşlevleri) gösterir. Ayrıca nasıl başka bir kaynak ile entegre gösterir, bu durumda görüntü analizi için Bilişsel Hizmetler.

Konsol uygulaması, web'deki bir URL'ye bağlantı aktarmanızı sağlar. Uygulama URL'yi olay ızgara iletisi olarak yayımlar. Buna paralel olarak, sunucusuz bir işlev uygulaması ve bir mantık uygulaması iletiyi abone eder. Sunucusuz işlev uygulaması, görüntüyü blob depolamaalanına serileştirir. Ayrıca bilgileri Azure Tablo Depolama'da da saklar. Meta veriler orijinal resim URL'sini ve blob resminin adını depolar. Mantık uygulaması, görüntüyü analiz etmek ve makine tarafından oluşturulan bir başlık oluşturmak için Özel Vizyon API'si ile etkileşime girer. Resim yazısı meta veri tablosunda depolanır.

![Görüntü mimarisini analiz et ve arşivle](./media/image-processing-example.png)

Ayrı bir tek sayfa uygulaması (SPA), görüntülerin ve meta verilerin listesini almak için sunucusuz bir işlev çağırır. Her görüntü için, arşivdeki görüntü verilerini sağlayan başka bir işlev çağırır. Nihai sonuç, otomatik altyazıları olan bir galeridir.

![Otomatik resim galerisi](./media/automated-image-gallery.png)

Mantık uygulaması oluşturmak için tam deposu ve talimatları burada mevcuttur: [Olay ızgara tutkal](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Xamarin.Forms ve işlevleri kullanarak çapraz platform mobil istemci

Azure Web Portalı'nda veya Visual Studio'da basit bir sunucusuz Azure İşi'nin nasıl uygulanacağını görün. Android, iOS ve Windows'da çalışan Xamarin.Forms ile bir istemci oluşturun. Uygulama daha sonra sunucu ve sunucusuz arka uç ile mobil istemciler arasında bir iletişim aracı olarak JavaScript Nesne Gösterimi (JSON) kullanmak için rafine edilir.

Daha fazla bilgi için bkz: [Xamarin.Forms istemcisi ile basit bir Azure İşlevi uygulama.](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Sunucusuz görüntü tanıma özelliğine sahip bir fotoğraf mozaiği oluşturma

Örnek, giriş görüntüsünden bir fotoğraf mozaiği oluşturmak için Azure İşlevlerini ve Microsoft Bilişsel Hizmetler Özel Görme Hizmeti'ni kullanır. Model görüntüleri tanımak için eğitildi. Bir resim yüklendiğinde, görüntüyü tanır ve Bing ile arama lar. Orijinal görüntü, arama sonuçları kullanılarak yeniden oluşturulur.

![Orlando göz fotoğrafı ve mozaik](./media/orlando-eye-both.png)

Örneğin, modelinizi Orlando Eye gibi Orlando simge yapıları ile eğitebilirsiniz. Özel Vizyon Orlando Göz bir görüntü tanıyacak, ve işlevi için Bing görüntü arama sonuçlarıoluşan bir fotoğraf mozaik yaratacak "Orlando Eye."

Daha fazla bilgi için Azure [Fonksiyonları fotoğraf mozaik jeneratörüne](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)bakın.

## <a name="migrate-an-existing-application-to-the-cloud"></a>Varolan bir uygulamayı buluta geçirme

Önceki bölümlerde tartışıldığı gibi, başvurunuzu şirket içinde barındırmak için n-tier mimarisini benimsemek yaygındır. Sanal makineleri kullanarak kaynakları "olduğu gibi" geçirmek buluta giden en az riskli yol olsa da, birçok şirket uygulamalarını yeniden düzenleme fırsatını kullanmayı tercih eder. Neyse ki, refactoring bir "ya hep ya hiç" çaba olmak zorunda değildir. Aslında, uygulamanızı geçirip parçaları bulut yerel benzerleriyle parça parça değiştirmek mümkündür.

Uygulama, eski şirket içi koddan sunucusuz bir bitiş noktasına bir bitiş noktası nı yeniden düzenlemeyi etkinleştirmek için Azure İşlevlerinin yakınlık özelliğini kullanır.

![Geçiş mimarisi](./media/migration-architecture.png)

Proxy, tek tek istekleri sunucusuz işlevlere taşındıklarında yeniden yönlendirmek için güncelleştirilen tek bir API bitiş noktası sağlar.

Tüm geçiş boyunca yürüyen bir videoyu görüntüleyebilirsiniz: [Sunucusuz Azure işlevleriyle kaldırma ve kaydırma.](https://channel9.msdn.com/Events/Connect/2017/E102) Örnek koda erişin: [Kendi uygulamanızı getirin.](https://github.com/JeremyLikness/bring-own-app-connect-17)

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>CSV dosyalarını ayrıştın ve veritabanına ekleme

Ayıklama, Dönüştürme ve Yükleme (ETL), farklı sistemleri entegre eden ortak bir iş fonksiyonudur. Geleneksel yaklaşımlar genellikle özel FTP sunucuları ayarlamayı ve zamanlanmış işleri dosyaları ayrıştırmak ve iş amaçlı çevirmek için dağıtmayı içerir. Sunucusuz mimari, dosya yüklendiğinde bir tetikleyici ateş edebileceğinden işi kolaylaştırır. Azure İşlevler, belirli bir soruna odaklanan küçük kod parçalarını ideal bileşimi aracılığıyla ETL gibi görevleri ele alır.

![CSV ayrıştma işlemini gösteren ekran görüntüsü.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Kaynak kodu ve uygulamalı laboratuvar için [CSV alma laboratuvarına](https://github.com/JeremyLikness/azure-fn-file-process-hol)bakın.

## <a name="shorten-links-and-track-metrics"></a>Bağlantıları kısaltma ve ölçümleri izleme

Bağlantı kısaltma araçları başlangıçta 140 karakter sınırını karşılamak için kısa twitter gönderilerinde URL'lerin kodlanmasına yardımcı oldu. Bunlar, en yaygın olarak analitik için tıklamaları izlemek için çeşitli kullanımları kapsayacak şekilde büyüdü. Bağlantı kısaltıcı senaryosu, bağlantıları ve rapor ölçümlerini yöneten tamamen sunucusuz bir uygulamadır.

Azure İşlevleri, uzun URL'yi yapıştırıp kısa URL'ler oluşturmanıza olanak tanıyan tek sayfalı bir Uygulama (SPA) sunmak için kullanılır. URL'ler kampanyalar (konular) ve ortamlar (bağlantıların yayınlandığı sosyal ağlar gibi) gibi şeyleri izlemek için etiketlenir. Kısa kod, anahtar olarak Azure Tablo Depolama'da, değeri uzun URL ile depolanır. Kısa bağlantıyı tıklattığınızda, başka bir işlev uzun URL'yi arar, yeniden yönlendirme gönderir ve olay la ilgili bilgileri sıraya yerleştirir. Başka bir Azure İşlevi sırayı işler ve bilgileri Azure Cosmos DB'ye yerleştirir.

![Bağlantı kısaltıcı mimarisi](./media/link-shortener-architecture.png)

Daha sonra toplanan veriler hakkında bilgi toplamak için bir Power BI panosu oluşturabilirsiniz. Arka uçta, Application Insights önemli ölçümler sağlar. Telemetri, ortalama bir kullanıcının yeniden yönlendirmesinin ne kadar sürdüğünü ve Azure Tablo Depolama'ya erişme nin ne kadar sürdüğünü içerir.

![Güç BI örneği](./media/power-bi-example.png)

Talimatlar ile tam bağlantı kısaltıcı deposu burada mevcuttur: [Serverless URL kısaltıcı](https://github.com/jeremylikness/serverless-url-shortener). Burada basitleştirilmiş bir sürüm hakkında bilgi edinebilirsiniz: [Sunucusuz .NET uygulamaları için Azure Depolama dakika içinde](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Ping kullanarak aygıt bağlantısını doğrulama

Örnek, bir Azure IoT Hub'ı ve bir Azure İşlevi'nden oluşur. IoT Hub'daki yeni bir ileti Azure İşi'ni tetikler. Sunucusuz kod, aynı ileti içeriğini gönderen aygıta geri gönderir. Proje, çözüm için gereken tüm kod ve dağıtım yapılandırmasına sahiptir.

Daha fazla bilgi için [Azure IoT Hub ping'ine](https://github.com/Azure-Samples/iot-hub-node-ping)bakın.

## <a name="recommended-resources"></a>Önerilen kaynaklar

- [Azure Fonksiyonları fotoğraf mozaik jeneratör](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Azure IoT Hub ping](https://github.com/Azure-Samples/iot-hub-node-ping)
- [Dakikalar içinde sunucusuz .NET uygulamaları için Azure Depolama](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Kendi uygulamanızı getirin](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [CSV ithalat laboratuvarı](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Olay ızgara tutkal](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Xamarin.Forms istemcisi ile basit bir Azure İşi uygulama](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Sunucusuz Azure işlevleriyle kaldırma ve kaydırma](https://channel9.msdn.com/Events/Connect/2017/E102)
- [Sunucusuz URL kısaltıcı](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Önceki](orchestration-patterns.md)
>[Sonraki](serverless-conclusion.md)
