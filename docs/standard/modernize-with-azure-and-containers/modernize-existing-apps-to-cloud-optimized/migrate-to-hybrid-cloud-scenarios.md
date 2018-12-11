---
title: Karma bulut senaryolarına geçiş
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Karma bulut senaryolarına geçiş
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 3d6fc272854654d890559d5db032b05667627d94
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147352"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Karma bulut senaryolarına geçiş

Bazı kuruluşlar ve işletmeler, bazı Microsoft Azure gibi genel Bulutlar, uygulamalarına veya diğer genel bulut düzenlemeler veya kendi ilkeleri nedeniyle geçiremezsiniz. Ancak, bazı müşterilerin uygulamalarını genel bulutta ve diğer şirket içi uygulamaları sahip her kuruluş yararlanabilecek olasıdır. Ancak, karma bir ortamda ortamlarda farklı platformları ve şirket içi ortamlara ve genel bulutlarda kullanılan teknolojiler nedeniyle aşırı karmaşıklıktan yol açabilir.

Microsoft sağladığı en iyi hibrit bulut çözümü, size en iyi duruma getirebilir mevcut varlıklarınızı bir şirket içi ve Azure hibrit bulut tutarlılığı sırada genel bulutta. Mevcut becerilerinizi en üst düzeye çıkarmak ve bulutta veya şirket içi, Azure Stack (şirket) ve Azure (genel bulut) sayesinde çalışabilen uygulamalar oluşturmak için esnek ve birleşik bir yaklaşım elde edin.

Güvenlik geldiğinde, yönetim ve güvenlik arasında karma bulutunuzu merkezileştirebilirsiniz. Şirket içi çoklu oturum açma sağlayarak tüm varlıklar üzerinde denetim veri merkezinizi buluta alın ve bulut uygulamaları. Bu Active Directory karma buluta genişleterek ve kimlik yönetimi kullanarak gerçekleştirirsiniz.

Son olarak, dağıtın ve verileri sorunsuz bir şekilde analiz, Bulut ve şirket içi varlıkları için aynı sorgu dilini kullanın ve analiz ve derin öğrenme azure'da verilerinizi kaynağından bağımsız olarak zenginleştirin için geçerlidir.

## <a name="azure-stack"></a>Azure Stack

Azure Stack, kuruluşunuzun veri merkezinden Azure Hizmetleri elde etmenizi sağlayan bir karma bulut platformudur. Azure Stack, edge ve bağlantısız ortamlarda veya toplantı belirli güvenlik ve uyumluluk gereksinimlerini gibi anahtar senaryolar, modern uygulamalar için yeni seçenekler desteklemek için tasarlanmıştır.

Şekil 4-13, Microsoft'un sunduğu gerçek hibrit bulut platformu özetini gösterir.

![Azure Stack ve Azure ile Microsoft hibrit bulut platformu](./media/image13.jpg)

> **Şekil 4-13.** Azure Stack ve Azure ile Microsoft hibrit bulut platformu

Azure Stack, gereksinimlerinizi karşılamak üzere iki dağıtım seçenekleri sunulur:

-   Azure Stack tümleşik sistemleri

-   Azure Stack Geliştirme Seti

### <a name="azure-stack-integrated-systems"></a>Azure Stack tümleşik sistemleri

Azure Stack tümleşik sistemleri, Microsoft ve donanım iş ortaklarından oluşan bir iş ortaklığı sunulur. İş ortaklığı, basitçe yönetim olanağı sunan bulut hızını sizin belirlediğiniz yenilik sunan bir çözüm oluşturur. Azure Stack, donanım ve yazılım tümleşik bir sistem halinde sunulur çünkü hala buluttan yenilik benimseme sırasında esneklik ve denetim, doğru miktarda alın. Azure Stack tümleşik sistemleri 12 düğümlere boyutu 4'ten aralık ve tüm dünyada donanım iş ortağı ve Microsoft tarafından desteklenir. Üretim iş yükleriniz için yeni senaryolar uygulamak için Azure Stack tümleşik sistemleri kullanın.

### <a name="azure-stack-development-kit"></a>Azure Stack Geliştirme Seti

Microsoft Azure Stack geliştirme Seti'ni değerlendirmek ve Azure Stack hakkında bilgi edinmek için kullanabileceğiniz Azure Stack, tek düğümlü dağıtımıdır. Burada API'lerini kullanarak geliştirebilirsiniz ve Araçlar Azure ile tutarlı bir geliştirme ortamı olarak Azure Stack Geliştirme Seti de kullanabilirsiniz. Azure Stack Geliştirme Seti, bir üretim ortamı olarak kullanılmak üzere tasarlanmamıştır.

### <a name="additional-resources"></a>Ek kaynaklar

-   **Azure hibrit bulut**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Windows kapsayıcıları için Active Directory hizmet hesapları**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Active Directory desteği ile bir kapsayıcı oluşturma**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Azure hibrit avantajı lisanslama**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
>[Önceki](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[İleri](../walkthroughs-technical-get-started-overview.md)