---
title: Sunucusuz uygulamalar için örnek iş senaryoları ve kullanım örnekleri
description: Görüntü işlemeden mobil arka uçlarına ve ETL işlem hattına kadar olan örneklere erişerek, uygulamalı bir yaklaşım ile sunucusuz öğrenin.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: cb761524976125c816aae925f0c369eb8c76e7de
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926479"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Sunucusuz iş senaryoları ve kullanım örnekleri

Sunucusuz uygulamalar için birçok kullanım durumu ve senaryosu vardır. Bu bölümde, farklı senaryoları gösteren örnekler yer almaktadır. Senaryolar ilgili belgelerin ve genel kaynak kodu depolarının bağlantılarını içerir. Bu bölümdeki örnekler, kendi oluşturma ve sunucusuz çözümler uygulamanıza başlamanızı sağlar.

## <a name="analyze-and-archive-images"></a>Görüntüleri çözümleme ve arşivleme

Bu örnek sunucusuz olayları (Event Grid), iş akışlarını (mantıksal uygulama) ve kodu (Azure Işlevleri) gösterir. Ayrıca, görüntü analizi için bu örnekte bilişsel hizmetler ' de başka bir kaynakla nasıl tümleştirileceğini gösterir.

Konsol uygulaması, Web 'deki bir URL bağlantısını geçirmenize olanak sağlar. Uygulama, URL 'YI bir Event Grid iletisi olarak yayımlar. Paralel olarak, sunucusuz bir işlev uygulaması ve bir mantıksal uygulama iletiye abone olur. Sunucusuz işlev uygulaması görüntüyü blob depolamaya seri hale getirir. Ayrıca Azure Tablo depolama alanındaki bilgileri depolar. Meta veriler özgün görüntü URL 'sini ve BLOB görüntüsünün adını depolar. Mantıksal uygulama, görüntüyü çözümlemek ve makine tarafından oluşturulan bir başlık oluşturmak için Özel Görüntü İşleme API 'siyle etkileşime girer. Başlık, meta veri tablosunda depolanır.

![Görüntüleri çözümleme ve arşivleme mimarisi](./media/image-processing-example.png)

Ayrı bir tek sayfalı uygulama (SPA), görüntülerin ve meta verilerin bir listesini almak için sunucusuz bir işlev çağırır. Her görüntü için, arşivden görüntü verilerini teslim eden başka bir işlevi çağırır. Nihai sonuç, otomatik açıklamalı alt yazıların bulunduğu bir galerisidir.

![Otomatik görüntü Galerisi](./media/automated-image-gallery.png)

Mantıksal uygulamayı oluşturmak için tam depoya ve yönergelere buradan ulaşabilirsiniz: [Event Grid tutkalla](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Xamarin. Forms ve işlevleri kullanan platformlar arası mobil istemci

Bkz. Azure Web portalında veya Visual Studio 'da basit sunucusuz Azure Işlevi uygulama. Android, iOS ve Windows üzerinde çalışan Xamarin. Forms ile bir istemci oluşturun. Daha sonra uygulama, sunucu ile mobil istemciler arasında sunucusuz arka uca bir iletişim ortamı olarak JavaScript Nesne Gösterimi (JSON) kullanmak üzere iyileştirilmektedir.

Daha fazla bilgi için bkz [. Xamarin. Forms istemcisiyle basit bir Azure Işlevi uygulama](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Sunucusuz görüntü tanıma ile fotoğraf mozaik oluşturma

Örnek, bir giriş görüntüsünden fotoğraf mozaik oluşturmak için Azure Işlevleri ve Microsoft bilişsel Hizmetler Özel Görüntü İşleme Hizmeti kullanır. Model, görüntüleri tanımak için eğitilen. Bir görüntü karşıya yüklendiğinde, görüntüyü tanır ve Bing ile arar. Özgün görüntü, arama sonuçları kullanılarak yeniden oluşturulur.

![Orlando göz fotoğrafı ve mozaik](./media/orlando-eye-both.png)

Örneğin, modelinize göz önünde olacak şekilde modelleyebilirsiniz. Özel Görüntü İşleme, Orlando gözle bir görüntüyü tanıyacak ve işlev, Bing resim arama sonuçlarından oluşturulan "Orlando göz" için bir fotoğraf mozaik oluşturacaktır.

Daha fazla bilgi için bkz. [Azure işlevleri fotoğraf mozaik Oluşturucu](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Mevcut bir uygulamayı buluta geçirme

Önceki bölümlerde açıklandığı gibi, uygulamanızı şirket içinde barındırmak için N katmanlı bir mimarinin ayraç oluşturma yaygındır. "Olduğu gibi" kaynakları sanal makineler kullanarak geçirmek, bulutun en az riskli yoludur, ancak birçok şirket, uygulamalarını yeniden düzenleme fırsatını tercih etmek üzere tercih edilir. Neyse ki yeniden düzenlemenin "hepsi veya-Nothing" efor olması gerekmez. Aslında, uygulamanızı geçirmek öbek sonra bileşenleri Cloud Native karşılıklarıyla değiştirmek mümkündür.

Uygulama, bir uç noktanın eski şirket içi koddan sunucusuz bir uç noktaya yeniden düzenleme özelliğini etkinleştirmek için Azure Işlevleri 'nin proxy 'lerini kullanır.

![Geçiş mimarisi](./media/migration-architecture.png)

Proxy, bireysel istekleri sunucusuz işlevlere taşınırken yeniden yönlendirmek üzere güncellenen tek bir API uç noktası sağlar.

Geçişin tamamında izlenecek bir video görüntüleyebilirsiniz: [Sunucusuz Azure işlevleri Ile kaldırın ve](https://channel9.msdn.com/Events/Connect/2017/E102)geçiş yapın. Örnek koda erişin: [Kendi uygulamanızı getirin](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Bir CSV dosyasını Ayrıştır ve veritabanına ekleyin

Ayıklama, dönüştürme ve yükleme (ETL), farklı sistemleri tümleştiren ortak bir iş işlevidir. Geleneksel yaklaşımlar genellikle adanmış FTP sunucularının ayarlanmasını ve ardından dosyaları ayrıştırmak ve bunları iş kullanımı için çevirmek üzere zamanlanmış işleri dağıtmaktır. Dosya karşıya yüklenirken bir tetikleyici tetikleyebileceğinden sunucusuz mimari işi kolaylaştırır. Azure Işlevleri, belirli bir soruna odaklanabilecek küçük kod parçalarının ideal kompozisyonu aracılığıyla ETL gibi tackles görevlerini ele alır.

![CSV ayrıştırma sürecini gösteren ekran görüntüsü.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Kaynak kodu ve uygulamalı laboratuvar için bkz. [CSV içeri aktarma Laboratuvarı](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Bağlantıları kısaltın ve ölçümleri izleyin

Kısa bir süre önce bağlantı kısayol araçları, kısa Twitter gönderilerinde URL 'Leri kodlamak için 140 karakter sınırına uyum sağlar. Birçok kullanım için en yaygın olarak izleme-kılavuzlarına for Analytics ' i izlemek çok artmıştır. Bağlantı kısa eğilimi senaryosu, bağlantıları ve rapor ölçümlerini yöneten, tamamen sunucusuz bir uygulamadır.

Azure Işlevleri, uzun URL 'YI yapıştırmanızı ve kısa URL 'Ler oluşturmanızı sağlayan tek sayfalı uygulama (SPA) hizmeti sağlamak için kullanılır. URL 'Ler, kampanyalar (konular) ve ortaums gibi şeyleri (bağlantıların nakledildiği sosyal ağlar gibi) izlemek için etiketlenebilir. Kısa kod, Azure Tablo depolama 'da, değer olarak uzun URL ile anahtar olarak depolanır. Kısa bağlantıya tıkladığınızda, başka bir işlev uzun URL 'yi arar, yeniden yönlendirme gönderir ve olay hakkındaki bilgileri bir sıraya koyar. Başka bir Azure Işlevi kuyruğu işler ve bilgileri Azure Cosmos DB içine koyar.

![Kısa bir mimari bağlantı mimarisi](./media/link-shortener-architecture.png)

Daha sonra, toplanan veriler hakkında Öngörüler toplamak için bir Power BI panosu oluşturabilirsiniz. Arka uçta Application Insights önemli ölçümler sağlar. Telemetri, ortalama kullanıcının yeniden yönlendirileceği süreyi ve Azure Tablo depolama alanına erişmek için geçen süreyi içerir.

![Power BI örneği](./media/power-bi-example.png)

Yönergelerin bulunduğu tam bağlantı kısa bir deposu şurada bulunabilir: [Sunucusuz URL kısaltalayıcı](https://github.com/jeremylikness/serverless-url-shortener). Basitleştirilmiş bir sürüm hakkında buradan bilgi edinebilirsiniz: [Dakikalar içinde sunucusuz .NET uygulamaları Için Azure depolama](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Ping kullanarak cihaz bağlantısını doğrulama

Örnek, bir Azure IoT Hub ve bir Azure Işlevinden oluşur. IoT Hub yeni bir ileti Azure Işlevini tetikler. Sunucusuz kod, aynı ileti içeriğini gönderen cihaza geri gönderir. Projede, çözüm için gereken tüm kod ve dağıtım yapılandırması vardır.

Daha fazla bilgi için bkz. [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).

## <a name="recommended-resources"></a>Önerilen Kaynaklar

* [Azure Işlevleri fotoğraf mozaik Oluşturucu](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [Dakikalar içinde sunucusuz .NET uygulamaları için Azure depolama](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
* [Kendi uygulamanızı getir](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [CSV içeri aktarma Laboratuvarı](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [Olay Kılavuzu tutkalla](https://github.com/JeremyLikness/Event-Grid-Glue)
* [Xamarin. Forms istemcisiyle basit bir Azure Işlevi uygulama](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [Sunucusuz Azure işlevleri ile kaldırın ve geçiş yapın](https://channel9.msdn.com/Events/Connect/2017/E102)
* [Sunucusuz URL kısaltalayıcı](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Önceki](orchestration-patterns.md)İleri
>[](serverless-conclusion.md)
