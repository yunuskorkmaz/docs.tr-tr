---
title: Windows üzerinde Docker için Visual Studio Araçları
description: Visual Studio 2017 sürüm 15,7 ve sonraki sürümlerde bulunan Docker araçlarını öğrenin.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295810"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Windows üzerinde Visual Studio 2017 ' de Docker Araçları 'nı kullanma

Visual Studio 2017 sürüm 15,7 ve üzeri sürümlerde bulunan Docker Araçları kullanılırken geliştirici iş akışı, Visual Studio Code ve Docker CLı kullanmaya benzerdir (aslında aynı Docker CLı 'yi temel alır), ancak başlamak daha kolay hale gelir, böylece işlemi basitleştirir ve oluşturma, çalıştırma ve oluşturma görevleri için daha fazla verimlilik sağlar. Ayrıca, Visual Studio 'daki her zamanki `F5` ve `Ctrl+F5` anahtarlar aracılığıyla Kapsayıcılarınızı çalıştırabilir ve hata ayıklayabilirsiniz. Her bir çözümün, kapsayıcıları çözüm düzeyinde aynı `docker-compose.yml` dosyada tanımlansa bile, tüm çözümde hata ayıklayabilirsiniz.

## <a name="configure-your-local-environment"></a>Yerel ortamınızı yapılandırma

En son Docker for Windows sürümleriyle, aşağıdaki başvurularda açıklandığı gibi, kurulum basit olduğundan Docker uygulamalarının geliştirilmesi her zamankinden daha kolay.

> [!TIP]
> Docker for Windows yükleme hakkında daha fazla bilgi için (<https://docs.docker.com/docker-for-windows/>) bölümüne gidin.

## <a name="docker-support-in-visual-studio-2017"></a>Visual Studio 2017 'de Docker desteği

Bir projeye ekleyebileceğiniz iki adet Docker desteği düzeyi vardır. ASP.NET Core projelerinde, Docker desteğini etkinleştirerek yalnızca projeye `Dockerfile` bir dosya ekleyebilirsiniz. Bir sonraki düzey, proje (zaten yoksa) `Dockerfile` `docker-compose.yml` ve çözüm düzeyinde bir dosya ekleyen kapsayıcı düzenleme destedir. Docker Compose aracılığıyla kapsayıcı düzenleme desteği, Visual Studio 2017 sürüm 15,0 ' den 15,7 ' de varsayılan olarak eklenir. Kapsayıcı düzenleme desteği, Visual Studio 2017 sürüm 15,8 veya üzeri bir katılım özelliğidir. Sürüm 15,8, daha sonra Docker Compose ve Service Fabric destek.

**> Docker desteği ekleme** ve **ekleme > kapsayıcı Orchestrator destek** komutları, Şekil 4-31 ' de gösterildiği gibi **Çözüm Gezgini**içindeki bir ASP.NET Core projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsü) bulunur:

![Visual Studio 'da Docker desteği Ekle menü seçeneği](./media/add-docker-support-menu.png)

**Şekil 4-31**. Visual Studio 2017 projesine Docker desteği ekleme

### <a name="add-docker-support"></a>Docker desteği ekle

**Çözüm Gezgini**' de**Docker desteği** **Ekle** > ' ye tıklayarak mevcut bir ASP.NET Core projesine Docker desteği ekleyebilirsiniz. Ayrıca, şekil oluşturma sırasında Docker desteğini, **Yeni proje** Iletişim kutusunda **Tamam** ' a tıkladıktan sonra açılan **Yeni ASP.NET Core Web uygulaması** iletişim kutusunda **Docker desteğini etkinleştir** ' i seçerek etkinleştirebilirsiniz. 4-32.

![Visual Studio 'da yeni ASP.NET Core Web uygulaması için Docker desteğini etkinleştir](./media/enable-docker-support-visual-studio.png)

**Şekil 4-32**. Visual Studio 2017 ' de proje oluşturma sırasında Docker desteğini etkinleştir

Docker desteğini eklediğinizde veya etkinleştirdiğinizde, Visual Studio projeye bir *Dockerfile* dosyası ekler.

> [!NOTE]
> Şekil 4-33 ' de gösterildiği gibi, bir ASP.NET projesi .NET Framework (.NET Core projesi değil) için proje oluşturma sırasında Docker Compose desteğini etkinleştirdiğinizde, kapsayıcı düzenleme desteği de eklenir.

![Bir ASP.NET projesi için Docker Compose desteğini etkinleştir](media/enable-docker-compose-support.png)

**Şekil 4-33**. Visual Studio 2017 ' de bir ASP.NET projesi için Docker Compose desteğini etkinleştirme

### <a name="add-container-orchestration-support"></a>Kapsayıcı düzenleme desteği ekle

Çok kapsayıcılı bir çözüm oluşturmak istediğinizde, projelerinize kapsayıcı düzenleme desteği ekleyin. Bu, aynı *Docker-Compose. yıml* dosyasında tanımlandıklarında bir kapsayıcı grubunu (bir bütün çözüm) aynı anda çalıştırmanıza ve hata ayıklamanıza olanak tanır.

Kapsayıcı düzenleme desteği eklemek için **Çözüm Gezgini**çözüm veya proje düğümüne sağ tıklayın ve **> kapsayıcı düzenleme desteği ekle**' yi seçin. Sonra kapsayıcıları yönetmek için **Docker Compose** veya **Service Fabric** öğesini seçin.

Projenize kapsayıcı düzenleme desteğini ekledikten sonra şekil 4-34 ' de gösterildiği gibi, projeye eklenen bir Dockerfile ve **Çözüm Gezgini**çözüme eklenen bir **Docker-Compose** klasörü görürsünüz:

![Visual Studio 'da Çözüm Gezgini Docker dosyaları](media/docker-support-solution-explorer.png)

**Şekil 4-34**. Visual Studio 2017 ' de Çözüm Gezgini Docker dosyaları

*Docker-Compose. yml* zaten varsa, Visual Studio buna yalnızca gerekli olan yapılandırma kodu satırlarını ekler.

## <a name="configure-docker-tools"></a>Docker araçlarını yapılandırma

Ana menüden **araçlar > seçenekler**' i seçin ve **kapsayıcı araçları > Ayarlar**' ı genişletin. Kapsayıcı araçları ayarları görüntülenir.

![Visual Studio Docker Araçları seçenekleri, şunu gösterir: Gerekli Docker görüntülerini proje yüküne otomatik olarak çekme, kapsayıcıları arka planda otomatik olarak Başlat, çözüm kapatıldığında kapsayıcıları otomatik olarak sonlandır ve SSL sertifikası için sorma.](./media/visual-studio-docker-tools-options.png)

**Şekil 4-35**. Docker Araçları seçenekleri

Aşağıdaki tablo, bu seçeneklerin nasıl ayarlanacağına karar vermenize yardımcı olur.

| Ad | Varsayılan ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Gerekli Docker görüntülerini proje yüküne otomatik olarak çekme | Açık | Docker Compose | Projeleri yüklerken daha yüksek performans için, Visual Studio arka planda bir Docker çekme işlemi başlatır, böylece kodunuzu çalıştırmaya hazırsanız görüntü zaten indirilmeye devam eder ve indirme sürecinde olur. Yalnızca projeler ve tarama kodu yüklüyorsanız, gerek duymadığınız kapsayıcı görüntülerini indirmeyi önlemek için bunu kapatabilirsiniz. |
| Kapsayıcıları arka planda otomatik olarak Başlat | Açık | Docker Compose | Daha yüksek performans için, Visual Studio, kapsayıcınızı oluşturup çalıştırdığınızda, toplu takmaya hazırlama ile bir kapsayıcı oluşturur. Kapsayıcının ne zaman oluşturulduğunu denetlemek isterseniz, bunu kapatın. |
| Çözüm kapatıldığında kapsayıcıları otomatik olarak Sonlandır | Açık | Docker Compose | Çözümünüzü kapattıktan veya Visual Studio 'Yu kapattıktan sonra çözümünüz için kapsayıcıların çalışmaya devam etmesini istiyorsanız bunu kapatın. |
| Localhost SSL sertifikası için güvenme isteme | Kapalı | ASP.NET Core 2,2 projeleri | Localhost SSL sertifikası güvenilir değilse, bu onay kutusu işaretlenmediği takdirde, Visual Studio projenizi her çalıştırdığınızda sorar. |

> [!WARNING]
> Localhost SSL sertifikasına güvenilmiyorsa ve sorulmayı önlemek için kutuyu görmüyorsanız, HTTPS Web istekleri uygulamanızdaki veya hizmetinizdeki çalışma zamanında başarısız olabilir. Bu **durumda, sorma onay kutusunun** işaretini kaldırın, projenizi çalıştırın ve sorulduğunda güveni belirtin.

> [!TIP]
> Hizmet uygulamasıyla ilgili daha fazla ayrıntı ve Docker için Visual Studio Araçları kullanımı için aşağıdaki makaleleri okuyun:
>
>Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama:<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Visual Studio 'Yu kullanarak bir kapsayıcı kayıt defterine ASP.NET kapsayıcısını dağıtma:<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Önceki](docker-apps-inner-loop-workflow.md)İleri
>[](set-up-windows-containers-with-powershell.md)
