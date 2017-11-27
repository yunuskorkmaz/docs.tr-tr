---
title: "WCF'de Kimlik Doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6fbd4a322153bd9f560b6c039f586100770a0216
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="e0af8-102">WCF'de Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="e0af8-102">Authentication in WCF</span></span>
<span data-ttu-id="e0af8-103">Aşağıdaki konular de farklı mekanizmaları sayısını gösterir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kimlik doğrulama, örneğin, Windows kimlik doğrulaması, X.509 sertifikaları ve kullanıcı adı ve parola sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e0af8-103">The following topics show a number of different mechanisms in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0af8-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e0af8-104">In This Section</span></span>  
 [<span data-ttu-id="e0af8-105">Nasıl yapılır: ASP.NET üyelik sağlayıcısı kullanın</span><span class="sxs-lookup"><span data-stu-id="e0af8-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="e0af8-106">ASP.NET özellikleri, kullanıcı adı/parola çiftleri kimlik doğrulaması ve yetkilendirme için kullanıcı rollerini depolamak için bir üyelik ve rol sağlayıcısı, bir veritabanı içerir.</span><span class="sxs-lookup"><span data-stu-id="e0af8-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="e0af8-107">Bu konuda açıklanmaktadır nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri kimliğini doğrulamak ve kullanıcılara yetki vermek için aynı veritabanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0af8-107">This topic explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="e0af8-108">Nasıl yapılır: özel bir kullanıcı adı ve parola Doğrulayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="e0af8-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="e0af8-109">Özel kullanıcı adı/parola Doğrulayıcı tümleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e0af8-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="e0af8-110">Hizmet kimliği ve kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e0af8-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="e0af8-111">Ek bir koruyucu olarak beklenen belirterek istemci hizmetin kimliğini *kimlik* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="e0af8-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="e0af8-112">Beklenen kimlik ve hizmet tarafından döndürülen kimlik eşleşmiyorsa, kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e0af8-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="e0af8-113">Güvenlik görüşmeleri ve zaman aşımları</span><span class="sxs-lookup"><span data-stu-id="e0af8-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="e0af8-114">Nasıl kullanılacağını açıklar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> özelliğinde <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e0af8-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="e0af8-115">Windows kimlik doğrulama hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="e0af8-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="e0af8-116">Windows kimlik doğrulamasını kullanırken sık karşılaşılan sorunlar odaklanır.</span><span class="sxs-lookup"><span data-stu-id="e0af8-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e0af8-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e0af8-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="e0af8-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0af8-118">Related Sections</span></span>  
 [<span data-ttu-id="e0af8-119">Ortak Güvenlik senaryoları</span><span class="sxs-lookup"><span data-stu-id="e0af8-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0af8-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0af8-120">See Also</span></span>  
 [<span data-ttu-id="e0af8-121">Güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="e0af8-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="e0af8-122">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="e0af8-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
