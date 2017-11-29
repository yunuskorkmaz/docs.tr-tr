---
title: "Karma bulut senaryolarında geçirme"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Karma bulut senaryolarında geçirme"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/2/2017
ms.openlocfilehash: 7394d0fd208e131b4e683298f6ca31a9eddade28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Karma bulut senaryolarında geçirme

Bazı kuruluşlar ve işletmeler uygulamalarını Microsoft Azure gibi genel Bulutlar için bazıları veya diğer genel bulut düzenlemeler veya kendi ilkeleri nedeniyle geçiremezsiniz. Ancak, herhangi bir kuruluştaki bazı genel Bulut ve diğer uygulamalar şirket uygulamalarında kalmaktan yararlanabilir olasıdır. Ancak, karma bir ortamı farklı platformları ve şirket içi ortamları ve genel Bulutlar kullanılan teknolojiler nedeniyle ortamlarda aşırı karmaşıklığa neden olabilir.

Microsoft, en iyi karma bulut çözümü sağlar, biri içinde en iyi duruma getirebilir varolan varlıklarınızı şirket içi ve buluttaki bir Azure karma bulutta tutarlılığı sırada ortak,. Var olan becerileri en üst düzeye çıkarmak ve bulutta veya şirket içi, Azure yığını (şirket içi) ve Azure (genel bulut) sayesinde çalıştırabilirsiniz uygulamaları oluşturmak için esnek, birleştirilmiş bir yaklaşım alabilirsiniz.

Güvenlik geldiğinde, yönetim ve güvenlik, karma bulut merkezileştirebilirsiniz. Çoklu oturum açma şirket içi sağlayarak tüm varlıklar üzerinde denetim merkeziniz buluta almak ve bulut uygulamalarında. Bunu Active Directory karma bir buluta genişletme ve kimlik yönetimi kullanarak gerçekleştirirsiniz.

Son olarak, dağıtmak ve sorunsuz bir şekilde verileri çözümlemek, Bulut ve şirket içi varlıklar için sorgu dillerini kullanın ve analizi ve kaynağına bakılmaksızın, verilerinizi zenginleştirmek için azure'da öğrenme derin uygulanır.

## <a name="azure-stack"></a>Azure yığını

Azure yığın kuruluşunuzun veri merkezinden Azure Hizmetleri sunmanıza olanak sağlayan bir karma bulut platformudur. Azure yığın kenar ve bağlantısız ortamlarda veya toplantı belirli güvenlik ve uyumluluk gereksinimleri gibi anahtar senaryolarda modern, uygulamalarınız için yeni seçenekler destekleyecek şekilde tasarlanmıştır.

Şekil 4-13 Microsoft sunar doğru karma bulut platformu özetini gösterir.

![Microsoft Azure yığın ve Azure ile karma bulut platformu](./media/image13.jpg)

> **Şekil 4-13.** Microsoft Azure yığın ve Azure ile karma bulut platformu

Azure yığın gereksinimlerinizi karşılamak için iki dağıtım seçeneği, sunulur:

-   Azure tümleşik yığını sistemleri

-   Azure yığın Geliştirme Seti

### <a name="azure-stack-integrated-systems"></a>Azure tümleşik yığını sistemleri

Azure tümleşik yığını sistemleri, bir Microsoft ve donanım iş ortakları ortaklık sunulur. Ortaklık Yönetimi'nde Basitlik denkleştirilir bulut hızını belirleyebileceği yenilik sunan bir çözümü oluşturur. Azure yığın donanım ve yazılım tümleşik bir sistem olarak sunulan olduğundan hala bulutta yenilik benimsenmesi sırasında esneklik ve Denetim doğru miktarda alın. Azure tümleşik yığını sistemleri 4 boyutu 12 düğümlere aralığı ve ortaklaşa donanım iş ortakları ve Microsoft tarafından desteklenir. Üretim iş yükleri için yeni senaryolar uygulamak için Azure tümleşik yığını sistemleri kullanın.

### <a name="azure-stack-development-kit"></a>Azure yığın Geliştirme Seti

Microsoft Azure yığın Geliştirme Seti değerlendirmek ve Azure yığın hakkında bilgi almak için kullanabileceğiniz Azure yığınının tek düğümlü dağıtımıdır. Burada API'lerini kullanarak geliştirebilirsiniz ve, tooling Azure ile tutarlı bir geliştirici ortamı olarak Azure yığın Geliştirme Seti de kullanabilirsiniz. Azure yığın Geliştirme Seti, bir üretim ortamına olarak kullanılmak üzere tasarlanmamıştır.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Azure karma bulut**

    [https://www.microsoft.com/cloud-Platform/Hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure yığını**

    [https://Azure.microsoft.com/Overview/Azure-Stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Windows kapsayıcıları için Active Directory hizmet hesapları**

    [https://docs.microsoft.com/Virtualization/windowscontainers/Manage-Containers/Manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Active Directory desteği olan bir kapsayıcı oluşturma**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/Create-a-Container-With-Active-Directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Azure karma avantajı lisanslama**

    [https://Azure.microsoft.com/pricing/Hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
[Önceki](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[sonraki](../walkthroughs-technical-get-started-overview.md)
