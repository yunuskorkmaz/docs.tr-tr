---
title: Üretim ortamlarında oluşturulan ve mikro hizmet tabanlı uygulamaları çalıştırma
description: Üretimde kapsayıcı tabanlı uygulamaları çalıştırmak için anahtar bileşenleri ile tanışın
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 52cf273194bff10192b06d236bda7c1cbea1abd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921595"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Üretim ortamlarında oluşturulan ve mikro hizmet tabanlı uygulamaları çalıştırma

Uygulamalar tarafından birden çok mikro hizmetlerden dağıtım karmaşıklığını basitleştirir ve uygun bir BT açısından kolaylaştırmak için orchestrator kümeler halinde dağıtılması gerekiyor. Bir orchestrator kümesi dağıtmak ve karmaşık mikro hizmetler uygulamanın ölçeğini genişletmek zor olacaktır.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Düzenleyicileri, zamanlayıcılar ve kapsayıcı kümeleri giriş

Bu e-kitap, önceki *kümeleri* ve *zamanlayıcılar* yazılım mimarisi ve geliştirme tartışmaya bir parçası olarak tanıtılan. Kubernetes ve Service Fabric kümeleri Docker örnekleridir. Bu düzenleyicileri her ikisi de, Microsoft Azure Kubernetes hizmeti tarafından sunulan altyapıyı bir parçası olarak çalıştırabilirsiniz.

Uygulamalar arasında birden fazla konak sistemi genişletilmiş olduğunda, her bir konak sistemi yönetmek ve temel alınan platformu karmaşıklığını hemen soyut olanağı cazip hale gelir. Tam olarak neler düzenleyiciler ve zamanlayıcılar sağlar olmasıdır. Burada bunları kısa bir göz atalım:

- **Zamanlayıcılar**. "Zamanlama" özelliği bir yöneticinin hizmet dosya belirli bir kapsayıcı çalıştırma kurar ve bir konak sistemi yüklemesini ifade eder. Kapsayıcıları bir Docker kümesi başlatma zamanlama olarak bilinen eğilimindedir. Hizmet tanımında daha genel bir fikir yükleme belirli Yasası zamanlama başvuruyor ancak zamanlayıcılar gereken herhangi bir kapasite hizmetleri yönetmek için bir ana bilgisayarın init sisteme takma için sorumlu olursunuz.

   Bir küme Zamanlayıcı birden çok hedefi vardır: küme kaynaklarını verimli bir şekilde kullanarak, kullanıcı tarafından sağlanan yerleştirme kısıtlamaları, "eşitliği, hataları güçlü olan" derecesini sahip hızlı bir şekilde onlara bir bekleyen durumda bırakmamaya uygulamalar planlama ile çalışma ve her zaman kullanılabilir olacak.

- **Düzenleyiciler**. Platformları, bir konak kümesi üzerinde dağıtılmış karmaşık, çok kapsayıcılı iş yüklerini yaşam döngüsü yönetim özelliklerini genişletin. Aldığı konak altyapısının özetleyen tarafından düzenleme araçları kullanıcıların tüm küme tek dağıtım hedefi olarak değerlendirilecek bir yol sağlar.

   Düzenleme işlemi, Araçlar ve uygulama yönetimi ilk yerleştirme veya kapsayıcı başına dağıtım tüm yönlerini otomatikleştiren bir platform gerektirir; kapsayıcıları kendi ana bilgisayarın sistem durumu veya performans bağlı olarak farklı Konaklara taşıma; sürüm oluşturma ve sıralı güncelleştirmeler ve sistem durumu izleme, ölçeklendirme ve yük devretme destekleyen işlevleri; ve daha fazlası.

   Orchestration kapsayıcı zamanlama, küme yönetimi ve büyük olasılıkla ek ana sağlama için başvuruda bulunan bir geniş bir terimdir.

Düzenleyiciler ve zamanlayıcılar tarafından sağlanan özellikler geliştirmek ve sıfırdan oluşturmak için karmaşık, bu nedenle, genellikle düzenleme çözümlerinin satıcıları tarafından sunulan kullanmak isteyebilirsiniz.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](manage-production-docker-environments.md)
