---
title: WCF'de Kimlik Doğrulama
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 22bfd7edf0ca0e9eb57e63c168c783f25782d607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523928"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="88e64-102">WCF'de Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="88e64-102">Authentication in WCF</span></span>
<span data-ttu-id="88e64-103">Aşağıdaki konular, kimlik doğrulama, örneğin sağlayan Windows Communication Foundation (WCF), Windows kimlik doğrulaması, X.509 sertifikaları ve kullanıcı adı ve parola farklı mekanizmalar sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88e64-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88e64-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="88e64-104">In This Section</span></span>  
 [<span data-ttu-id="88e64-105">Nasıl yapılır: ASP.NET üyelik sağlayıcısını kullanma</span><span class="sxs-lookup"><span data-stu-id="88e64-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="88e64-106">ASP.NET özellikleri, kullanıcı adı/parola çiftleri için kimlik doğrulaması ve yetkilendirme için kullanıcı rolleri depolamak için bir üyelik ve rol sağlayıcısı, bir veritabanı içerir.</span><span class="sxs-lookup"><span data-stu-id="88e64-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="88e64-107">Bu konuda, WCF hizmetleri kimliğini doğrulamak ve kullanıcılara yetki vermek için aynı veritabanını nasıl kullanabileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="88e64-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="88e64-108">Nasıl yapılır: Özel bir kullanıcı adı ve parola Doğrulayıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="88e64-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="88e64-109">Nasıl bir özel kullanıcı adı/parola Doğrulayıcı ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="88e64-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="88e64-110">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="88e64-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="88e64-111">Ek bir koruyucu olarak beklenen belirterek istemci hizmetin kimliğini *kimlik* hizmeti.</span><span class="sxs-lookup"><span data-stu-id="88e64-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="88e64-112">Beklenen kimliği ve hizmet tarafından döndürülen kimlik eşleşmiyorsa, kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="88e64-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="88e64-113">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="88e64-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="88e64-114">Nasıl kullanılacağını açıklar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> özelliğinde <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="88e64-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="88e64-115">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="88e64-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="88e64-116">Windows kimlik doğrulamasını kullanırken sık karşılaşılan sorunlar odaklanır.</span><span class="sxs-lookup"><span data-stu-id="88e64-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="88e64-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="88e64-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="88e64-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="88e64-118">Related Sections</span></span>  
 [<span data-ttu-id="88e64-119">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="88e64-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="88e64-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88e64-120">See also</span></span>
- [<span data-ttu-id="88e64-121">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="88e64-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="88e64-122">Windows Server AppFabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="88e64-122">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
