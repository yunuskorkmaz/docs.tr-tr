---
title: "Docker (Windows için Visual Studio) için Visual Studio araçlarını kullanma"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0525633b23625d915fd447d438c6281fb14b3b46
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2018
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Docker (Windows için Visual Studio) için Visual Studio araçlarını kullanma

Docker Visual Studio Code ve Docker CLI kullanırken akışına benzer için Visual Studio Araçları kullanırken Geliştirici iş akışı (aslında, aynı Docker CLI üzerinde temel), ancak başlamak kolaydır, işlemini basitleştirir ve büyük sağlar derleme için üretkenlik çalıştırın ve Görevler oluşturun. Ayrıca yürütün ve kapsayıcılarınızı F5 ve Ctrl + F5 Visual Studio'dan gibi basit eylemleri aracılığıyla hata ayıklama mümkün değildir. Daha da ile çalıştırın ve tek bir kapsayıcı hata ayıklamak için ek olarak Visual Studio 2017, ayrıca çalıştırabilir ve çözüm düzeyinde aynı docker-compose.yml dosyası olarak tanımlanmışsa kapsayıcıları (tam çözüm) bir grup aynı anda hata ayıklama.

## <a name="configuring-your-local-environment"></a>Yerel ortamınızı yapılandırma

Windows için Docker en son sürümleri ile Kurulum sonucunun aşağıdaki başvurularında açıklandığı gibi olduğundan Docker uygulamaları geliştirmek için her zamankinden daha kolay olur.

**Daha fazla bilgi:** Docker için Windows'u yükleme hakkında daha fazla bilgi için şuraya gidin <https://docs.docker.com/docker-for-windows/>.

Visual Studio 2015 kullanıyorsanız, güncelleştirme 3 veya sonraki bir sürümünü artı Docker için Visual Studio Araçları olması gerekir.

**Daha fazla bilgi:** Visual Studio'yu yükleme ile ilgili yönergeler için Git [https://www.visualstudio.com/ \ ürünler/vs-2015-ürün-sürümleri](https://www.visualstudio.com/products/vs-2015-product-editions).

Docker için Visual Studio araçlarını yükleme hakkında daha fazla bilgi görmek için Git <http://aka.ms/vstoolsfordocker> ve <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.

Visual Studio 2017 kullanıyorsanız, Docker destek zaten dahil edilmiştir.

## <a name="using-docker-tools-in-visual-studio-2015"></a>Visual Studio 2015'te Docker araçlarını kullanma

Docker için Visual Studio Araçları geliştirmek ve yerel olarak Linux Docker ana bilgisayar veya VM ya da Windows Kapsayıcılarınızı doğrudan Windows'da Linux için Docker kapsayıcılarınızı doğrulamak için tutarlı bir yol sağlar.

Tek bir kapsayıcı kullanıyorsanız, .NET Core projenize Docker desteğini etkinleştirmek için başlamak için gereken ilk şey olur. Bunu yapmak için Şekil 4-25 gösterildiği gibi proje dosyasını sağ tıklatın.

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

Şekil 4-25: açma, Visual Studio projesi için Docker desteği

## <a name="using-docker-tools-in-visual-studio-2017"></a>Visual Studio 2017 içinde Docker araçlarını kullanma

Eklediğinizde Docker destek hizmeti projesine çözümünüzde (bkz. Şekil 4-26), Visual Studio değil yalnızca ekleme DockerFile dosyayı projenize, bunu ayrıca bir hizmet bölümü çözümünüzün docker-compose.yml dosyaları (veya bunlar almadıysanız dosyalar oluşturma ekleme var). Multicontainer çözümünüzü oluşturmaya başlamak için kolay bir yoludur.; ardından docker-compose.yml dosyaları açmak ve bunları ile ek özellikler güncelleştirin.

![](./media/image32.png)

Şekil 4-26: Visual Studio 2017 proje Docker çözümü desteği kapatma

Bu eylem, yalnızca DockerFile projenize ekler, bir genel docker-çözüm düzeyinde ayarlanan compose.yml için gerekli yapılandırma satırlık bir kod da ekler.

Ayrıca Docker desteği Visual Studio 2017 ' bir ASP.NET Core projesi oluştururken, Şekil 4-27'de gösterildiği gibi kapatabilirsiniz.

![](./media/image33.png)

Şekil 4-27: açma bir projesi oluştururken, Docker desteği

Çözüm Gezgini'nde yeni düğümü ağacı eklenen docker-compose.yml dosyalarla ayrıca Visual Studio çözümünüzde Docker destek ekledikten sonra Şekil 4-28'de gösterildiği gibi görürsünüz.

![](./media/image34.PNG)

Şekil 4-28: docker-compose.yml dosyaları şimdi Çözüm Gezgini'nde görüntüler.

Bir multicontainer dağıtabilirsiniz çalıştırdığınızda tek docker-compose.yml dosyası kullanarak uygulama docker-oluşturun; değerleri (Geliştirme karşı üretim) ortamını ve yürütme bağlı olarak kılabilir ancak, Visual Studio, bir grup ekler türü (hata ayıklama ve yayın). Bu yetenek, daha iyi sonraki bölümde açıklanacaktır.

**Daha fazla bilgi:** Hizmetleri uygulaması ve Docker için Visual Studio Araçları kullanımı hakkında daha fazla ayrıntı için aşağıdaki makaleleri okuyun:

Yapı, hata ayıklama, güncelleştirme ve yenileme yerel bir Docker kapsayıcısı uygulamalarında: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Bir ASP.NET kapsayıcısı uzak bir Docker konağına dağıtın: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)


>[!div class="step-by-step"]
[Önceki] (docker-apps-iç-döngü-workflow.md) [sonraki] (set-up-windows-containers-with-powershell.md)
