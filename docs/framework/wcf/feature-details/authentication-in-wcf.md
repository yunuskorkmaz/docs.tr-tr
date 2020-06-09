---
title: WCF'de Kimlik Doğrulama
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: b513c9713bd2c04e125915d1a0a87c86ce249666
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597650"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="38a59-102">WCF'de Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="38a59-102">Authentication in WCF</span></span>
<span data-ttu-id="38a59-103">Aşağıdaki konularda, kimlik doğrulaması (örneğin, Windows kimlik doğrulaması, X. 509.440 sertifikaları ve Kullanıcı adı ve parolalar) sağlayan Windows Communication Foundation (WCF) içinde çeşitli mekanizmalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38a59-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38a59-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="38a59-104">In This Section</span></span>  
 [<span data-ttu-id="38a59-105">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="38a59-105">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="38a59-106">ASP.NET özellikleri bir üyelik ve rol sağlayıcısı, kimlik doğrulaması için Kullanıcı adı/parola çiftlerini depolamak üzere bir veritabanı ve yetkilendirme için Kullanıcı rolleri içerir.</span><span class="sxs-lookup"><span data-stu-id="38a59-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="38a59-107">Bu konuda, WCF hizmetlerinin, kullanıcıların kimliğini doğrulamak ve yetkilendirmek için aynı veritabanını nasıl kullanabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38a59-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="38a59-108">Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="38a59-108">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="38a59-109">Özel bir Kullanıcı adı/parola doğrulayıcının nasıl tümleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="38a59-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="38a59-110">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="38a59-110">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="38a59-111">Bir istemci, ek bir güvenlik önlemi olarak hizmetin beklenen *kimliğini* belirterek hizmetin kimliğini doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="38a59-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="38a59-112">Beklenen kimlik ve hizmet tarafından döndürülen kimlik eşleşmiyorsa, kimlik doğrulaması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="38a59-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="38a59-113">Güvenlik Görüşmeleri ve Zaman Aşımları</span><span class="sxs-lookup"><span data-stu-id="38a59-113">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="38a59-114">Sınıfında özelliğinin nasıl kullanılacağını açıklar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> .</span><span class="sxs-lookup"><span data-stu-id="38a59-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="38a59-115">Windows Kimlik Doğrulama Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="38a59-115">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="38a59-116">Windows kimlik doğrulaması kullanılırken karşılaşılan yaygın sorunlara odaklanır.</span><span class="sxs-lookup"><span data-stu-id="38a59-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="38a59-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="38a59-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="38a59-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="38a59-118">Related Sections</span></span>  
 [<span data-ttu-id="38a59-119">Ortak Güvenlik Senaryoları</span><span class="sxs-lookup"><span data-stu-id="38a59-119">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="38a59-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38a59-120">See also</span></span>

- [<span data-ttu-id="38a59-121">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="38a59-121">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="38a59-122">[Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="38a59-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
