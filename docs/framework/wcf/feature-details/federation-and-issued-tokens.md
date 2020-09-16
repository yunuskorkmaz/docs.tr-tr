---
title: Federasyon ve Verilen Belirteçler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: dffba51c1bf1aaffbed8725aafc96fd747cb31c6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559258"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="263e8-102">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="263e8-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="263e8-103">Windows Communication Foundation (WCF) ile, WS-Federation ve WS-Trust belirtimlerini uygulayan hizmetlerle güvenli bir şekilde iletişim kuran istemciler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="263e8-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="263e8-104">Belirtimler, farklı güven bölgelerinde kimlik doğrulaması ve yetkilendirmeyi etkinleştiren mekanizmalar sağlamak üzere XML, SOAP ve Web Hizmetleri Açıklama Dili (WSDL) kullanır.</span><span class="sxs-lookup"><span data-stu-id="263e8-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="263e8-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="263e8-105">In This Section</span></span>  
 [<span data-ttu-id="263e8-106">Federasyon</span><span class="sxs-lookup"><span data-stu-id="263e8-106">Federation</span></span>](federation.md)  
 <span data-ttu-id="263e8-107">Federasyona genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="263e8-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="263e8-108">Federasyon ve Güven</span><span class="sxs-lookup"><span data-stu-id="263e8-108">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="263e8-109">Federasyon Hizmetleri veya istemcileri oluştururken dikkat edilecek tasarım sorunlarını listeler.</span><span class="sxs-lookup"><span data-stu-id="263e8-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="263e8-110">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="263e8-110">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="263e8-111">WCF ile federe istemci oluşturma hakkında temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="263e8-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="263e8-112">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="263e8-112">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="263e8-113">Federasyon hizmeti oluşturma adımlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="263e8-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="263e8-114">Nasıl yapılır: WSFederationHttpBinding Oluşturma</span><span class="sxs-lookup"><span data-stu-id="263e8-114">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="263e8-115">Kullanan istemcilerin ve hizmetlerin nasıl yapılandırılacağını açıklar `WSFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="263e8-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="263e8-116">Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="263e8-116">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="263e8-117">Güvenlik belirteci hizmeti oluşturma adımlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="263e8-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="263e8-118">Güvenlik Onaylama İşlemi İşaretleme Dili (SAML) Belirteçleri ve Talepleri</span><span class="sxs-lookup"><span data-stu-id="263e8-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="263e8-119">Genişletilebilir olan ve zengin talep türleri oluşturmanızı sağlayan güvenlik onayları biçimlendirme dili (SAML) belirteçlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="263e8-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="263e8-120">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="263e8-120">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="263e8-121">Güvenlik belirteçlerinin yerel olarak vereni oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="263e8-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="263e8-122">Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="263e8-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="263e8-123">Bir üzerinde güvenli oturumların nasıl devre dışı bırakılacağını açıklar `WSFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="263e8-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="263e8-124">Her istemci için bir oturum gerektiren bir Web grubu oluşturulurken güvenli oturumların devre dışı bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="263e8-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="263e8-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="263e8-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="263e8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="263e8-126">See also</span></span>

- [<span data-ttu-id="263e8-127">Yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="263e8-127">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="263e8-128">Özel Belirteçler</span><span class="sxs-lookup"><span data-stu-id="263e8-128">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="263e8-129">[Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="263e8-129">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
