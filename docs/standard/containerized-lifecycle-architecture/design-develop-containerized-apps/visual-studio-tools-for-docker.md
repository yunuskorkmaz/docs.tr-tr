---
title: Windows üzerinde Docker için Visual Studio Araçları
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: c58c680c6500bc3b9adec50e18c26af3329122c9
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086394"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>(Windows için Visual Studio) Docker için Visual Studio araçlarını kullanma

Docker geliştirme iş akışı için Visual Studio Araçları, Visual Studio Code ve Docker CLI'yı kullanırken iş akışına benzerdir. Aslında, aynı Docker CLI'yı dayanır ancak başlamak kolaydır, bu süreci kolaylaştırır ve daha yüksek üretkenlik sağlar, derleme için çalıştırın ve Görevler oluşturun. Yürütme ve kapsayıcılarınızı gibi basit eylemleri aracılığıyla hata ayıklama **F5** ve **Ctrl**+**F5**. Çalıştırın ve tek bir kapsayıcı hata ayıklama ek olarak isteğe bağlı bir kapsayıcı düzenleme desteği, çalıştırın ve bir grup kapsayıcının (tam çözüm) aynı anda hata ayıklama.

> [!NOTE]
> Bu makale Windows üzerinde Visual Studio ve Visual Studio değil, Mac için geçerlidir

## <a name="configure-your-local-environment"></a>Yerel ortamınızı yapılandırma

Docker için Windows en son sürümlerinde ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), basit kurulum Docker uygulamaları geliştirmek kolaylaştırır.

Docker desteği, Visual Studio 2017'de dahildir. Visual Studio 2017'ı buradan indirin: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Visual Studio 2017'de Docker araçları kullanın

Bir projeye ekleyebilirsiniz Docker desteği iki düzeyi vardır. .NET Core web uygulaması projelerinde yalnızca ekleyebilirsiniz bir *Dockerfile* Docker desteği etkinleştirerek projeye dosya. İleri düzey ekler kapsayıcı düzenleme desteği olan bir *Dockerfile* (zaten yoksa) projeye ve *docker-compose.yml* çözüm düzeyinde dosya. Docker Compose, aracılığıyla kapsayıcı düzenleme desteği, varsayılan olarak Visual Studio 2017 sürüm 15.7 veya önceki eklenir. Kapsayıcı düzenleme desteği Tercihli özellik Visual Studio 2017 sürümlerinde 15,8 ya da daha sonra bu durumda Docker Compose ve Service Fabric desteklenir.

**Ekle** > **Docker desteği** ve **Ekle** > **kapsayıcı düzenleme desteği** komutlar bir web uygulaması projesi için proje düğümünü sağ tıklama menüsünü (veya bağlam menüsü) bulunan **Çözüm Gezgini**, Şekil 4-26 gösterildiği gibi:

![Visual Studio'da Docker desteği menü seçeneği ekleyin](media/add-docker-support-menu.png)

Şekil 4-26: Visual Studio 2017 projeye Docker desteği ekleme

### <a name="add-docker-support"></a>Docker desteği Ekle

Docker desteği seçerek mevcut bir .NET Core web uygulaması projesine ekleyebilirsiniz **Ekle** > **Docker desteği** içinde **Çözüm Gezgini**. Seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz **Docker desteği etkinleştirme** içinde **yeni ASP.NET Core Web uygulaması** tıkladığınızda açılan iletişim kutusunda **Tamam** içinde **yeni proje** iletişim kutusu, Şekil 4-27'de gösterildiği gibi.

![Visual Studio'da yeni bir ASP.NET Core web uygulaması için Docker desteğini etkinleştir](./media/enable-docker-support-visual-studio.png)

Visual Studio 2017'de proje oluşturma sırasında Şekil 4-27: Docker desteğini etkinleştir

Visual Studio ekleyin ya da Docker desteğini etkinleştirmek ekler bir *Dockerfile* projeye dosya.

> [!NOTE]
> Bilgisayarınızda Docker Compose desteği proje oluştururken bir .NET Framework web uygulaması projesi (olmayan bir .NET Core web uygulaması projesi) için Şekil 4-28 gösterildiği etkinleştirdiğinizde, kapsayıcı düzenleme desteği de eklenir.
>
> ![Docker'ı etkinleştirme desteği için bir .NET Framework web uygulaması projesi oluşturma](media/enable-docker-compose-support.png)

> Şekil 4-28: Visual Studio 2017'de .NET Framework web uygulaması projesi üzerinde Docker Compose desteği etkinleştirme

### <a name="add-container-orchestration-support"></a>Kapsayıcı düzenleme desteği ekleme

Çok kapsayıcılı bir çözüm oluşturmak istediğinizde, kapsayıcı düzenleme desteği, projenize ekleyin. Bu, çalıştırma ve aynı tanımlanan bir grup kapsayıcının (tam çözüm) aynı anda hata ayıklaması sağlar *docker-compose.yml* dosya.

Kapsayıcı düzenleme desteği eklemek için çözümü veya proje düğümünü sağ **Çözüm Gezgini**ve **Ekle** > **kapsayıcı düzenlemedesteği**. Ardından **Docker Compose** veya **Service Fabric** kapsayıcıları yönetmek için.

Kapsayıcı düzenleme desteği projenize ekledikten sonra projeye eklenen bir Dockerfile bakın ve **docker-compose** çözümüne eklenmiş klasör **Çözüm Gezgini**, Şekil 4-29 gösterildiği gibi:

![Visual Studio'daki Çözüm Gezgini'nde docker dosyaları](media/docker-support-solution-explorer.png)

Şekil 4-29: Docker dosyaları Çözüm Gezgini'nde Visual Studio 2017

Varsa *docker-compose.yml* zaten var, Visual Studio yalnızca ekler gerekli yapılandırma kod satırı için.

## <a name="configure-docker-tools"></a>Docker araçları yapılandırma

Ana menüden **Araçları** > **seçenekleri**, genişletin **kapsayıcı Araçları** > **ayarları**. Kapsayıcı Araçları ayarları görüntülenir.

![](./media/visual-studio-docker-tools-options.png)

Şekil 4-30: seçenekleri Docker araçları

Aşağıdaki tabloda, bu seçenekleri ayarlamak nasıl karar vermenize yardımcı olabilir.

| Ad | Varsayılan ayar | Uygulandığı öğe: | Açıklama |
| -----|:---------------:|:----------:| ----------- |
| Otomatik olarak proje yükünde gerekli Docker görüntülerini çekme | Açık | Docker Compose | Proje yüklenirken daha yüksek performans için Visual Studio Docker çekme işlemi arka planda böylece kodunuzu çalıştırmak hazır olduğunuzda, görüntü zaten yüklenene veya yükleme sürecinde başlar. Yalnızca projeler yükleniyor ve kod gözatma ise, ihtiyacınız olmayan kapsayıcı görüntülerini yüklenmesini önlemek için kapatabilirsiniz. |
| Kapsayıcıları arka planda otomatik olarak Başlat | Açık | Docker Compose | Yeniden performansı artırmak için Visual Studio kapsayıcı ile birim başlatmalar, derleme ve kapsayıcı çalıştırma için hazır oluşturur. Kapsayıcı oluşturulduğunda denetlemek istiyorsanız, kapatır. |
| KILL çözümdeki kapsayıcıları otomatik olarak Kapat | Açık | Docker Compose | Kapsayıcıları çözümünüzün çözümün kapatılması veya Visual Studio kapatıldıktan sonra çalışmaya devam etmesini istiyorsanız kapatır. |
| İçin localhost SSL sertifikasına güvenme istemi yapma | Kapalı | ASP.NET Core 2.1 projeleri | Localhost SSL sertifikasına güvenilir değilse, bu onay kutusu işaretli değilse, projenizi her çalıştırdığınızda Visual Studio ister. |

> [!WARNING]
> Ardından localhost SSL sertifikasına güvenilmiyor ve isteyen bastırmak için kutuyu işaretleyin, HTTPS isteklerine uygulamanızı veya hizmetinizi çalışma zamanında başarısız olabilir. Bu durumda, onay kutusunu temizleyin **sorma** onay kutusunu projenizi çalıştırmak ve güven isteminde gösterir.

**Daha fazla bilgi:** Hizmetleri uygulaması ve Docker için Visual Studio Araçları'nın kullanımı hakkında daha ayrıntılı bilgi için bu makaleleri okuyun:

Derleme, hata ayıklama, güncelleştirme ve uygulamaları yerel bir Docker kapsayıcısında Yenile: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Bir ASP.NET Core Docker kapsayıcısını bir kapsayıcı kayıt defterine dağıtın: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Önceki](docker-apps-inner-loop-workflow.md)
[İleri](set-up-windows-containers-with-powershell.md)