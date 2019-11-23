---
title: Üretim ortamlarında oluşturulan ve mikro hizmet tabanlı uygulamaları çalıştırma
description: Üretimde kapsayıcı tabanlı uygulamalar çalıştırmak için temel bileşenleri öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295465"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Üretim ortamlarında oluşturulan ve mikro hizmet tabanlı uygulamaları çalıştırma

Birden fazla mikro hizmet tarafından oluşturulan uygulamaların, dağıtımın karmaşıklığını basitleştirmek ve BT bakış noktasından önemli hale getirmek için Orchestrator kümelerine dağıtılması gerekir. Orchestrator kümesi olmadan, karmaşık bir mikro hizmet uygulamasının dağıtılması ve ölçeğini genişletmek zor olabilir.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Düzenleyicilerine, zamanlayıcılar ve kapsayıcı kümelerine giriş

Bu e-kitapta daha önce, *kümeler* ve *zamanlayıcılar* , yazılım mimarisi ve geliştirme hakkındaki tartışmanın bir parçası olarak sunulmuştur. Kubernetes ve Service Fabric Docker kümelerine örnektir. Bu düzenleyiciler her ikisi de Microsoft Azure Kubernetes hizmeti tarafından sunulan altyapının bir parçası olarak çalışabilir.

Uygulamalar birden çok konak sisteminde ölçeklendirildiğinde, her bir konak sistemini yönetebilir ve temel alınan platformun karmaşıklığını ortadan kaldırmak etkileyici hale gelir. Bu, tam olarak hangi düzenleyiciler ve zamanlayıcılar sağlar. Buradan buraya göz atalım:

- **Zamanlayıcılar**. "Zamanlama", yöneticinin belirli bir kapsayıcının nasıl çalıştırılacağını belirleyen bir konak sistemine hizmet dosyası yükleme yeteneğini ifade eder. Bir Docker kümesinde kapsayıcılar başlatma, zamanlama olarak bilinmesine eğilimindedir. Zamanlama, hizmet tanımını yüklemeyi belirli bir şekilde ifade eder, ancak daha genel bir fikir için, zamanlayıcılar gereken herhangi bir kapasiteye sahip hizmetleri yönetmek üzere bir konağın init sistemine bağlanmaktan sorumludur.

   Bir küme zamanlayıcıda birden çok hedef vardır: kümenin kaynaklarını verimli bir şekilde kullanma, Kullanıcı tarafından sağlanan yerleştirme kısıtlamalarıyla çalışma, uygulamaları bir bekleme durumunda bırakmak için hızla zamanlama, "eşitliği", hatalara dayanıklı olma ve her zaman kullanılabilir.

- **Düzenleyiciler**. Platformlar, yaşam döngüsü yönetimi yeteneklerini, bir konaklar kümesine dağıtılan karmaşık, çok Kapsayıcılı iş yüklerine genişletir. Orchestration araçları, konak altyapısını soyutlayarak kullanıcılara tüm kümeyi tek bir dağıtım hedefi olarak ele almak için bir yol sağlar.

   Düzenleme süreci, araç ve uygulama yönetiminin tüm yönlerini kapsayıcı başına ilk yerleştirme veya dağıtımdan otomatik hale getirebilen bir platform içerir. bir konağın sistem durumuna veya performansına bağlı olarak kapsayıcıları farklı konaklara taşıma; ölçek ve yük devretmeyi destekleyen sürüm oluşturma ve yuvarlama güncelleştirmeleri ve sistem durumu izleme işlevleri; ve çok daha fazlası.

   Düzenleme, kapsayıcı zamanlama, küme yönetimi ve büyük olasılıkla ek ana bilgisayarların sağlanması ile ilgili geniş bir terimdir.

Düzenleyen ve zamanlayıcılar tarafından sağlanan yetenekler sıfırdan geliştirme ve oluşturma için karmaşıktır. bu nedenle, genellikle satıcılar tarafından sunulan düzenleme çözümlerini kullanmak istersiniz.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](manage-production-docker-environments.md)
