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
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="a2ee1-103">Bulutta yerel uygulamalarda kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="a2ee1-103">Authentication and authorization in cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a2ee1-104">*Kimlik doğrulama,* bir güvenlik ilkesinin kimliğini belirleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="a2ee1-105">*Yetkilendirme,* bir eylemi gerçekleştirmek veya kaynağa erişmek için kimlik doğrulaması verilen bir asıl izin verme eylemidir.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="a2ee1-106">Bazen kimlik doğrulama kısaltılır `AuthN` ve yetkilendirme `AuthZ`' ya kısaltılır.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="a2ee1-107">Hem istemciler hem de uygulamalar dünyanın herhangi bir platformuveya aygıtında çalışıyor olabileceğinden, bulut tabanlı uygulamaların güvenlik ilkelerini doğrulamak için açık HTTP tabanlı protokollere dayanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="a2ee1-108">Tek ortak faktör HTTP'dir.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="a2ee1-109">Birçok kuruluş hala Active Directory Federation Services (ADFS) gibi yerel kimlik doğrulama hizmetlerine güvenir.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="a2ee1-110">Bu yaklaşım geleneksel olarak kuruluşlara şirket içi kimlik doğrulama gereksinimlerine iyi hizmet etmiş olsa da, bulut yerel uygulamalar bulut için özel olarak tasarlanmış sistemlerden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="a2ee1-111">Yakın tarihli bir 2019 Birleşik Krallık Ulusal Siber Güvenlik Merkezi (NCSC) danışma belgesinde, "Azure AD'yi birincil kimlik doğrulama kaynağı olarak kullanan kuruluşların ADFS'ye göre risklerini düşüreceği" belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="a2ee1-112">[Bu analizde](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) özetlenen bazı nedenler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a2ee1-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="a2ee1-113">Tam microsoft kimlik bilgisi koruma teknolojilerine erişim.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="a2ee1-114">Çoğu kuruluş bir dereceye kadar Azure AD'ye güveniyor.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="a2ee1-115">NTLM karmalarının çift karma olması, yerel Active Directory'de çalışan kimlik bilgilerinin uzlaştırılmamasından ödün verir.</span><span class="sxs-lookup"><span data-stu-id="a2ee1-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="a2ee1-116">Başvurular</span><span class="sxs-lookup"><span data-stu-id="a2ee1-116">References</span></span>

- [<span data-ttu-id="a2ee1-117">Kimlik doğrulaması temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="a2ee1-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="a2ee1-118">Erişim belirteçleri ve talepler</span><span class="sxs-lookup"><span data-stu-id="a2ee1-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="a2ee1-119">Şirket içi kimlik doğrulama hizmetlerinizi bırakmanın zamanı gelebilir</span><span class="sxs-lookup"><span data-stu-id="a2ee1-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="a2ee1-120">[Önceki](identity.md)
>[Sonraki](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="a2ee1-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
