---
title: Özet ve yol ileride
description: Key Davpr ekibinizle Özeti ve yolda ileride bir bakış.
ms.date: 02/04/2021
author: robvet
ms.openlocfilehash: 28b4b2a86865fd2e701e95bdd0b0979ed45786ca
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100629439"
---
# <a name="summary-and-the-road-ahead"></a>Özet ve yol ileride

En son olarak, Davpr uçuşımızı sunuyoruz. [Bölüm 2](dapr-at-20000-feet.md) ' den 20.000 metrede bulunan Jet düzlemi, son yaklaşımda ve vb. ile ilgilidir.

Düzlem, kapıya ait olduğundan, bu kılavuzun bazı önemli ekibinizle gözden geçirmek için bir dakikanızı atalım:

- **Davpr** -dadpr, dağıtılmış uygulamalar oluşturmayı kolaylaştıran bir *Dağıtılmış uygulama çalışma zamanı* . Yapı taşları ve takılabilir bileşen mimarisi sunar. Davpr, uygulamanızı, Davpr çalışma zamanında bulunan altyapı özellikleri ile bağlayan **dinamik bir birleştirici** sağlar. Altyapı sıhhi tesisat 'ı oluşturmak yerine, siz ve takımınız müşterilere iş özellikleri sunmaya odaklanmaktadır.

- **Açık kaynak ve platformlar arası** -yerel davpr API 'SI, http veya GRPC 'yi destekleyen *herhangi bir platformda* tüketilebilir. Davpr Ayrıca popüler geliştirme platformları için dile özgü SDK 'lar sağlar. Davpr v 1.0 Go, Python, .NET, Java, PHP ve JavaScript 'i destekler.

- **Derleme blokları** -davpr yapı taşları dağıtılmış uygulama işlevselliğini Kapsüller. Bu yazma sırasında, Davpr Şekil 11-1 ' de gösterilen yedi bina bloğunu destekler.

![Davpr yapı taşları](./media/dapr-at-20000-feet/building-blocks.png)

**Şekil 11-1**. Davpr yapı taşları.

- **Bileşenler** -davpr bileşenleri, her bir davpr yapı taşı özelliği için somut uygulama sağlar. Bunlar, geliştiricilerin uygulama kodunu değiştirmeden bileşen uygulamalarını takas etmesini sağlayan ortak bir arabirim sunar. Şekil 11-2, bileşenler, yapı taşları ve hizmetiniz arasındaki ilişkiyi gösterir.

![Davpr derleme blokları tümleştirmesi](./media/dapr-at-20000-feet/building-blocks-integration.png)

**Şekil 11-2**. Davpr yapı blok tümleştirmesi.

- **Sidecars** -DAPR, bir kapsayıcının ayrı bir işlemi olarak bir sepet mimarisinde uygulamanızın yanı sıra çalışır. Uygulamanız HTTP ve gRPC üzerinden Davpr API 'Leri ile iletişim kurar. Sidecler, hizmetin bir parçası olmadıkları ve ona bağlı olduğu için yalıtım ve kapsülleme sağlar. Şekil 11-3, bir sepet mimarisini gösterir.

![Sidecar mimarisi](./media/dapr-at-20000-feet/sidecar-generic.png)

**Şekil 11-3**. Sidecar mimarisi.

- **Barındırma ortamları** Davpr platformlar arası desteğe sahiptir ve birden çok ortamda çalışabilir. Bu yazma sırasında ortamlar, yerel olarak barındırılan bir mod ve Kubernetes içerir.

- **eshopondadpr** -bu kitap, [eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr)'e yönelik bir başvuru uygulaması içerir. Popüler bir e-ticaret uygulaması etki alanı kullanarak, başvuru uygulaması her yapı bloğunun kullanımını gösterir. Bu, birkaç yıl önce yayınlanan yaygın olarak popüler [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers)'ın bir evmidir.

## <a name="the-road-ahead"></a>Yol ileride

İleri bakıyor, Davpr dağıtılmış uygulama geliştirmeye yönelik bir etkiye sahip olma potansiyelini içeriyor. Davpr ekibinin ve açık kaynaklı katkıda bulunanların ne kadar beklediğini düşünüyorsunuz?

Yazma sırasında, Davpr için önerilen geliştirmelerin listesi şunları içerir:

- Mevcut yapı taşlarına yönelik özellik geliştirmeleri:
  - Durum yönetiminde sorgu özellikleri, birden çok değer almanızı sağlar.
  - Konuya göre konuları filtrelemenizi sağlayan, pub/Sub 'da filtreleme konusu.
  - Observability içinde, belirli kitaplıklara bağlama gerekmeden doğrudan uygulamada izleme sağlayan bir uygulama izleme API 'SI.
  - Aktör programlama modeline olay odaklı yetenekler sağlayan aktörler için bağlama ve yayımlama/alt destek. Bağlantılı bileşenler, aktördeki yöntemleri çağırmak için olayları ve iletileri tetikler.

- Yeni yapı taşları:
  - Yapılandırma verilerini okumak ve yazmak için yapılandırma API 'SI yapı taşı. Blok, Azure Configuration Manager veya GCP yapılandırma yönetimi içeren sağlayıcılara bağlanır.
  - Http 'den sıfıra ölçeğe otomatik ölçeklendirme.
  - Öncü seçim yapı bloğu tekil örnekler sağlamak ve anlam özelliklerini kilitlemek için.
  - Hizmet çağrısı için saydam proxy oluşturma bloğu, ağ düzeyinde URL 'Leri veya DNS adreslerini temel alarak iletileri yönlendirmenize olanak tanır.
  - Dayanıklılık yapı taşı (devre kesiciler, bölme perdeleri & zaman aşımları).

- Çerçeveler ve bulut Yerel teknolojileriyle tümleştirme. Bazı örnekler:
  - Django
  - Nodejs
  - Express
  - Kyma dili
  - Midway

- Yeni dil SDK 'Ları:
  - JavaScript
  - RUST
  - C++

- Yeni barındırma platformları:
  - VM'ler
  - Azure IoT Edge
  - Azure Stack Edge
  - Azure Service Fabric

- Geliştirici ve operatör üretkenlik araçları:
  - VS Code uzantısı.
  - DevOps işlem hattı geliştirmede yerel hata ayıklama için uzak geliştirme kapsayıcıları.
  - Davpr uygulamalarını yönetmenin işletimsel kaygılarına daha derin görünürlük sağlayacak olan davpr işlemsel Pano geliştirmeleri.

Davpr sürüm 1,0, geliştiricilere dağıtılmış uygulamalar oluşturmaya yönelik etkileyici bir araç kutusu sağlar. Önerilen geliştirme listesinde gösterildiği gibi, Davpr, gelecek birçok yeni özelliğe sahip etkin geliştirme aşamasındadır. Sonraki güncelleştirmeler için, [davpr sitesini](https://dapr.io/) ve [davpr duyurusu blogunu](https://cloudblogs.microsoft.com/opensource/2019/10/16/announcing-dapr-open-source-project-build-microservice-applications/) takip edin.

>[!div class="step-by-step"]
>[Önceki](secrets.md)
