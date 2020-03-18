---
title: Windows'da Docker için Görsel Stüdyo Araçları
description: Visual Studio 2017 sürüm 15.7 ve sonraki sürümlerde sunulan Docker araçlarını tanıyın.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295810"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Windows'da Visual Studio 2017'de Docker Araçlarını Kullanma

Visual Studio 2017 sürüm 15.7 ve sonrası sürüm15.7 ve sonraki sürümlerinde yer alan Docker Tools'u kullanırken geliştirici iş akışı Visual Studio Code ve Docker CLI 'yi kullanmaya benzer (aslında aynı Docker CLI'ye dayanır), ancak başlamak daha kolaydır, süreci kolaylaştırır ve oluşturma, çalıştırma ve oluşturma görevleri için daha fazla üretkenlik sağlar. Ayrıca Visual Studio'dan her zamanki `F5` ve `Ctrl+F5` tuşlarla kaplarınızı çalıştırıp hata ayıklayabilir. Kapsayıcıları çözüm düzeyinde aynı `docker-compose.yml` dosyada tanımlanmışsa, tüm bir çözümü hata ayıklayabilirsiniz.

## <a name="configure-your-local-environment"></a>Yerel ortamınızı yapılandırın

Docker for Windows'un en son sürümleriyle Docker uygulamalarını geliştirmek her zamankinden daha kolaydır, çünkü kurulum aşağıdaki başvurularda açıklandığı gibi basittir.

> [!TIP]
> Windows için Docker'ı yükleme hakkında<https://docs.docker.com/docker-for-windows/>daha fazla bilgi edinmek için ( ).

## <a name="docker-support-in-visual-studio-2017"></a>Visual Studio 2017'de Docker desteği

Bir projeye ekleyebileceğiniz iki Docker desteği düzeyi vardır. ASP.NET Core projelerinde Docker desteğini `Dockerfile` etkinleştirerek projeye bir dosya ekleyebilirsiniz. Bir sonraki düzey, projeye (zaten `Dockerfile` yoksa) bir dosya ve çözüm düzeyinde bir `docker-compose.yml` dosya ekleyen kapsayıcı düzenleme desteğidir. Docker Compose aracılığıyla konteyner orkestrasyon desteği, Visual Studio 2017 sürümleri 15.0 ile 15.7 arasında varsayılan olarak eklenir. Konteyner orkestrasyon desteği Visual Studio 2017 sürümleri 15.8 veya daha sonra bir opt-in özelliğidir. Sürüm 15.8 daha sonra destek Docker Compose ve Hizmet Kumaş.

Şekil 4-31'de gösterildiği **gibi, Çözüm Gezgini**>'ndeki bir ASP.NET Çekirdek projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsünde) > Docker Desteği ve Ekle > **Docker Desteği** ve **Ekle** komutları bulunur:

![Visual Studio'da Docker Destek menüsü ekle seçeneği](./media/add-docker-support-menu.png)

**Şekil 4-31**. Visual Studio 2017 projesine Docker desteği ekleme

### <a name="add-docker-support"></a>Docker desteği ekleme

**Çözüm Gezgini'nde**Docker Desteği **Ekle'yi** > seçerek varolan bir ASP.NET Core projesine Docker**desteği** ekleyebilirsiniz. Şekil 4-32'de gösterildiği gibi **Yeni Proje** iletişim kutusunda **Tamam'ı** tıklattıktan sonra açılan Yeni ASP.NET Çekirdek **Web Uygulaması** iletişim kutusunda Docker **Desteğini Etkinleştir'i** seçerek proje oluşturma sırasında Docker desteğini de etkinleştirebilirsiniz.

![Visual Studio'da yeni ASP.NET Core web uygulaması için Docker Desteği etkinleştirin](./media/enable-docker-support-visual-studio.png)

**Şekil 4-32**. Visual Studio 2017'de proje oluşturma sırasında Docker desteğini etkinleştirin

Docker desteği eklediğinizde veya etkinleştirdiğinizde, Visual Studio projeye bir *Dockerfile* dosyası ekler.

> [!NOTE]
> Şekil 4-33'te gösterildiği gibi ASP.NET bir proje (.NET Core projesi değil,.NET Core projesi) için proje oluşturma sırasında Docker Compose desteğini etkinleştirdiğinizde, konteyner orkestrasyonu desteği de eklenir.

![ASP.NET bir proje için Docker'ın destek oluşturmasını etkinleştirme](media/enable-docker-compose-support.png)

**Şekil 4-33**. Visual Studio 2017'de ASP.NET projesi için Docker Compose desteğini etkinleştirme

### <a name="add-container-orchestration-support"></a>Konteyner düzenleme desteği ekle

Çok kapsayıcılı bir çözüm oluşturmak istediğinizde, projelerinize konteyner düzenleme desteği ekleyin. Bu, aynı *docker-compose.yml* dosyasında tanımlanmışsa, bir kapsayıcı grubunu (tam çözüm) aynı anda çalıştırmanızı ve hata ayıklamanızı sağlar.

Kapsayıcı orkestrasyon desteği eklemek **için, Solution Explorer'daki**çözüm veya proje düğümüne sağ tıklayın ve **Kapsayıcı Düzenleme Desteği > ekle'yi**seçin. Ardından, konteynerleri yönetmek için **Docker Compose** veya **Service Fabric'i** seçin.

Projenize kapsayıcı düzenleme desteği ekledikten sonra, projeye bir Dockerfile ve Şekil 4-34'te gösterildiği gibi **Solution Explorer'da**çözüme eklenen **docker-compose** klasörü görürsünüz:

![Visual Studio'da Solution Explorer'da Docker dosyaları](media/docker-support-solution-explorer.png)

**Şekil 4-34**. Visual Studio 2017'de Solution Explorer'da Docker dosyaları

*Docker-compose.yml* zaten varsa, Visual Studio sadece yapılandırma kodu gerekli satırları ekler.

## <a name="configure-docker-tools"></a>Docker araçlarını yapılandırma

Ana menüden **Araçlar > Seçenekleri'ni**seçin ve Kapsayıcı Araçları **> Ayarları'nı**genişletin. Kapsayıcı araçları ayarları görüntülenir.

![Visual Studio Docker araçları seçenekleri, gösteriliyor: Proje yükünde gerekli Docker görüntülerini otomatik olarak çekin, arka planda kapları otomatik olarak başlatın, çözüm kapanışında kapları otomatik olarak öldürün ve SSL sertifikasına güvenmek için istekte bulunmayın.](./media/visual-studio-docker-tools-options.png)

**Şekil 4-35**. Docker Araçları Seçenekleri

Aşağıdaki tablo, bu seçenekleri nasıl ayarlayacağınınıza karar vermenize yardımcı olabilir.

| Adı | Varsayılan Ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Proje yükünde gerekli Docker görüntülerini otomatik olarak çekin | Açık | Docker Oluştur | Proje yüklerken daha yüksek performans için Visual Studio arka planda docker çekme işlemine başlar, böylece kodunuzu çalıştırmaya hazır olduğunuzda görüntü zaten indirilir veya indirme işleminde olur. Projeleri ve gözatma kodunu yüklüyorsanız, ihtiyacınız olmayan kapsayıcı görüntülerini indirmemek için bunu kapatabilirsiniz. |
| Arka planda kapsayıcıları otomatik olarak başlatın | Açık | Docker Oluştur | Yine artan performans için Visual Studio, kapsayıcınızı inşa edip çalıştırdığınızda ses montajlarına hazır bir kapsayıcı oluşturur. Kapsayıcınızın ne zaman oluşturulduğunu denetlemek istiyorsanız, bunu kapatın. |
| Çözelti kapatmada otomatik olarak kapları öldürmek | Açık | Docker Oluştur | Çözümünüzü kapattıktan veya Visual Studio'yu kapattıktan sonra çalışmaya devam etmesini istiyorsanız bunu kapatın. |
| Localhost SSL sertifikasına güvenmek için istekte yok | Kapalı | ASP.NET Core 2.2 projeleri | Localhost SSL sertifikasına güvenilmezse, bu onay kutusu işaretlenmedikçe Visual Studio projenizi her çalıştırdığınızda ister. |

> [!WARNING]
> Localhost SSL sertifikasına güvenilmezse ve istek isteni bastırmak için kutuyu işaretleseniz, HTTPS web istekleri uygulamanızda veya hizmetinizde çalışma zamanında başarısız olabilir. Bu durumda, Onay **kutusunu işaretlenin,** projenizi çalıştırın ve istek anında güven belirtin.

> [!TIP]
> Docker için Visual Studio Tools hizmetlerinin uygulanması ve kullanımı hakkında daha fazla bilgi için aşağıdaki makaleleri okuyun:
>
>Uygulamaları yerel bir Docker konteynerinde hata ayıklama:<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Visual Studio'ASP.NET bir kapsayıcıyı kullanarak konteyner kayıt defterine dağıtın:<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Önceki](docker-apps-inner-loop-workflow.md)
>[Sonraki](set-up-windows-containers-with-powershell.md)
