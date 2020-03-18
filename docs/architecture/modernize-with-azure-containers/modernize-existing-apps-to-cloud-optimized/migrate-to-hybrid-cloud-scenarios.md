---
title: Karma bulut senaryolarına geçiş
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Karma bulut senaryolarına geçiş
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937372"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Karma bulut senaryolarına geçiş

Bazı kuruluşlar ve kuruluşlar, düzenlemeler veya kendi ilkeleri nedeniyle bazı uygulamalarını Microsoft Azure veya başka bir genel bulut gibi genel bulutlara geçiremez. Ancak, herhangi bir kuruluşun bazı uygulamalarının genel bulutta ve diğer uygulamalarda şirket içinde olması ndan yararlanabileceği olasıdır. Ancak karışık bir ortam, genel bulutlarda kullanılan farklı platformlar ve teknolojiler ve şirket içi ortamlar nedeniyle ortamlarda aşırı karmaşıklığa yol açabilir.

Microsoft, bir Azure karma bulutta tutarlılık sağlarken, varolan varlıklarınızı şirket içinde ve genel bulutta optimize edebileceğiniz en iyi karma bulut çözümlerini sağlar. Azure Yığını (şirket içi) ve Azure (genel bulut) sayesinde varolan becerileri en üst düzeye çıkarabilir ve bulutta veya şirket içinde çalıştırılabilen uygulamalar oluşturmak için esnek ve birleşik bir yaklaşım elde edebilirsiniz.

Güvenlik söz konusu olduğunda, yönetim ve güvenliği karma bulutunuzda merkezileştirebilirsiniz. Şirket içi ve bulut uygulamalarına tek oturum açma sağlayarak veri merkezinizden buluta kadar tüm varlıkların kontrolünü edinebilirsiniz. Bunu, Active Directory'yi karma buluta genişleterek ve kimlik yönetimini kullanarak gerçekleştirebilirsiniz.

Son olarak, verileri sorunsuz bir şekilde dağıtabilir ve analiz edebilir, bulut ve şirket içi varlıklar için aynı sorgu dillerini kullanabilir ve kaynağıne bakılmaksızın verilerinizi zenginleştirmek için Azure'da analitik ve derin öğrenme uygulayabilirsiniz.

## <a name="azure-stack"></a>Azure Stack

Azure Yığını, kuruluşunuzun veri merkezinden Azure hizmetleri sunmanıza olanak tanıyan karma bir bulut platformudur. Azure Yığını, kenar ve bağlantısız ortamlar veya belirli güvenlik ve uyumluluk gereksinimlerini karşılama gibi önemli senaryolarda modern uygulamalarınız için yeni seçenekleri desteklemek üzere tasarlanmıştır.

Şekil 4-13, Microsoft'un sunduğu gerçek karma bulut platformuna genel bir bakış gösterir.

![Azure Yığını ve Azure ile Microsoft karma bulut platformu diyagramı.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Şekil 4-13.** Azure Yığını ve Azure ile Microsoft karma bulut platformu

Azure Yığını, gereksinimlerinizi karşılamak için iki dağıtım seçeneğinde sunulur:

- Azure Yığını tümleşik sistemleri

- Azure Yığını Geliştirme Kiti

### <a name="azure-stack-integrated-systems"></a>Azure Yığını tümleşik sistemleri

Azure Stack tümleşik sistemleri, Microsoft ve donanım iş ortaklarının ortaklığı yla sunulur. Ortaklık, yönetimde basitlikle dengelenmiş bulut tempolu bir yenilik sunan bir çözüm oluşturur. Azure Yığını entegre bir donanım ve yazılım sistemi olarak sunulduğundan, buluttan inovasyonu benimsemeye devam ederken doğru miktarda esneklik ve denetim elde edersiniz. Azure Stack tümleşik sistemlerinin boyutları 4 ile 12 arasında değişir ve donanım ortağı ve Microsoft tarafından ortaklaşa desteklenir. Üretim iş yükleriniçin yeni senaryolar uygulamak için Azure Yığını tümleşik sistemlerini kullanın.

### <a name="azure-stack-development-kit"></a>Azure Yığını Geliştirme Kiti

Microsoft Azure Yığını Geliştirme Kiti, Azure Yığını'nı değerlendirmek ve Azure Yığını hakkında bilgi edinmek için kullanabileceğiniz tek düğümlü bir Azure Yığını dağıtımıdır. Azure Yığını Geliştirme Kiti'ni, ApI'leri ve Azure ile tutarlı araçlar kullanarak geliştirebileceğiniz bir geliştirici ortamı olarak da kullanabilirsiniz. Azure Yığını Geliştirme Kiti'nin üretim ortamı olarak kullanılması amaçlanmamıştır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure karma bulut**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Windows Kapsayıcıları için Etkin Dizin Hizmet Hesapları**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Active Directory desteğine sahip bir kapsayıcı oluşturma**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Azure Karma Avantaj lisanslama**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Önceki](life-cycle-ci-cd-pipelines-devops-tools.md)
>[Sonraki](../walkthroughs-technical-get-started-overview.md)
