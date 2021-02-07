---
description: 'Hakkında daha fazla bilgi edinin: <peerAuthentication>'
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: b640b4aac296c40fadcc5f4070ba58e5f92fd265
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683664"
---
# \<peerAuthentication>

<span data-ttu-id="55c28-102">Eş düğüm tarafından kullanılan bir eş sertifika için kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c28-102">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="55c28-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="55c28-103">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55c28-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c28-104">Attributes and Elements</span></span>  

 <span data-ttu-id="55c28-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55c28-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55c28-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55c28-106">Attributes</span></span>  
  
|<span data-ttu-id="55c28-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55c28-107">Attribute</span></span>|<span data-ttu-id="55c28-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c28-108">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="55c28-109">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="55c28-109">Optional enumeration.</span></span> <span data-ttu-id="55c28-110">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c28-110">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="55c28-111">Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="55c28-111">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="55c28-112">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="55c28-112">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="55c28-113">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="55c28-113">Optional string.</span></span> <span data-ttu-id="55c28-114">Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c28-114">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="55c28-115">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="55c28-115">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="55c28-116">Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="55c28-116">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="55c28-117">Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="55c28-117">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="55c28-118">Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="55c28-118">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="55c28-119">Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55c28-119">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="55c28-120">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="55c28-120">Optional enumeration.</span></span> <span data-ttu-id="55c28-121">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c28-121">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="55c28-122">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="55c28-122">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="55c28-123">Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="55c28-123">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="55c28-124">Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="55c28-124">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="55c28-125">İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="55c28-125">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="55c28-126">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="55c28-126">Optional enumeration.</span></span> <span data-ttu-id="55c28-127">Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c28-127">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="55c28-128">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="55c28-128">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55c28-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c28-129">Child Elements</span></span>  

 <span data-ttu-id="55c28-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="55c28-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55c28-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c28-131">Parent Elements</span></span>  
  
|<span data-ttu-id="55c28-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="55c28-132">Element</span></span>|<span data-ttu-id="55c28-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c28-133">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="55c28-134">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c28-134">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55c28-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55c28-135">Remarks</span></span>  

 <span data-ttu-id="55c28-136">`<authentication>`Öğesi sınıfına karşılık gelir <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> .</span><span class="sxs-lookup"><span data-stu-id="55c28-136">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="55c28-137">Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="55c28-137">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="55c28-138">Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="55c28-138">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="55c28-139">Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="55c28-139">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="55c28-140">Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="55c28-140">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c28-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55c28-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="55c28-142">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="55c28-142">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="55c28-143">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="55c28-143">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="55c28-144">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="55c28-144">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="55c28-145">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="55c28-145">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="55c28-146">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="55c28-146">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
