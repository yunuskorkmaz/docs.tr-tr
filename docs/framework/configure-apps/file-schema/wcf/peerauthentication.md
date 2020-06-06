---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 118159617a7f4c27ecc5e8fe077c28cfefac8537
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397614"
---
# \<peerAuthentication>
<span data-ttu-id="59f41-101">Eş düğüm tarafından kullanılan bir eş sertifika için kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="59f41-101">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="59f41-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59f41-102">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59f41-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="59f41-103">Attributes and Elements</span></span>  
 <span data-ttu-id="59f41-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="59f41-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59f41-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="59f41-105">Attributes</span></span>  
  
|<span data-ttu-id="59f41-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="59f41-106">Attribute</span></span>|<span data-ttu-id="59f41-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59f41-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="59f41-108">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="59f41-108">Optional enumeration.</span></span> <span data-ttu-id="59f41-109">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59f41-109">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="59f41-110">Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="59f41-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="59f41-111">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59f41-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="59f41-112">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="59f41-112">Optional string.</span></span> <span data-ttu-id="59f41-113">Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="59f41-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="59f41-114">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="59f41-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="59f41-115">Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="59f41-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="59f41-116">Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="59f41-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="59f41-117">Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="59f41-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="59f41-118">Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59f41-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="59f41-119">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="59f41-119">Optional enumeration.</span></span> <span data-ttu-id="59f41-120">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="59f41-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="59f41-121">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="59f41-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="59f41-122">Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="59f41-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="59f41-123">Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="59f41-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="59f41-124">İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="59f41-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="59f41-125">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="59f41-125">Optional enumeration.</span></span> <span data-ttu-id="59f41-126">Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="59f41-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="59f41-127">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="59f41-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59f41-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="59f41-128">Child Elements</span></span>  
 <span data-ttu-id="59f41-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="59f41-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59f41-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="59f41-130">Parent Elements</span></span>  
  
|<span data-ttu-id="59f41-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="59f41-131">Element</span></span>|<span data-ttu-id="59f41-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59f41-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="59f41-133">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="59f41-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59f41-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59f41-134">Remarks</span></span>  
 <span data-ttu-id="59f41-135">`<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> .</span><span class="sxs-lookup"><span data-stu-id="59f41-135">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="59f41-136">Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="59f41-136">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="59f41-137">Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="59f41-137">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="59f41-138">Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="59f41-138">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="59f41-139">Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="59f41-139">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f41-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59f41-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="59f41-141">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="59f41-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="59f41-142">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="59f41-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="59f41-143">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="59f41-143">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="59f41-144">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="59f41-144">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="59f41-145">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="59f41-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
