---
title: Bulutta yerel uygulamalarda kimlik doğrulama ve yetkilendirme
description: Azure için Cloud Native .NET uygulamaları tasarlama | Bulutta yerel uygulamalarda kimlik doğrulama ve yetkilendirme
ms.date: 05/13/2020
ms.openlocfilehash: bbd2df110dd7a7dc7363e9c07d87f1fa12f4e464
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161145"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a>Bulutta yerel uygulamalarda kimlik doğrulaması ve yetkilendirme

*Kimlik doğrulaması* , bir güvenlik sorumlusunun kimliğini belirleme işlemidir. *Yetkilendirme* , bir eylem gerçekleştirmek veya bir kaynağa erişmek için kimliği doğrulanmış bir sorumlu izin verme işlemidir. Bazen kimlik doğrulaması kısaltıldı `AuthN` ve yetkilendirme olarak kısaltıldı `AuthZ` . Her iki istemci ve uygulama da herhangi bir platformda veya cihazda dünyanın herhangi bir yerinden çalıştığından, bulutta yerel uygulamalar, güvenlik sorumlularının kimlik doğrulaması için açık HTTP tabanlı protokollere güvenmelidir. Tek ortak etken HTTP 'dir.

Birçok kuruluş hala Active Directory Federasyon Hizmetleri (AD FS) (ADFS) gibi yerel kimlik doğrulama hizmetlerini kullanır. Bu yaklaşım, şirket içi kimlik doğrulaması ihtiyaçlarına yönelik olarak kuruluşların iyi şekilde sunulmasını sağlarken, bulutta yerel uygulamalar, özellikle bulut için tasarlanan sistemlerden faydalanır. Son 2019 Birleşik Krallık Ulusal Cyber Güvenlik Merkezi (NCSC) danışmanlığı, "birincil kimlik doğrulama kaynağı olarak Azure AD kullanan kuruluşların, ADFS 'ye kıyasla risk azaltmasına neden olduğunu belirtir." [Bu analizde](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) özetlenen bazı nedenler şunlardır:

- Tüm Microsoft kimlik bilgileri koruma teknolojileri kümesine erişim.
- Çoğu kuruluş zaten Azure AD 'ye bir ölçüde bağlıdır.
- NTLM karmalarının çift karması, güvenliğinin, yerel Active Directory çalışan kimlik bilgilerine izin vermez.

## <a name="references"></a>Başvurular

- [Kimlik doğrulaması temel bilgileri](/azure/active-directory/develop/authentication-scenarios)
- [Belirteçleri ve talepleri erişim](/azure/active-directory/develop/access-tokens)
- [Şirket içi kimlik doğrulama hizmetlerinizin Ditch zaman alabilir](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
>[Önceki](identity.md) 
> [Sonraki](azure-active-directory.md)
