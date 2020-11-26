---
title: WCF'de Kimlik Doğrulama
description: WCF 'de, Windows kimlik doğrulaması, X. 509.440 sertifikaları ve Kullanıcı adı ve parola gibi kimlik doğrulaması sağlayan çeşitli mekanizmalar hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: e2334a8c024238f38e1c927a278a4e25e7dabd9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247544"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="35529-103">WCF'de Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="35529-103">Authentication in WCF</span></span>

<span data-ttu-id="35529-104">Aşağıdaki konularda, kimlik doğrulaması (örneğin, Windows kimlik doğrulaması, X. 509.440 sertifikaları ve Kullanıcı adı ve parolalar) sağlayan Windows Communication Foundation (WCF) içinde çeşitli mekanizmalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="35529-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35529-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="35529-105">In This Section</span></span>  

 [<span data-ttu-id="35529-106">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="35529-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="35529-107">ASP.NET özellikleri bir üyelik ve rol sağlayıcısı, kimlik doğrulaması için Kullanıcı adı/parola çiftlerini depolamak üzere bir veritabanı ve yetkilendirme için Kullanıcı rolleri içerir.</span><span class="sxs-lookup"><span data-stu-id="35529-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="35529-108">Bu konuda, WCF hizmetlerinin, kullanıcıların kimliğini doğrulamak ve yetkilendirmek için aynı veritabanını nasıl kullanabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35529-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="35529-109">Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="35529-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="35529-110">Özel bir Kullanıcı adı/parola doğrulayıcının nasıl tümleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="35529-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="35529-111">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="35529-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="35529-112">Bir istemci, ek bir güvenlik önlemi olarak hizmetin beklenen *kimliğini* belirterek hizmetin kimliğini doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="35529-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="35529-113">Beklenen kimlik ve hizmet tarafından döndürülen kimlik eşleşmiyorsa, kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="35529-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="35529-114">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="35529-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="35529-115">Sınıfında özelliğinin nasıl kullanılacağını açıklar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> .</span><span class="sxs-lookup"><span data-stu-id="35529-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="35529-116">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="35529-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="35529-117">Windows kimlik doğrulaması kullanılırken karşılaşılan yaygın sorunlara odaklanır.</span><span class="sxs-lookup"><span data-stu-id="35529-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="35529-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="35529-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="35529-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="35529-119">Related Sections</span></span>  

 [<span data-ttu-id="35529-120">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="35529-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="35529-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35529-121">See also</span></span>

- [<span data-ttu-id="35529-122">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="35529-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="35529-123">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="35529-123">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
