---
title: Üretim ortamlarında oluşturulan ve mikro hizmet tabanlı uygulamaları çalıştırma
description: Üretimde konteyner tabanlı uygulamaları çalıştırmak için önemli bileşenleri tanıyın
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295465"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Üretim ortamlarında oluşturulan ve mikro hizmet tabanlı uygulamaları çalıştırma

Birden çok mikro hizmet tarafından oluşturulan uygulamaların, dağıtımın karmaşıklığını basitleştirmek ve BT açısından uygulanabilir hale getirmek için orkestratör kümelerine dağıtılması gerekir. Bir orchestrator kümesi olmadan, karmaşık bir mikrohizmetler uygulamasını dağıtmak ve ölçeklendirmek zor olacaktır.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Orkestratörlere, zamanlayıcılara ve konteyner kümelerine giriş

Daha önce bu e-kitap, *kümeler* ve *zamanlayıcılar* yazılım mimarisi ve geliştirme tartışmanın bir parçası olarak tanıtıldı. Kubernetes ve Hizmet Kumaş Docker kümeleri örnekleridir. Bu orkestratörlerin her ikisi de Microsoft Azure Kubernetes Hizmeti tarafından sağlanan altyapının bir parçası olarak çalıştırılabilir.

Uygulamalar birden çok ana bilgisayar sistemi arasında ölçeklendirildiğinde, her ana bilgisayar sistemini yönetme ve temel platformun karmaşıklığını soyutlayabilme becerisi çekici hale gelir. Orkestratörler ve programcılar tam olarak bunu sağlıyor. Burada onlara kısa bir göz atalım:

- **Zamanlayıcılar.**"Zamanlama", yöneticinin bir hizmet dosyasını belirli bir kapsayıcının nasıl çalıştırılsüreceğini belirleyen bir ana bilgisayar sistemine yükleme yeteneğini ifade eder. Docker kümesinde kapsayıcıların başlatılması zamanlama olarak bilinir. Zamanlama, hizmet tanımını yüklemenin özel bir eylemi anlamına gelse de, daha genel anlamda, zamanlayıcılar gereken kapasitede hizmetleri yönetmek için bir ana makinenin init sistemine bağlanmaktan sorumludur.

   Küme zamanlayıcısının birden çok hedefi vardır: kümenin kaynaklarını verimli bir şekilde kullanmak, kullanıcı tarafından sağlanan yerleşim kısıtlamalarıyla çalışmak, uygulamaları bekleme durumunda bırakmamak için hızla planlamak, bir "adalet derecesine" sahip olmak, hatalara karşı sağlam olmak ve her zaman kullanılabilir olmalıdır.

- **Orkestratörler.**Platformlar, bir ana bilgisayar kümesinde dağıtılan karmaşık, çok kapsayıcılı iş yüklerine yaşam döngüsü yönetimi yeteneklerini genişletir. Ana bilgisayar altyapısını soyutlayarak, düzenleme araçları kullanıcılara tüm kümeyi tek bir dağıtım hedefi olarak ele almaları için bir yol sağlar.

   Düzenleme süreci, takım ve uygulama yönetiminin tüm yönlerini konteyner başına ilk yerleştirme veya dağıtımdan otomatikleştirebilen bir platform içerir; konteynırları ev sahibinin sağlığına veya performansına bağlı olarak farklı ana bilgisayarlara taşımak; ölçekleme ve başarısızlığı destekleyen sürüm ve yuvarlama güncellemeleri ve sistem durumu izleme işlevleri; ve daha birçok.

   Orkestrasyon, kapsayıcı zamanlaması, küme yönetimi ve büyük olasılıkla ek ana bilgisayarların sağlanmasıanlamına gelen geniş bir terimdir.

Orkestratörler ve zamanlayıcılar tarafından sağlanan yetenekler geliştirmek ve sıfırdan oluşturmak için karmaşıktır, bu nedenle genellikle satıcılar tarafından sunulan orkestrasyon çözümleri kullanmak isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](manage-production-docker-environments.md)
