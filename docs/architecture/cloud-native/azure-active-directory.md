---
title: Azure Active Directory
description: Azure için Cloud Native .NET uygulamaları tasarlama | Azure Active Directory
ms.date: 06/30/2019
ms.openlocfilehash: 55787f3565fc15bb25cf1a101aa5c1e3ddefe5e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161119"
---
# <a name="azure-active-directory"></a><span data-ttu-id="6469b-103">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="6469b-103">Azure Active Directory</span></span>

<span data-ttu-id="6469b-104">Microsoft Azure Active Directory (Azure AD), hizmet olarak kimlik ve erişim yönetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6469b-104">Microsoft Azure Active Directory (Azure AD) offers identity and access management as a service.</span></span> <span data-ttu-id="6469b-105">Müşteriler, kullanıcıların kim olduğunu, kendileri hakkında hangi bilgilerin depolanacağını, bu bilgilere kimlerin erişebileceğini, kimin yönetebileceğini ve hangi uygulamalara erişebileceğini yapılandırmak ve bakımını yapmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="6469b-105">Customers use it to configure and maintain who users are, what information to store about them, who can access that information, who can manage it, and what apps can access it.</span></span> <span data-ttu-id="6469b-106">AAD, bir çoklu oturum açma (SSO) deneyimi sunarak, bu kullanıcı tarafından kullanılmak üzere yapılandırılmış uygulamalar için kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="6469b-106">AAD can authenticate users for applications configured to use it, providing a single sign-on (SSO) experience.</span></span> <span data-ttu-id="6469b-107">Bu, kendi başına kullanılabilir veya şirket içinde çalışan Windows AD ile tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6469b-107">It can be used on its own or be integrated with Windows AD running on premises.</span></span>

<span data-ttu-id="6469b-108">Azure AD, bulut için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="6469b-108">Azure AD is built for the cloud.</span></span> <span data-ttu-id="6469b-109">Bu, LDAP kullanan Windows AD 'nin aksine, sorgular için REST tabanlı Graph API ve OData söz dizimini kullanan, gerçek bir bulut Yerel kimlik çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="6469b-109">It's truly a cloud-native identity solution that uses a REST-based Graph API and OData syntax for queries, unlike Windows AD, which uses LDAP.</span></span> <span data-ttu-id="6469b-110">Şirket içi Active Directory, kimlik eşitleme hizmetleri 'ni kullanarak Kullanıcı özniteliklerini buluta eşitleyebilir ve Azure AD kullanarak tüm kimlik doğrulamanın bulutta yer geçirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6469b-110">On premises Active Directory can sync user attributes to the cloud using Identity Sync Services, allowing all authentication to take place in the cloud using Azure AD.</span></span> <span data-ttu-id="6469b-111">Alternatif olarak, kimlik doğrulaması, şirket içi Windows AD tarafından tamamlanmak üzere ADFS aracılığıyla yerel Active Directory geri dönmek için Bağlan aracılığıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6469b-111">Alternately, authentication can be configured via Connect to pass back to local Active Directory via ADFS to be completed by Windows AD on premises.</span></span>

<span data-ttu-id="6469b-112">Azure AD, şirket markalı oturum açma ekranlarını, çok fabrika kimlik doğrulamasını ve şirket içinde barındırılan uygulamalar için SSO sağlamak üzere kullanılan bulut tabanlı uygulama proxy 'lerini destekler.</span><span class="sxs-lookup"><span data-stu-id="6469b-112">Azure AD supports company branded sign-in screens, multi-factory authentication, and cloud-based application proxies that are used to provide SSO for applications hosted on premises.</span></span> <span data-ttu-id="6469b-113">Farklı türlerde güvenlik raporlama ve uyarı özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="6469b-113">It offers different kinds of security reporting and alert capabilities.</span></span>

## <a name="references"></a><span data-ttu-id="6469b-114">Başvurular</span><span class="sxs-lookup"><span data-stu-id="6469b-114">References</span></span>

- [<span data-ttu-id="6469b-115">Microsoft kimlik platformu</span><span class="sxs-lookup"><span data-stu-id="6469b-115">Microsoft identity platform</span></span>](/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="6469b-116">[Önceki](authentication-authorization.md) 
> [Sonraki](identity-server.md)</span><span class="sxs-lookup"><span data-stu-id="6469b-116">[Previous](authentication-authorization.md)
[Next](identity-server.md)</span></span>
