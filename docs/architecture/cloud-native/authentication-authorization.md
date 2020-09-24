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
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="c5254-103">Bulutta yerel uygulamalarda kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="c5254-103">Authentication and authorization in cloud-native apps</span></span>

<span data-ttu-id="c5254-104">*Kimlik doğrulaması* , bir güvenlik sorumlusunun kimliğini belirleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="c5254-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="c5254-105">*Yetkilendirme* , bir eylem gerçekleştirmek veya bir kaynağa erişmek için kimliği doğrulanmış bir sorumlu izin verme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="c5254-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="c5254-106">Bazen kimlik doğrulaması kısaltıldı `AuthN` ve yetkilendirme olarak kısaltıldı `AuthZ` .</span><span class="sxs-lookup"><span data-stu-id="c5254-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="c5254-107">Her iki istemci ve uygulama da herhangi bir platformda veya cihazda dünyanın herhangi bir yerinden çalıştığından, bulutta yerel uygulamalar, güvenlik sorumlularının kimlik doğrulaması için açık HTTP tabanlı protokollere güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5254-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="c5254-108">Tek ortak etken HTTP 'dir.</span><span class="sxs-lookup"><span data-stu-id="c5254-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="c5254-109">Birçok kuruluş hala Active Directory Federasyon Hizmetleri (AD FS) (ADFS) gibi yerel kimlik doğrulama hizmetlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5254-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="c5254-110">Bu yaklaşım, şirket içi kimlik doğrulaması ihtiyaçlarına yönelik olarak kuruluşların iyi şekilde sunulmasını sağlarken, bulutta yerel uygulamalar, özellikle bulut için tasarlanan sistemlerden faydalanır.</span><span class="sxs-lookup"><span data-stu-id="c5254-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="c5254-111">Son 2019 Birleşik Krallık Ulusal Cyber Güvenlik Merkezi (NCSC) danışmanlığı, "birincil kimlik doğrulama kaynağı olarak Azure AD kullanan kuruluşların, ADFS 'ye kıyasla risk azaltmasına neden olduğunu belirtir."</span><span class="sxs-lookup"><span data-stu-id="c5254-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="c5254-112">[Bu analizde](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) özetlenen bazı nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c5254-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="c5254-113">Tüm Microsoft kimlik bilgileri koruma teknolojileri kümesine erişim.</span><span class="sxs-lookup"><span data-stu-id="c5254-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="c5254-114">Çoğu kuruluş zaten Azure AD 'ye bir ölçüde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5254-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="c5254-115">NTLM karmalarının çift karması, güvenliğinin, yerel Active Directory çalışan kimlik bilgilerine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c5254-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="c5254-116">Başvurular</span><span class="sxs-lookup"><span data-stu-id="c5254-116">References</span></span>

- [<span data-ttu-id="c5254-117">Kimlik doğrulaması temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="c5254-117">Authentication basics</span></span>](/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="c5254-118">Belirteçleri ve talepleri erişim</span><span class="sxs-lookup"><span data-stu-id="c5254-118">Access tokens and claims</span></span>](/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="c5254-119">Şirket içi kimlik doğrulama hizmetlerinizin Ditch zaman alabilir</span><span class="sxs-lookup"><span data-stu-id="c5254-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="c5254-120">[Önceki](identity.md) 
> [Sonraki](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="c5254-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
