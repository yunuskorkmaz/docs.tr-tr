---
title: WCF'de Yetkilendirme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0c2afafa1d645ec0e95b7b41ff8389873969c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="d493a-102">WCF'de Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="d493a-102">Authorization in WCF</span></span>
<span data-ttu-id="d493a-103">Yetkilendirme access ve Hizmetleri ya da dosyalar gibi kaynaklara hakları denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="d493a-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="d493a-104">Bu bölümdeki konular, bu temel görevi gerçekleştirmek nasıl Göster [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] çeşitli şekillerde.</span><span class="sxs-lookup"><span data-stu-id="d493a-104">The topics in this section show you how to perform this basic task in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d493a-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d493a-105">In This Section</span></span>  
 [<span data-ttu-id="d493a-106">Erişim denetimi mekanizmaları</span><span class="sxs-lookup"><span data-stu-id="d493a-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="d493a-107">İçinde yetkilendirme mekanizmaları kısa bir özeti sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ve önerilen kullanır.</span><span class="sxs-lookup"><span data-stu-id="d493a-107">Provides a brief outline of the authorization mechanisms in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and suggested uses.</span></span>  
  
 [<span data-ttu-id="d493a-108">Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama</span><span class="sxs-lookup"><span data-stu-id="d493a-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="d493a-109">Bir hizmetle erişimi kısıtlama sürecini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d493a-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="d493a-110">Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="d493a-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="d493a-111">Rol Sağlayıcısı'nın özelliğini kullanmasını sağlamak için bir hizmet yapılandırması anlatılmaktadır [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d493a-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="d493a-112">Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="d493a-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="d493a-113">Yetkilendirme Yöneticisi'ni bir Web sitesi için yetkilendirme yönetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d493a-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d493a-114">benzer şekilde Dengeleme yapabilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]istemcilerin yetkilendirme için /Authorization Yöneticisi birleşimi.</span><span class="sxs-lookup"><span data-stu-id="d493a-114"> can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="d493a-115">Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme</span><span class="sxs-lookup"><span data-stu-id="d493a-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="d493a-116">Talep tabanlı yetkilendirme kimlik modeli altyapısını kullanarak temellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d493a-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="d493a-117">Temsilcilik ve kimliğe bürünme</span><span class="sxs-lookup"><span data-stu-id="d493a-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="d493a-118">Temsilcilik ve kimliğe bürünme arasındaki farkı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d493a-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d493a-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d493a-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="d493a-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d493a-120">Related Sections</span></span>  
 [<span data-ttu-id="d493a-121">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d493a-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="d493a-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d493a-122">See Also</span></span>  
 [<span data-ttu-id="d493a-123">Güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="d493a-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="d493a-124">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="d493a-124">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
