---
title: Buluta özgü uygulamalarda kimlik doğrulama ve yetkilendirme
description: Azure için Cloud Native .NET Uygulamalarını Temel Alma | Bulut Yerel Uygulamalarında Kimlik Doğrulama ve Yetkilendirme
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805548"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Bulutta yerel uygulamalarda kimlik doğrulaması ve yetkilendirme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

*Kimlik doğrulama,* bir güvenlik ilkesinin kimliğini belirleme işlemidir. *Yetkilendirme,* bir eylemi gerçekleştirmek veya kaynağa erişmek için kimlik doğrulaması verilen bir asıl izin verme eylemidir. Bazen kimlik doğrulama kısaltılır `AuthN` ve yetkilendirme `AuthZ`' ya kısaltılır. Hem istemciler hem de uygulamalar dünyanın herhangi bir platformuveya aygıtında çalışıyor olabileceğinden, bulut tabanlı uygulamaların güvenlik ilkelerini doğrulamak için açık HTTP tabanlı protokollere dayanması gerekir. Tek ortak faktör HTTP'dir.

Birçok kuruluş hala Active Directory Federation Services (ADFS) gibi yerel kimlik doğrulama hizmetlerine güvenir. Bu yaklaşım geleneksel olarak kuruluşlara şirket içi kimlik doğrulama gereksinimlerine iyi hizmet etmiş olsa da, bulut yerel uygulamalar bulut için özel olarak tasarlanmış sistemlerden yararlanır. Yakın tarihli bir 2019 Birleşik Krallık Ulusal Siber Güvenlik Merkezi (NCSC) danışma belgesinde, "Azure AD'yi birincil kimlik doğrulama kaynağı olarak kullanan kuruluşların ADFS'ye göre risklerini düşüreceği" belirtiliyor. [Bu analizde](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) özetlenen bazı nedenler şunlardır:

- Tam microsoft kimlik bilgisi koruma teknolojilerine erişim.
- Çoğu kuruluş bir dereceye kadar Azure AD'ye güveniyor.
- NTLM karmalarının çift karma olması, yerel Active Directory'de çalışan kimlik bilgilerinin uzlaştırılmamasından ödün verir.

## <a name="references"></a>Başvurular

- [Kimlik doğrulaması temel bilgileri](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [Erişim belirteçleri ve talepler](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [Şirket içi kimlik doğrulama hizmetlerinizi bırakmanın zamanı gelebilir](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Önceki](identity.md)
>[Sonraki](azure-active-directory.md)
