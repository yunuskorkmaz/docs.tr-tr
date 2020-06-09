---
title: Davranış Güvenliği
ms.date: 03/30/2017
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
ms.openlocfilehash: 5d09fcc2068133b3bb302850a647a2539ab07ee3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575595"
---
# <a name="behavior-security"></a><span data-ttu-id="6d29c-102">Davranış Güvenliği</span><span class="sxs-lookup"><span data-stu-id="6d29c-102">Behavior Security</span></span>
<span data-ttu-id="6d29c-103">Bu bölüm, hizmet davranışlarını için güvenliği yapılandırmayı gösteren örnekleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6d29c-103">This section includes samples that demonstrate configuring security for service behaviors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d29c-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6d29c-104">In This Section</span></span>  
 [<span data-ttu-id="6d29c-105">Hizmet Denetleme Davranışı</span><span class="sxs-lookup"><span data-stu-id="6d29c-105">Service Auditing Behavior</span></span>](service-auditing-behavior.md)  
 <span data-ttu-id="6d29c-106">Bu örnek, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirmek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d29c-106">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span>  
  
 [<span data-ttu-id="6d29c-107">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="6d29c-107">Membership and Role Provider</span></span>](membership-and-role-provider.md)  
 <span data-ttu-id="6d29c-108">Bu örnekte, bir hizmetin, istemcilerin kimliğini doğrulamak ve yetkilendirmek için ASP.NET üyeliğini ve rol sağlayıcılarını nasıl kullanabileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6d29c-108">This sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 [<span data-ttu-id="6d29c-109">Hizmet İşlemlerine Erişimi Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="6d29c-109">Authorizing Access to Service Operations</span></span>](authorizing-access-to-service-operations.md)  
 <span data-ttu-id="6d29c-110">Bu örnek, [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet işlemlerine erişim yetkisi vermek için özniteliğinin kullanımını etkinleştirmek üzere öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d29c-110">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span>  
  
 [<span data-ttu-id="6d29c-111">İstemci Kimliğine Bürünme</span><span class="sxs-lookup"><span data-stu-id="6d29c-111">Impersonating the Client</span></span>](impersonating-the-client.md)  
 <span data-ttu-id="6d29c-112">Bu örnek, hizmetin çağıran adına sistem kaynaklarına erişebilmesi için, hizmette çağıran uygulamanın özelliklerini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d29c-112">This sample demonstrates how to impersonate the caller application at the service so that the service can access system resources on behalf of the caller.</span></span>
