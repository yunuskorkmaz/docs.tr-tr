---
title: Windows üzerinde Docker için Visual Studio Araçları
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235721"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>(Windows için Visual Studio) Docker için Visual Studio araçlarını kullanma

Docker Geliştirici iş akışı için Visual Studio Araçları, Visual Studio Code ve Docker CLI'yı (aynı Docker CLI'yı temel alır) kullanmaya benzer. Visual Studio Araçları için Docker kullanmaya başlamak daha da kolay hale getirir, bu süreci kolaylaştırır ve derleme için daha yüksek üretkenlik sağlar çalıştırın ve Görevler oluşturun. Yürütme ve kapsayıcılarınızı gibi basit eylemleri aracılığıyla hata ayıklama **F5** ve **Ctrl**+**F5**.

> [!NOTE]
> Bu makale Windows üzerinde Visual Studio ve Visual Studio değil, Mac için geçerlidir

## <a name="configure-your-local-environment"></a>Yerel ortamınızı yapılandırma

Docker için Windows en son sürümlerinde ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), basit kurulum Docker uygulamaları geliştirmek kolaylaştırır.

Docker desteği, Visual Studio 2017'de dahildir. Visual Studio 2017'ı buradan indirin: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Visual Studio 2017'de Docker araçları kullanın

Bir projeye ekleyebilirsiniz Docker desteği iki düzeyi vardır. .NET Core web uygulaması projelerinde yalnızca ekleyebilirsiniz bir *Dockerfile* Docker desteği etkinleştirerek projeye dosya. İleri düzey ekler kapsayıcı Düzenleyicisi desteği olan bir *Dockerfile* (zaten yoksa) projeye ve *docker-compose.yml* çözüm düzeyinde dosya.

**Ekle** > **Docker desteği** ve **Ekle** > **kapsayıcı Düzenleyicisi desteği** komutlar bir web uygulaması projesi için proje düğümünü sağ tıklama menüsünü (veya bağlam menüsü) bulunan **Çözüm Gezgini**, Şekil 4-26 gösterildiği gibi:

![Visual Studio'da Docker desteği menü seçeneği ekleyin](media/add-docker-support-menu.png)

Şekil 4-26: Visual Studio 2017 projeye Docker desteği ekleme

### <a name="add-docker-support"></a>Docker desteği Ekle

Docker desteği seçerek mevcut bir .NET Core web uygulaması projesine ekleyebilirsiniz **Ekle** > **Docker desteği** içinde **Çözüm Gezgini**. Seçerek proje oluşturma sırasında Docker desteğini etkinleştirebilirsiniz **Docker desteği etkinleştirme** içinde **yeni ASP.NET Core Web uygulaması** tıkladığınızda açılan iletişim kutusunda **Tamam** içinde **yeni proje** iletişim kutusu, Şekil 4-27'de gösterildiği gibi.

![Visual Studio'da yeni bir ASP.NET Core web uygulaması için Docker desteğini etkinleştir](./media/enable-docker-support-visual-studio.png)

Visual Studio 2017'de proje oluşturma sırasında Şekil 4-27: Docker desteğini etkinleştir

Visual Studio ekleyin ya da Docker desteğini etkinleştirmek ekler bir *Dockerfile* projeye dosya.

> [!NOTE]
> Bilgisayarınızda Docker Compose desteği proje oluştururken bir .NET Framework web uygulaması projesi (olmayan bir .NET Core web uygulaması projesi) için Şekil 4-28 gösterildiği etkinleştirdiğinizde, kapsayıcı Düzenleyicisi desteği de eklenir.
>
> ![Docker'ı etkinleştirme desteği için bir .NET Framework web uygulaması projesi oluşturma](media/enable-docker-compose-support.png)

> Şekil 4-28: Visual Studio 2017'de .NET Framework web uygulaması projesi üzerinde Docker Compose desteği etkinleştirme

### <a name="add-container-orchestrator-support"></a>Kapsayıcı Düzenleyicisi desteği Ekle

Çok kapsayıcılı bir çözüm oluşturmak istediğinizde, kapsayıcı Düzenleyicisi desteği, projenize ekleyin. Kapsayıcı Düzenleyicisi desteği eklediğinizde, Visual Studio ekler bir *Dockerfile* (zaten yoksa) proje ile genel *docker-compose.yml* çözüm düzeyinde dosya. Bu, çalıştırma ve aynı tanımlanan bir grup kapsayıcının (tam çözüm) aynı anda hata ayıklaması sağlar *docker-compose.yml* dosya. Varsa *docker-compose.yml* zaten var, Visual Studio yalnızca ekler gerekli yapılandırma kod satırı için.

Kapsayıcı düzenleme desteği projenize ekledikten sonra projeye eklenen bir Dockerfile bakın ve **docker-compose** çözümüne eklenmiş klasör **Çözüm Gezgini**, Şekil 4-29 gösterildiği gibi:

![Visual Studio'daki Çözüm Gezgini'nde docker dosyaları](media/docker-support-solution-explorer.png)

Şekil 4-29: Docker dosyaları Çözüm Gezgini'nde Visual Studio 2017

**Daha fazla bilgi:** Hizmetleri uygulaması ve Docker için Visual Studio Araçları'nın kullanımı hakkında daha ayrıntılı bilgi için bu makaleleri okuyun:

Derleme, hata ayıklama, güncelleştirme ve uygulamaları yerel bir Docker kapsayıcısında Yenile: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Bir ASP.NET Core Docker kapsayıcısını bir kapsayıcı kayıt defterine dağıtın: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Önceki](docker-apps-inner-loop-workflow.md)
[İleri](set-up-windows-containers-with-powershell.md)