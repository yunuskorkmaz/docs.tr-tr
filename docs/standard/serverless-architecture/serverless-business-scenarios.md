---
title: Örnek İş senaryoları ve sunucusuz uygulamalar için kullanım örnekleri
description: Mobil arka uçlar ve ETL işlem hatları için gelen görüntü işleme aralığı örnekleri erişerek pratik bir yaklaşım ile sunucusuz öğrenin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: adc4e1f3249cd72c423430ad4cb5dbb8eea8baf9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638822"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Sunucusuz iş senaryoları ve kullanım örnekleri

Birçok kullanım örnekleri ve senaryoları için sunucusuz uygulamalar vardır. Bu bölüm, farklı senaryolar gösteren örnekleri içerir. Senaryolar ilgili belgeler ve ortak kaynak kodu depoları bağlantılar içerir. Bu bölümdeki örnekler, oluşturma ve sunucusuz çözümler uygulama kendi kullanmaya başlamak etkinleştirin.

## <a name="analyze-and-archive-images"></a>Analiz ve görüntüleri arşiv

Bu örnek, sunucusuz olayları (Event Grid), iş akışları (mantıksal uygulama) ve kod (Azure işlevleri) gösterir. Ayrıca başka bir kaynak, görüntü analizi için büyük/küçük harf bu Bilişsel hizmetler ile tümleştirme işlemini de gösterir.

Bir konsol uygulaması web üzerinde bir URL için bir bağlantı geçirilecek sağlar. Uygulama URL'sini bir event grid iletisi yayımlar. Paralel olarak bir sunucusuz işlev uygulaması ve bir mantıksal uygulama iletiyi abone olun. Sunucusuz bir işlev uygulaması, blob depolama alanına görüntü serileştirir. Ayrıca Azure tablo Depolama'da bilgileri depolar. Meta veriler, özgün resim URL'si ve blob görüntünün adını depolar. Mantıksal uygulama resmi çözümleme ve makine tarafından oluşturulan açıklamalı alt yazı oluşturma için özel görüntü işleme API'si ile etkileşimde bulunur. Açıklamalı alt yazı, meta veri tablosunda depolanır.

![Analiz ve görüntü mimari arşiv](./media/image-processing-example.png)

Ayrı bir tek sayfalı uygulama (SPA) bir listesini görüntüler ve meta verileri almak için sunucusuz bir işlev çağırır. Her bir görüntü için görüntü verilerini arşivden sunan başka bir işlevi çağırır. Otomatik açıklamalı alt yazılı bir galeri son sonucudur.

![Otomatik görüntü Galerisi](./media/automated-image-gallery.png)

Mantıksal uygulama oluşturmak için yönergeleri ve tam depo şuradan ulaşılabilir: [Event grid Birleştirici](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Platformlar arası mobil istemci Xamarin.Forms ve işlevlerini kullanma

Azure Web Portalı'nda veya Visual Studio'da basit bir sunucusuz Azure işlevi nasıl göreceksiniz. Bir Android, iOS ve Windows üzerinde çalıştırılan Xamarin.Forms istemci oluşturun. Uygulama, ardından JavaScript nesne gösterimi (JSON) sunucusu ve sunucusuz bir arka ucu ile mobil istemciler arasında bir iletişim ortamı olarak kullanmak için iyileştirilmiştir.

Daha fazla bilgi için [basit bir Azure işlevi ile bir Xamarin.Forms istemci uygulama](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Fotoğraf Mozaik sunucusuz görüntü tanıma ile oluşturma

Örnek Giriş bir görüntüden bir fotoğraf Mozaik oluşturmak için Azure işlevleri ve Microsoft Bilişsel hizmetler Custom Vision Service'ı kullanır. Görüntüleri tanımak için modeli eğitilir. Görüntü karşıya yüklendiğinde, görüntünün tanır ve Bing ile arar. Özgün görüntü arama sonuçlarını kullanarak yeniden.

![Orlando göz fotoğraf ve Mozaik](./media/orlando-eye-both.png)

Örneğin, modelinizi Orlando göz gibi Orlando yer işareti eğitebilirsiniz. Özel görüntü işleme Orlando göz görüntüsü algılar ve işlevi bir fotoğraf Mozaik Bing resim arama sonuçlarının oluşan "Orlando gözünden bakın." oluşturur

Daha fazla bilgi için [Azure işlevleri fotoğraf Mozaik Oluşturucu](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Mevcut bir uygulamayı buluta geçirme

Önceki bölümlerde açıklandığı gibi uygulama şirket içi barındırmak için N katmanlı bir mimari benimsemek için yaygındır. "Olduğu gibi" kaynakları geçirme olsa da sanal makineleri kullanarak bulut az riskli yolu, birçok şirket uygulamalarını yeniden fırsatı kullanmak seçin. Neyse ki, yeniden düzenleme "zorlamadan" çaba olmak zorunda değildir. Aslında, uygulamanızı geçişi ardından parça parça bileşenleri ile bulut yerel karşılıklarını değiştirmek mümkündür.

Uygulama, eski şirket içi koddan bir uç nokta sunucusuz bir uç noktasına yeniden düzenlemeyi etkinleştirmek için Azure işlevleri proxy'leri özelliğini kullanır.

![Geçiş mimarisi](./media/migration-architecture.png)

Proxy istekleri ayrı ayrı sunucusuz işlevler taşındı yönlendirecek şekilde güncelleştirilir tek bir API uç noktası sağlar.

Tüm geçiş anlatan bir videoyu görüntüleyebilirsiniz: [Lift- and -shift ile sunucusuz Azure işlevleri](https://channel9.msdn.com/Events/Connect/2017/E102). Örnek kod erişimi: [Kendi uygulamanızı taşıyın](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Bir CSV dosyasını ayrıştırabilir ve bir veritabanına ekleme

Ayıklama, dönüştürme ve yükleme (ETL), farklı sistemleri tümleştiren bir ortak iş işlevidir. Geleneksel yaklaşım genellikle ayrılmış FTP sunucuları kurma sonra dosyalarını ayrıştırmak ve kurumsal kullanım için çevirmek için zamanlanmış işleri dağıtma içerir. Sunucusuz mimari dosya yüklendiğinde bir tetikleyiciyi harekete geçirmek çünkü iş kolaylaştırır. Azure işlevleri Associates görevleri, belirli bir soruna odaklanmak küçük kod parçalarını ideal, oluşumunu aracılığıyla ETL ister.

![İşlem ayrıştırma csv gösteren ekran görüntüsü.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Kaynak kodu ve uygulamalı bir laboratuvara için bkz: [CSV içe Laboratuvar](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Bağlantılar kısaltın ve ölçümleri izleme

Özgün URL'leri kısa kodlama Yardım bağlantısı kısaltmayı araçları 140 karakter sınırı uyum sağlamak için gönderiler twitter. Geçişli tıklatma analiz için izlemek için çeşitli kullanımları, en yaygın olarak kapsayacak şekilde büyüdü. Bağlama kısaltıcı senaryosu, bağlantıları yönetir ve ölçümleri raporları tamamen sunucusuz bir uygulamadır.

Azure işlevleri, uzun URL'yi yapıştırın ve kısa URL üretmek için sağlayan bir tek sayfa uygulama (SPA) sunmak için kullanılır. URL'leri kampanyaları (konuları) ve (örneğin, bağlantıları gönderilen değerler sosyal ağlar) ortamları gibi izlemek için etiketlenir. Kısa bir kod değeri olarak uzun URL'siyle anahtarı Azure tablo Depolama'da depolanır. Kısa bağlantıya tıkladığınızda, başka bir işlev uzun URL'sini arar, bir yeniden yönlendirme gönderir ve olayla ilgili bilgileri bir sırada yerleştirir. Başka bir Azure işlevi, sıra işler ve bilgileri Azure Cosmos DB içine yerleştirir.

![Bağlantı kısaltıcı mimarisi](./media/link-shortener-architecture.png)

Ardından, toplanan verileri hakkında bilgiler toplamak için bir Power BI panosu oluşturabilirsiniz. Arka uçta Application Insights önemli ölçümleri sağlar. Telemetri ne yönlendirmek için ortalama kullanıcı sürdüğünü ve Azure tablo depolamaya erişmek için ne kadar sürer içerir.

![Power BI örnek](./media/power-bi-example.png)

Tam bağlantı kısaltıcı deposuyla yönergeleri burada kullanılabilir: [Sunucusuz URL kısaltıcı](https://github.com/jeremylikness/serverless-url-shortener). Bir Basitleştirilmiş sürümden burada okuyabilirsiniz: [Dakikalar içinde sunucusuz .NET uygulamaları için Azure depolama](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Bir ping işlemi kullanarak cihaz bağlantısını doğrulayın

Örnek, bir Azure IOT hub'ı ve bir Azure işlevi oluşur. IOT Hub'ında yeni bir ileti Azure işlevi tetikler. Sunucusuz kod aynı ileti içeriği, gönderilen cihaza geri gönderir. Proje, çözüm için gereken tüm kod ve dağıtım yapılandırması vardır.

Daha fazla bilgi için [Azure IOT hub'ı ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).

## <a name="recommended-resources"></a>Önerilen kaynaklar

* [Azure işlevleri fotoğraf Mozaik Oluşturucusu](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IOT hub'ı ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [Dakikalar içinde sunucusuz .NET uygulamaları için Azure depolama](https://blogs.msdn.microsoft.com/webdev/2018/01/25/azure-storage-for-serverless-net-apps-in-minutes/)
* [Kendi uygulamanızı taşıyın](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [CSV Import Laboratuvar](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [Event grid Birleştirici](https://github.com/JeremyLikness/Event-Grid-Glue)
* [Basit bir Azure işlevi ile bir Xamarin.Forms istemci uygulama](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [Lift- and -shift ile sunucusuz Azure işlevleri](https://channel9.msdn.com/Events/Connect/2017/E102)
* [Sunucusuz URL kısaltıcı](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Önceki](orchestration-patterns.md)
>[İleri](serverless-conclusion.md)
