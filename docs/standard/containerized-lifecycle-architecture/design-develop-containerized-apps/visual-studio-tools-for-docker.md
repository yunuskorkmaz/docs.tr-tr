---
title: Windows üzerinde Docker için Visual Studio Araçları
description: Visual Studio 2017 sürüm 15.7 ve üzeri Docker araçları tanışın.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644692"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Windows üzerinde Visual Studio 2017'de Docker araçları kullanın

Visual Studio 2017 sürüm 15.7 ve üzeri, Docker araçları kullanırken, geliştirici iş akışını Visual Studio Code ve Docker CLI'yı kullanmaya benzer (aslında, aynı Docker CLI'yı temel), ancak başlamak kolaydır, bu süreci kolaylaştırır ve Daha fazla verimlilik sağlar, derleme için çalıştırın ve Görevler oluşturun. Ayrıca çalıştırmak ve kapsayıcılarınızı normal aracılığıyla hata ayıklama `F5` ve `Ctrl+F5` Visual Studio'dan anahtarları. Kapsayıcılarında aynı tanımlanmışsa, tüm çözüm bile ayıklayabilirsiniz `docker-compose.yml` çözüm düzeyinde dosya.

## <a name="configure-your-local-environment"></a>Yerel ortamınızı yapılandırma

Docker için Windows en son sürümleri ile Kurulumu aşağıdaki başvuruları açıklandığı gibi basit, çünkü Docker uygulamaları geliştirmek için her zamankinden daha kolaydır.

> [!TIP]
> Docker için Windows yükleme hakkında daha fazla bilgi için şuraya gidin (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Visual Studio 2017'de docker desteği

Bir projeye ekleyebilirsiniz Docker desteği iki düzeyi vardır. ASP.NET Core projelerinde, yalnızca ekleyebilirsiniz bir `Dockerfile` Docker desteği etkinleştirerek projeye dosya. İleri düzey ekler kapsayıcı düzenleme desteği olan bir `Dockerfile` (zaten yoksa) projeye ve `docker-compose.yml` çözüm düzeyinde dosya. Docker Compose, aracılığıyla kapsayıcı düzenleme desteği, varsayılan olarak Visual Studio 2017 sürüm 15.0 için 15.7 eklenir. Kapsayıcı düzenleme desteği bir katılım 15,8 veya sonraki bir sürümü Visual Studio 2017 sürüm özelliğidir. Sürüm 15,8 daha sonra bir Docker Compose ve Service Fabric desteği.

**Ekle > Docker desteği** ve **Ekle > kapsayıcı Düzenleyicisi desteği** komutları bulunan bir ASP.NET Core projesi için proje düğümünü sağ tıklama menüsünü (veya bağlam menüsü)  **Çözüm Gezgini**, Şekil 4-31'de gösterildiği gibi:

![Visual Studio'da Docker desteği menü seçeneği ekleyin](./media/add-docker-support-menu.png)

**Şekil 4-31**. Visual Studio 2017 projeye Docker desteği ekleme

### <a name="add-docker-support"></a>Docker desteği Ekle

Docker desteği seçerek mevcut bir ASP.NET Core projesine ekleyebilirsiniz **Ekle** > **Docker desteği** içinde **Çözüm Gezgini**. Seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz **Docker desteği etkinleştirme** içinde **yeni ASP.NET Core Web uygulaması** tıkladığınızda açılan iletişim kutusunda **Tamam** içinde **yeni proje** iletişim kutusu, Şekil 4-32 gösterildiği gibi.

![Visual Studio'da yeni bir ASP.NET Core web uygulaması için Docker desteğini etkinleştir](./media/enable-docker-support-visual-studio.png)

**Şekil 4-32**. Visual Studio 2017'de proje oluşturma sırasında Docker desteğini etkinleştir

Visual Studio ekleyin ya da Docker desteğini etkinleştirmek ekler bir *Dockerfile* projeye dosya.

> [!NOTE]
> Bilgisayarınızda Docker Compose desteği için bir ASP.NET projesi (.NET Framework, .NET Core projesi) proje oluşturma sırasında Şekil 4-33 gösterildiği etkinleştirdiğinizde, kapsayıcı düzenleme desteği de eklenir.

![Docker'ı etkinleştirme desteği için bir ASP.NET projesi oluşturma](media/enable-docker-compose-support.png)

**Şekil 4-33**. Visual Studio 2017'te ASP.NET projesi Docker Compose desteği etkinleştirme

### <a name="add-container-orchestration-support"></a>Kapsayıcı düzenleme desteği ekleme

Çok kapsayıcılı bir çözüm oluşturmak istediğinizde, kapsayıcı düzenleme desteği, projenize ekleyin. Bu, çalıştırma ve aynı tanımlanan bir grup kapsayıcının (tam çözüm) aynı anda hata ayıklaması sağlar *docker-compose.yml* dosya.

Kapsayıcı düzenleme desteği eklemek için çözümü veya proje düğümünü sağ **Çözüm Gezgini**ve **Ekle > kapsayıcı düzenleme desteği**. Ardından **Docker Compose** veya **Service Fabric** kapsayıcıları yönetmek için.

Kapsayıcı düzenleme desteği projenize ekledikten sonra projeye eklenen bir Dockerfile bakın ve **docker-compose** çözümüne eklenmiş klasör **Çözüm Gezgini**, Şekil 4-34 gösterildiği gibi:

![Visual Studio'daki Çözüm Gezgini'nde docker dosyaları](media/docker-support-solution-explorer.png)

**Şekil 4-34**. Çözüm Gezgini'nde Visual Studio 2017'de docker dosyaları

Varsa *docker-compose.yml* zaten var, Visual Studio yalnızca ekler gerekli yapılandırma kod satırı için.

## <a name="configure-docker-tools"></a>Docker araçları yapılandırma

Ana menüden **Araçlar > Seçenekler**, genişletin **kapsayıcı araçları > ayarları**. Kapsayıcı Araçları ayarları görüntülenir.

![Visual Studio Docker seçenekleri gösteren araçları: Otomatik olarak proje yükünde gerekli Docker görüntülerini çekme, kapsayıcıları arka planda otomatik olarak Başlat, Kapat çözümdeki kapsayıcıları otomatik olarak sonlandırmak ve SSL sertifikasına güvenme istemi yapma.](./media/visual-studio-docker-tools-options.png)

**Şekil 4-35**. Docker araçları seçenekleri

Aşağıdaki tabloda, bu seçenekleri ayarlamak nasıl karar vermenize yardımcı olabilir.

| Ad | Varsayılan ayar | Uygulanan Öğe | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Otomatik olarak proje yükünde gerekli Docker görüntülerini çekme | Açık | Docker Compose | Proje yüklenirken performansı artırmak için Visual Studio Docker çekme işlemi arka planda böylece kodunuzu çalıştırmak hazır olduğunuzda, görüntü zaten yüklenene veya yükleme sürecinde başlar. Yalnızca projeler yükleniyor ve kod gözatma ise, ihtiyacınız olmayan kapsayıcı görüntülerini yüklenmesini önlemek için kapatabilirsiniz. |
| Kapsayıcıları arka planda otomatik olarak Başlat | Açık | Docker Compose | Yeniden performansı artırmak için Visual Studio kapsayıcı ile birim başlatmalar, derleme ve kapsayıcı çalıştırma için hazır oluşturur. Kapsayıcı oluşturulduğunda denetlemek istiyorsanız, kapatır. |
| KILL çözümdeki kapsayıcıları otomatik olarak Kapat | Açık | Docker Compose | Kapsayıcıları çözümünüzün çözümün kapatılması veya Visual Studio kapatıldıktan sonra çalışmaya devam etmesini istiyorsanız kapatır. |
| İçin localhost SSL sertifikasına güvenme istemi yapma | Kapalı | 2.2 ASP.NET Core projeleri | Localhost SSL sertifikasına güvenilir değilse, bu onay kutusu işaretli değilse, projenizi her çalıştırdığınızda Visual Studio ister. |

> [!WARNING]
> Ardından localhost SSL sertifikasına güvenilmiyor ve isteyen bastırmak için kutuyu işaretleyin, HTTPS isteklerine uygulamanızı veya hizmetinizi çalışma zamanında başarısız olabilir. Bu durumda, onay kutusunu temizleyin **sorma** onay kutusunu projenizi çalıştırmak ve güven isteminde gösterir.

> [!TIP]
> Uygulama hizmetleri ve Docker için Visual Studio Araçları'nın kullanımı hakkında daha ayrıntılı bilgi için bu makaleleri okuyun:
>
>Yerel bir Docker kapsayıcısı uygulamalarında hata ayıklama: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>ASP.NET kapsayıcısını Visual Studio kullanarak bir kapsayıcı kayıt defterine dağıtın: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Önceki](docker-apps-inner-loop-workflow.md)
>[İleri](set-up-windows-containers-with-powershell.md)
