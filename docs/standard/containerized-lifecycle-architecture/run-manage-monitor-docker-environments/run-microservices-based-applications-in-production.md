---
title: "Üretim ortamlarında oluşan ve mikro tabanlı uygulamaları çalıştırma"
description: "Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0d7611d07c9995984269e3f7b071154d9b861367
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Üretim ortamlarında oluşan ve mikro tabanlı uygulamaları çalıştırma

Uygulamalar tarafından birden çok mikro oluşan dağıtım karmaşıklığını basitleştirmek ve açısından bir BT uygulanabilir yapabilmeniz için orchestrator kümeler halinde dağıtılması gerekiyor. Bir orchestrator küme dağıtmak ve genişleme karmaşık mikro uygulama çok zor olurdu.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Orchestrators, zamanlayıcılar ve kapsayıcı kümeleri giriş

Daha önce bu e-kitap içinde gösterdiğimizi *kümeleri* ve *zamanlayıcılar* yazılım mimarisi ve geliştirme tartışma bir parçası olarak. Docker Swarm ve Mesosphere Datacenter işletim sistemi (DC/OS) Docker kümeleri örnekleridir. Bunların her ikisi de, Microsoft Azure kapsayıcı hizmeti tarafından sağlanan alt yapısının bir parçası olarak çalıştırabilirsiniz.

Uygulamaları birden çok ana bilgisayar sistemleri arasında ölçeklendirilmiş olduğunda, her ana bilgisayar sistemi yönetmek ve hemen temel platform karmaşıklığını soyut olanağı çekici haline gelir. Tam olarak ne orchestrators ve zamanlayıcılar sağlamaktır. Burada onları kısa bir göz atalım:

-   **Zamanlayıcılar*** *özelliği bir yöneticinin belirli bir kapsayıcıya çalıştırma kurar bir ana bilgisayar sistemine üzerine hizmet dosyasını yüklemek "Zamanlama" başvurur. Kapsayıcıları bir Docker kümedeki başlatma planlama olarak bilindiği eğilimindedir. Hizmet tanımında daha genel bir fikir yüklenirken özel eylemi zamanlama başvuruyor ancak zamanlayıcılar gerekli ne olursa olsun kapasite hizmetleri yönetmek için bir ana bilgisayarın init sistemine takma için sorumludur.

Bir küme Zamanlayıcı birden çok hedefi vardır: küme kaynaklarını verimli bir şekilde kullanarak, kullanıcı tarafından sağlanan yerleşim kısıtlaması, hızlı bir şekilde bunları bekleyen bir durumda değil bırakmayı "eşitliği, hatalar için güçlü olan" derecesini sahip uygulamalar zamanlama ile çalışma ve her zaman kullanılabilir.

-   **Orchestration*** *platformları bir konak kümesi üzerinde dağıtılmış multicontainer, karmaşık iş yükleri yaşam döngüsü yönetimi özelliklerini genişletir. Ana bilgisayar altyapı özetleyen tarafından düzenleme araçları kullanıcıların tüm küme tek dağıtım hedefi olarak işlemek için bir yol sağlar.

Düzenleme işlemi araçları ve uygulama yönetimi ilk yerleştirme veya kapsayıcı başına dağıtım tüm yönlerini otomatikleştirebilirsiniz bir platform gerektirir; kapsayıcılar kendi ana bilgisayarın sistem durumu veya performans bağlı olarak farklı ana taşıma; sürüm oluşturma ve çalışırken güncelleştirmeleri ve sistem durumu izleme ölçekleme ve yük devretme desteği işlevlerine; ve çok daha fazlası.

Orchestration kapsayıcı zamanlama, küme yönetim ve büyük olasılıkla ek ana sağlama başvuran geniş bir terimdir.

Orchestrators ve zamanlayıcılar tarafından sağlanan özellikleri geliştirmek ve sıfırdan oluşturmak için çok karmaşık ve bu nedenle, genellikle yapmak istersiniz orchestration çözümleri kullanımını satıcılar tarafından sunulan.


>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (yönetme-üretim-docker-environments.md)
