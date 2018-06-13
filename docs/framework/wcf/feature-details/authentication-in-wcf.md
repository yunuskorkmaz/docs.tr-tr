---
title: WCF'de Kimlik Doğrulama
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: a4f9b719024db1334b599f0f02fe01bc083bf3c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489117"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="bd5e1-102">WCF'de Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="bd5e1-102">Authentication in WCF</span></span>
<span data-ttu-id="bd5e1-103">Aşağıdaki konular, kimlik doğrulama, örneğin sağlayan Windows Communication Foundation (WCF), Windows kimlik doğrulaması, X.509 sertifikaları ve kullanıcı adı ve parolaları farklı mekanizmaları sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd5e1-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bd5e1-104">In This Section</span></span>  
 [<span data-ttu-id="bd5e1-105">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="bd5e1-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="bd5e1-106">ASP.NET özellikleri, kullanıcı adı/parola çiftleri kimlik doğrulaması ve yetkilendirme için kullanıcı rollerini depolamak için bir üyelik ve rol sağlayıcısı, bir veritabanı içerir.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="bd5e1-107">Bu konu, WCF hizmetleri kimlik doğrulaması ve kullanıcılara yetki vermek için aynı veritabanını nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="bd5e1-108">Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="bd5e1-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="bd5e1-109">Özel kullanıcı adı/parola Doğrulayıcı tümleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="bd5e1-110">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="bd5e1-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="bd5e1-111">Ek bir koruyucu olarak beklenen belirterek istemci hizmetin kimliğini *kimlik* hizmetinin.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="bd5e1-112">Beklenen kimlik ve hizmet tarafından döndürülen kimlik eşleşmiyorsa, kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="bd5e1-113">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="bd5e1-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="bd5e1-114">Nasıl kullanılacağını açıklar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> özelliğinde <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="bd5e1-115">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bd5e1-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="bd5e1-116">Windows kimlik doğrulamasını kullanırken sık karşılaşılan sorunlar odaklanır.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bd5e1-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="bd5e1-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="bd5e1-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="bd5e1-118">Related Sections</span></span>  
 [<span data-ttu-id="bd5e1-119">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="bd5e1-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd5e1-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd5e1-120">See Also</span></span>  
 [<span data-ttu-id="bd5e1-121">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bd5e1-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="bd5e1-122">Windows Server App Fabric için güvenlik modeli</span><span class="sxs-lookup"><span data-stu-id="bd5e1-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
