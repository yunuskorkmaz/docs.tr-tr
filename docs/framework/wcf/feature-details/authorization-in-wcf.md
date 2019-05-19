---
title: WCF'de Yetkilendirme
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 8c605b310f19a05f994296d8f4268b91b408fb18
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881203"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="a4eee-102">WCF'de Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="a4eee-102">Authorization in WCF</span></span>
<span data-ttu-id="a4eee-103">Yetkilendirme, erişim ve kaynakları, hizmetleri ya da dosyalar gibi haklar denetleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a4eee-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="a4eee-104">Bu bölümdeki konular, çeşitli şekillerde Windows Communication Foundation (WCF) içinde temel bu görevi gerçekleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4eee-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4eee-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a4eee-105">In This Section</span></span>  
 [<span data-ttu-id="a4eee-106">Erişim Denetimi Mekanizmaları</span><span class="sxs-lookup"><span data-stu-id="a4eee-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="a4eee-107">WCF ve önerilen kullandığı yetkilendirme mekanizmalarını kısa bir özetini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4eee-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="a4eee-108">Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama</span><span class="sxs-lookup"><span data-stu-id="a4eee-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="a4eee-109">İle ilgili bir hizmete erişimi kısıtlamak işlemini gösterir <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a4eee-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="a4eee-110">Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="a4eee-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="a4eee-111">ASP.NET rol sağlayıcısını özelliğini kullanmasını sağlamak için bir hizmet yapılandırmasını size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4eee-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="a4eee-112">Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="a4eee-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="a4eee-113">ASP.NET Yetkilendirme Yöneticisi, bir Web sitesi için yetkilendirmeyi yönetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4eee-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="a4eee-114">WCF istemci yetkilendirme için ASP.NET/Authorization Manager birleşim benzer şekilde yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4eee-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="a4eee-115">Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="a4eee-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="a4eee-116">Beyana dayalı yetkilendirme için kimlik modeli altyapısı kullanmanın temellerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4eee-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="a4eee-117">Temsilcilik ve Kimliğe Bürünme</span><span class="sxs-lookup"><span data-stu-id="a4eee-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="a4eee-118">Temsilcilik ve kimliğe bürünme arasındaki farkı açıklar.</span><span class="sxs-lookup"><span data-stu-id="a4eee-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a4eee-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a4eee-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="a4eee-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a4eee-120">Related Sections</span></span>  
 [<span data-ttu-id="a4eee-121">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a4eee-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4eee-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4eee-122">See also</span></span>

- [<span data-ttu-id="a4eee-123">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a4eee-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="a4eee-124">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="a4eee-124">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
