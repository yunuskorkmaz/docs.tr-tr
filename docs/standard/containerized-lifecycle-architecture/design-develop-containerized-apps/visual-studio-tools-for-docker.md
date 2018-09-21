---
title: (Windows için Visual Studio) Docker için Visual Studio araçlarını kullanma
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46488957"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>(Windows için Visual Studio) Docker için Visual Studio araçlarını kullanma

Docker için Visual Studio araçları kullanarak, geliştirme iş akışı, Visual Studio Code ve Docker CLI'yı kullanırken iş akışına benzerdir. Aslında, aynı Docker CLI'yı dayanır ancak başlamak kolaydır, bu süreci kolaylaştırır ve daha yüksek üretkenlik sağlar, derleme için çalıştırın ve Görevler oluşturun. Ayrıca, yürütün ve kapsayıcılarınızı F5 ve Ctrl + F5 Visual Studio'dan gibi basit eylemleri aracılığıyla hata ayıklama mümkün değildir. Çalıştırın ve tek bir kapsayıcı hata ayıklama ek olarak isteğe bağlı bir kapsayıcı düzenleme desteği, çalıştırın ve bir grup kapsayıcının (tam çözüm) aynı anda hata ayıklama. Aynı kapsayıcıları tanımlamak *docker-compose.yml* çözüm düzeyinde dosya.

## <a name="configuring-your-local-environment"></a>Yerel ortamınızı yapılandırma

Docker desteği, herhangi bir yüklü .NET ve .NET Core iş yükleri ile Visual Studio 2017'de dahil edilmiştir. Docker için Windows ayrı yükleyin.

Docker için Windows en son sürümleri ile Kurulumu aşağıdaki başvuruları açıklandığı gibi basit, çünkü Docker uygulamaları geliştirmek için her zamankinden daha kolaydır.

**Daha fazla bilgi:** için Docker Windows yükleme hakkında daha fazla bilgi edinmek için Git <https://docs.docker.com/docker-for-windows/>.

**Daha fazla bilgi:** Visual Studio'yu yükleme ile ilgili yönergeler için Git [ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/).

Docker için Visual Studio Araçları'nı yükleme hakkında daha fazla bilgi görmek için Git <http://aka.ms/vstoolsfordocker> ve <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.

## <a name="using-docker-tools-in-visual-studio-2017"></a>Visual Studio 2017'de Docker araçları kullanma

Docker desteği bir projeye eklerken (bkz. Şekil 4-26), Visual Studio ekler bir *Dockerfile* proje kök dizini.

![Docker çözümü desteği Visual Studio 2017 proje açma](./media/image32.png)

Şekil 4-26: Docker çözümü desteği Visual Studio 2017 proje açma

 Docker Compose, aracılığıyla kapsayıcı düzenleme desteği, varsayılan olarak Visual Studio 2017 sürüm 15.7 veya önceki eklenir. Kapsayıcı düzenleme desteği Tercihli özellik Visual Studio 2017 sürümlerinde 15,8 ya da daha sonra bu durumda Docker Compose ve Service Fabric desteklenir.

Visual Studio sürüm 15,8 ve üzeri ile her ilişkili bir kapsayıcıya sahip olduğunuzu bir çözümde birden çok proje için destek ekleyebilirsiniz. İçinde çözüm veya proje düğümünü sağ **Çözüm Gezgini**ve **Ekle** > **kapsayıcı düzenleme desteği**.  Ardından **Docker Compose** veya **Service Fabric** kapsayıcıları yönetmek için.

Seçeneğini belirlediğinizde **Docker Compose**, Visual Studio çözümünüze ait bir hizmet bölümü ekler *docker-compose.yml* dosyaları (veya siz varsa dosyaları oluşturur). Çok kapsayıcılı çözümünüzü oluşturmaya başlamak için kolay bir yoludur; Daha sonra açabilirsiniz *docker-compose.yml* dosyaları ve ek özellikler ile güncelleştirin.

Bu eylem için kod gerekli yapılandırma satırlarını ekler bir *docker-compose.yml* çözüm düzeyinde ayarlayın.

Ayrıca Docker desteğini Visual Studio 2017'de bir ASP.NET Core projesi oluştururken, Şekil 4-27'de gösterildiği gibi kapatabilirsiniz.

![Bir proje oluştururken, Docker desteği açma](./media/image33.png)

Bir proje oluştururken, Docker desteği Şekil 4-27: açma

Visual Studio çözümünüzde Docker desteği ekledikten sonra ayrıca yeni bir düğüm ağaçta görürsünüz **Çözüm Gezgini** eklenen ile *docker-compose.yml* dosyaları, Şekil 4-28'de gösterildiği gibi.

![docker-compose.yml dosyaları şimdi Çözüm Gezgininde görüntüle](./media/image34.PNG)

Şekil 4-28: docker-compose.yml dosyaları artık öne **Çözüm Gezgini**

Tek bir kullanarak çok kapsayıcılı bir uygulama dağıtabilirsiniz *docker-compose.yml* dosyasını çalıştırdığınızda `docker-compose up`; ancak, Visual Studio (karşı geliştirme ortamına bağlı olarak değerleri geçersiz kılmak için bir grubu ekler Üretim) ve yürütme (hata ayıklama ve yayın) yazın. Bu özellik, daha iyi ilerleyen bölümlerde açıklanmıştır.

Service Fabric Docker Compose yerine birden çok kapsayıcı yönetmek için kullanabilirsiniz. Bkz: [öğretici: Azure Service Fabric'e Windows kapsayıcısındaki bir .NET uygulaması dağıtma](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).

**Daha fazla bilgi:** Hizmetleri uygulaması ve Docker için Visual Studio Araçları'nın kullanımı hakkında daha ayrıntılı bilgi için bu makaleleri okuyun:

Derleme, hata ayıklama, güncelleştirme ve uygulamaları yerel bir Docker kapsayıcısında Yenile: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Bir ASP.NET Core Docker kapsayıcısını bir kapsayıcı kayıt defterine dağıtın: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Önceki](docker-apps-inner-loop-workflow.md)
[İleri](set-up-windows-containers-with-powershell.md)
