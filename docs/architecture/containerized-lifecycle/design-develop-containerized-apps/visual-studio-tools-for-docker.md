---
title: Windows üzerinde Docker için Visual Studio Araçları
description: Visual Studio 2017 sürüm 15,7 ve sonraki sürümlerde bulunan Docker araçlarını öğrenin.
ms.date: 08/06/2020
ms.custom: vs-dotnet
ms.openlocfilehash: ae20ebf7c3c27d7f2ebe51c33719b82048f86241
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678933"
---
# <a name="use-docker-tools-in-visual-studio-on-windows"></a>Windows üzerinde Visual Studio 'da Docker Araçları kullanma

Visual Studio 2017 sürüm 15,7 ve üzeri sürümlerde bulunan Docker Araçları kullanılırken geliştirici iş akışı, Visual Studio Code ve Docker CLı (aslında aynı Docker CLı 'yi temel alır) kullanılmasına benzer, ancak çalışmaya başlamak, işlemi kolaylaştırmak ve oluşturma, çalıştırma ve oluşturma görevleri için daha fazla verimlilik sağlar. Ayrıca, `F5` Visual Studio 'daki her zamanki ve anahtarlar aracılığıyla Kapsayıcılarınızı çalıştırabilir ve hata ayıklayabilirsiniz `Ctrl+F5` . Her bir çözümün, kapsayıcıları çözüm düzeyinde aynı dosyada tanımlansa bile, tüm çözümde hata ayıklayabilirsiniz `docker-compose.yml` .

## <a name="configure-your-local-environment"></a>Yerel ortamınızı yapılandırma

En son Docker for Windows sürümleriyle, aşağıdaki başvurularda açıklandığı gibi, kurulum basit olduğundan Docker uygulamalarının geliştirilmesi her zamankinden daha kolay.

> [!TIP]
> Docker for Windows yükleme hakkında daha fazla bilgi için () bölümüne gidin <https://docs.docker.com/docker-for-windows/> .

## <a name="docker-support-in-visual-studio"></a>Visual Studio 'da Docker desteği

Bir projeye ekleyebileceğiniz iki adet Docker desteği düzeyi vardır. ASP.NET Core projelerinde, `Dockerfile` Docker desteğini etkinleştirerek yalnızca projeye bir dosya ekleyebilirsiniz. Bir sonraki düzey, `Dockerfile` Proje (zaten yoksa) ve çözüm düzeyinde bir dosya ekleyen kapsayıcı düzenleme destedir `docker-compose.yml` . Docker Compose aracılığıyla kapsayıcı düzenleme desteği, Visual Studio 2017 sürüm 15,0 ' den 15,7 ' de varsayılan olarak eklenir. Kapsayıcı düzenleme desteği, Visual Studio 2017 sürüm 15,8 veya üzeri bir katılım özelliğidir. Visual Studio 2019 ve üzeri, **Kubernetes/Held** dağıtımını da destekler.

**> Docker desteği ekleme** ve **ekleme > kapsayıcı Orchestrator destek** komutları, Şekil 4-31 ' de gösterildiği gibi **Çözüm Gezgini**içindeki bir ASP.NET Core projesi için proje düğümünün sağ tıklama menüsünde (veya bağlam menüsü) bulunur:

![Visual Studio 'da Docker desteği Ekle menü seçeneği](media/add-docker-support-menu.png)

**Şekil 4-31**. Visual Studio 2019 projesine Docker desteği ekleme

### <a name="add-docker-support"></a>Docker desteği ekleme

Önceki bölümde gösterildiği gibi, mevcut bir uygulamaya Docker desteği ekleme seçeneğinin yanı sıra, Şekil 4-32 ' de gösterildiği gibi **Yeni proje** Iletişim kutusunda **Tamam** ' a tıkladıktan sonra açılan **Yeni ASP.NET Core Web uygulaması** iletişim kutusunda **Docker desteğini etkinleştir** ' i seçerek proje oluşturma sırasında Docker desteğini de etkinleştirebilirsiniz.

![Visual Studio 'da yeni ASP.NET Core Web uygulaması için Docker desteğini etkinleştir](media/enable-docker-support-visual-studio.png)

**Şekil 4-32**. Visual Studio 2019 ' de proje oluşturma sırasında Docker desteğini etkinleştir

Docker desteğini eklediğinizde veya etkinleştirdiğinizde, Visual Studio projeye bir _Dockerfile_ dosyası ekler ve bu, Çözümdeki tüm gerekli projeye yönelik başvuruları içerir.

### <a name="add-container-orchestration-support"></a>Kapsayıcı düzenleme desteği ekle

Çok kapsayıcılı bir çözüm oluşturmak istediğinizde, projelerinize kapsayıcı düzenleme desteği ekleyin. Bu, aynı _Docker-Compose. yıml_ dosyasında tanımlandıklarında bir kapsayıcı grubunu (bir bütün çözüm) aynı anda çalıştırmanıza ve hata ayıklamanıza olanak tanır.

Kapsayıcı düzenleme desteği eklemek için **Çözüm Gezgini**çözüm veya proje düğümüne sağ tıklayın ve **> kapsayıcı düzenleme desteği ekle**' yi seçin. Ardından, kapsayıcıları yönetmek için **Kubernetes/Held** veya **Docker Compose** seçin.

Projenize kapsayıcı düzenleme desteğini ekledikten sonra şekil 4-33 ' de gösterildiği gibi, projeye eklenen bir Dockerfile ve **Çözüm Gezgini**çözüme eklenen bir **Docker-Compose** klasörü görürsünüz:

![Visual Studio 'da Çözüm Gezgini Docker dosyaları](media/docker-support-solution-explorer.png)

**Şekil 4-33**. Visual Studio 2019 ' de Çözüm Gezgini Docker dosyaları

_Docker-Compose. yml_ zaten varsa, Visual Studio buna yalnızca gerekli olan yapılandırma kodu satırlarını ekler.

## <a name="configure-docker-tools"></a>Docker araçlarını yapılandırma

Ana menüden **araçlar > seçenekler**' i seçin ve **kapsayıcı araçları > ayarlar**' ı genişletin. Kapsayıcı araçları ayarları görüntülenir.

![Visual Studio Docker Araçları seçenekleri, üç sayfa gösteriliyor: genel, tek proje ve Docker Compose, makale metnindeki ayrıntılar.](media/visual-studio-docker-tools-options.png)

**Şekil 4-34**. Docker Araçları seçenekleri

Aşağıdaki tablo, bu seçeneklerin nasıl ayarlanacağına karar vermenize yardımcı olur.

| Sayfa/ayar                                |  Varsayılan ayar   | Description                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------------------------------- | :----------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Genel sayfa**                            |
| Gerekirse Docker Desktop 'ı yükler            |     Bana sor      |
| Gerekirse Docker Desktop 'ı Başlat              |     Bana sor      |
| SSL sertifikası ASP.NET Core güven          |     Bana sor      | Localhost SSL sertifikası güvenilir (ile) olarak işaretlenmemişse `dotnet dev-certs https --trust` , projenizi her çalıştırdığınızda Visual Studio sorar.                                                                                                                                                                                                                                                    |
| **Tek proje sayfası**                     |
| Proje açıkken gerekli Docker görüntülerini çekme |        Doğru        | Projeyi çalıştırırken daha yüksek performans için, Visual Studio arka planda bir Docker çekme işlemi başlatır, böylece kodunuzu çalıştırmaya hazırsanız görüntü zaten indirilmeye devam eder ve indirme sürecinde olur. Yalnızca projeler ve tarama kodu yüklüyorsanız, gerek duymadığınız kapsayıcı görüntülerini indirmeyi önlemek için bunu kapatabilirsiniz. Bu, açık proje Kullanıcı deneyimini yavaşlatabilir. |
| Proje yükünde güncelleştirilmiş Docker görüntülerini çekme  | .NET Core projeleri | Proje açıkken en son güncelleştirmeleri almak için mevcut görüntülere yönelik güncelleştirmeleri çekin. Bu, açık proje Kullanıcı deneyimini yavaşlatabilir.                                                                                                                                                                                                                                                                                          |
| Proje kapatıldığında kapsayıcıları kaldır          |        Doğru        | Projeyi kapatmada Temizleme bu, proje Kullanıcı deneyimini kapatır, ancak genellikle hızlıdır.                                                                                                                                                                                                                                                                                                            |
| Açık proje üzerinde kapsayıcıları Çalıştır              |        Doğru        | Projeyi çalıştırırken daha yüksek performans için, Visual Studio Çözümdeki tüm kapsayıcıları başlatacak. Bu, açık proje Kullanıcı deneyimini yavaşlatabilir.                                                                                                                                                                                                                                                        |
| **Docker Compose**                          |                    | Docker Compose sayfası, tek proje sayfasıyla aynı ayarları içerir, ancak bunlar çok Kapsayıcılı çözümler için geçerlidir.                                                                                                                                                                                                                                                                                           |

> [!WARNING]
> Localhost SSL sertifikasına güvenilmiyor ve seçeneğini **hiçbir zaman**olarak AYARLARSANıZ, HTTPS Web istekleri uygulamanızdaki veya hizmetinizdeki çalışma zamanında başarısız olabilir. Bu durumda, bir kez daha önce **sorulması** için değeri yeniden, daha iyi bir şekilde ayarlamak için komutunu kullanarak geliştirme makinenizdeki sertifikalara güvenin `dotnet dev-certs https --trust` .

> [!TIP]
> Hizmet uygulamasıyla ilgili daha fazla ayrıntı ve Docker için Visual Studio Araçları kullanımı için aşağıdaki makaleleri okuyun:
>
> Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama: <https://docs.microsoft.com/visualstudio/containers/edit-and-refresh>
>
> Visual Studio 'Yu kullanarak bir kapsayıcı kayıt defterine ASP.NET kapsayıcısını dağıtma: <https://docs.microsoft.com/visualstudio/containers/hosting-web-apps-in-docker>

> [!div class="step-by-step"]
> [Önceki](docker-apps-inner-loop-workflow.md) 
>  [Sonraki](set-up-windows-containers-with-powershell.md)
