---
title: Bulutta yerel uygulamalarda kimlik doğrulama ve yetkilendirme
description: Azure için Cloud Native .NET uygulamaları tasarlama | Bulutta yerel uygulamalarda kimlik doğrulama ve yetkilendirme
ms.date: 05/13/2020
ms.openlocfilehash: e5254560ac82662e5e3ea6a25997516cd2b478b0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614311"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="d11df-103">Bulutta yerel uygulamalarda kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="d11df-103">Authentication and authorization in cloud-native apps</span></span>

<span data-ttu-id="d11df-104">*Kimlik doğrulaması* , bir güvenlik sorumlusunun kimliğini belirleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="d11df-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="d11df-105">*Yetkilendirme* , bir eylem gerçekleştirmek veya bir kaynağa erişmek için kimliği doğrulanmış bir sorumlu izin verme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="d11df-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="d11df-106">Bazen kimlik doğrulaması kısaltıldı `AuthN` ve yetkilendirme olarak kısaltıldı `AuthZ` .</span><span class="sxs-lookup"><span data-stu-id="d11df-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="d11df-107">Her iki istemci ve uygulama da herhangi bir platformda veya cihazda dünyanın herhangi bir yerinden çalıştığından, bulutta yerel uygulamalar, güvenlik sorumlularının kimlik doğrulaması için açık HTTP tabanlı protokollere güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d11df-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="d11df-108">Tek ortak etken HTTP 'dir.</span><span class="sxs-lookup"><span data-stu-id="d11df-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="d11df-109">Birçok kuruluş hala Active Directory Federasyon Hizmetleri (AD FS) (ADFS) gibi yerel kimlik doğrulama hizmetlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d11df-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="d11df-110">Bu yaklaşım, şirket içi kimlik doğrulaması ihtiyaçlarına yönelik olarak kuruluşların iyi şekilde sunulmasını sağlarken, bulutta yerel uygulamalar, özellikle bulut için tasarlanan sistemlerden faydalanır.</span><span class="sxs-lookup"><span data-stu-id="d11df-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="d11df-111">Son 2019 Birleşik Krallık Ulusal Cyber Güvenlik Merkezi (NCSC) danışmanlığı, "birincil kimlik doğrulama kaynağı olarak Azure AD kullanan kuruluşların, ADFS 'ye kıyasla risk azaltmasına neden olduğunu belirtir."</span><span class="sxs-lookup"><span data-stu-id="d11df-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="d11df-112">[Bu analizde](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) özetlenen bazı nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d11df-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="d11df-113">Tüm Microsoft kimlik bilgileri koruma teknolojileri kümesine erişim.</span><span class="sxs-lookup"><span data-stu-id="d11df-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="d11df-114">Çoğu kuruluş zaten Azure AD 'ye bir ölçüde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d11df-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="d11df-115">NTLM karmalarının çift karması, güvenliğinin, yerel Active Directory çalışan kimlik bilgilerine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="d11df-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="d11df-116">Başvurular</span><span class="sxs-lookup"><span data-stu-id="d11df-116">References</span></span>

- [<span data-ttu-id="d11df-117">Kimlik doğrulaması temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="d11df-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="d11df-118">Belirteçleri ve talepleri erişim</span><span class="sxs-lookup"><span data-stu-id="d11df-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="d11df-119">Şirket içi kimlik doğrulama hizmetlerinizin Ditch zaman alabilir</span><span class="sxs-lookup"><span data-stu-id="d11df-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="d11df-120">[Önceki](identity.md) 
> [Sonraki](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="d11df-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
