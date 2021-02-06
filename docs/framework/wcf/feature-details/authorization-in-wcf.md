---
description: Daha fazla bilgi için bkz. WCF 'de yetkilendirme
title: WCF'de Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 3fda699a33d8b512d047232398e9cfac63661a85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643715"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="67ea1-103">WCF'de Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="67ea1-103">Authorization in WCF</span></span>

<span data-ttu-id="67ea1-104">Yetkilendirme, hizmetler veya dosyalar gibi kaynaklara erişimi ve hakları denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="67ea1-104">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="67ea1-105">Bu bölümdeki konularda, bu temel görevin çeşitli yollarla Windows Communication Foundation (WCF) üzerinde nasıl gerçekleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="67ea1-105">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67ea1-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="67ea1-106">In This Section</span></span>  

 [<span data-ttu-id="67ea1-107">Erişim Denetimi Mekanizmaları</span><span class="sxs-lookup"><span data-stu-id="67ea1-107">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="67ea1-108">WCF 'de yetkilendirme mekanizmalarının kısa bir özetini ve önerilen kullanımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="67ea1-108">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="67ea1-109">Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama</span><span class="sxs-lookup"><span data-stu-id="67ea1-109">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="67ea1-110">İle bir hizmete erişimi kısıtlama sürecini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="67ea1-110">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="67ea1-111">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="67ea1-111">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="67ea1-112">ASP.NET 'in rol sağlayıcısı özelliğini kullanmasını sağlamak için bir hizmetin yapılandırılmasını adım adım açıklar.</span><span class="sxs-lookup"><span data-stu-id="67ea1-112">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="67ea1-113">Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="67ea1-113">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="67ea1-114">ASP.NET, bir Web sitesi için yetkilendirmeyi yönetmek üzere Yetkilendirme Yöneticisi 'ni kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="67ea1-114">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="67ea1-115">WCF, istemci yetkilendirmesi için ASP.NET/Authorization Manager bileşiminden benzer şekilde yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="67ea1-115">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="67ea1-116">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="67ea1-116">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="67ea1-117">Talep tabanlı yetkilendirme için kimlik modeli altyapısını kullanmanın temellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="67ea1-117">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="67ea1-118">Temsilcilik ve Kimliğe Bürünme</span><span class="sxs-lookup"><span data-stu-id="67ea1-118">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="67ea1-119">Temsil ve kimliğe bürünme arasındaki farkı açıklar.</span><span class="sxs-lookup"><span data-stu-id="67ea1-119">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="67ea1-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="67ea1-120">Reference</span></span>  

 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="67ea1-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="67ea1-121">Related Sections</span></span>  

 [<span data-ttu-id="67ea1-122">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="67ea1-122">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="67ea1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67ea1-123">See also</span></span>

- [<span data-ttu-id="67ea1-124">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="67ea1-124">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="67ea1-125">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="67ea1-125">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
