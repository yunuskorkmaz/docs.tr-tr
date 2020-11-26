---
title: WCF'de Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 67da01508fbb8f14b6405b79445bdef297e63288
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247492"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="66f8f-102">WCF'de Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="66f8f-102">Authorization in WCF</span></span>

<span data-ttu-id="66f8f-103">Yetkilendirme, hizmetler veya dosyalar gibi kaynaklara erişimi ve hakları denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="66f8f-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="66f8f-104">Bu bölümdeki konularda, bu temel görevin çeşitli yollarla Windows Communication Foundation (WCF) üzerinde nasıl gerçekleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="66f8f-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="66f8f-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="66f8f-105">In This Section</span></span>  

 [<span data-ttu-id="66f8f-106">Erişim Denetimi Mekanizmaları</span><span class="sxs-lookup"><span data-stu-id="66f8f-106">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="66f8f-107">WCF 'de yetkilendirme mekanizmalarının kısa bir özetini ve önerilen kullanımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="66f8f-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="66f8f-108">Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="66f8f-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="66f8f-109">İle bir hizmete erişimi kısıtlama sürecini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="66f8f-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="66f8f-110">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="66f8f-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="66f8f-111">ASP.NET 'in rol sağlayıcısı özelliğini kullanmasını sağlamak için bir hizmetin yapılandırılmasını adım adım açıklar.</span><span class="sxs-lookup"><span data-stu-id="66f8f-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="66f8f-112">Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="66f8f-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="66f8f-113">ASP.NET, bir Web sitesi için yetkilendirmeyi yönetmek üzere Yetkilendirme Yöneticisi 'ni kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="66f8f-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="66f8f-114">WCF, istemci yetkilendirmesi için ASP.NET/Authorization Manager bileşiminden benzer şekilde yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="66f8f-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="66f8f-115">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="66f8f-115">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="66f8f-116">Talep tabanlı yetkilendirme için kimlik modeli altyapısını kullanmanın temellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="66f8f-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="66f8f-117">Temsilcilik ve Kimliğe Bürünme</span><span class="sxs-lookup"><span data-stu-id="66f8f-117">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="66f8f-118">Temsil ve kimliğe bürünme arasındaki farkı açıklar.</span><span class="sxs-lookup"><span data-stu-id="66f8f-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="66f8f-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="66f8f-119">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="66f8f-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="66f8f-120">Related Sections</span></span>  

 [<span data-ttu-id="66f8f-121">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="66f8f-121">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="66f8f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66f8f-122">See also</span></span>

- [<span data-ttu-id="66f8f-123">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="66f8f-123">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="66f8f-124">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="66f8f-124">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
