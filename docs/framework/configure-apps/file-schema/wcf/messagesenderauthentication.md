---
description: 'Hakkında daha fazla bilgi edinin: <messageSenderAuthentication>'
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: e98388eafce24b0f19647364b6bbec94ee6ba135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749330"
---
# \<messageSenderAuthentication>

<span data-ttu-id="0a5f9-102">İleti gönderici tarafından kullanılan eş sertifika için kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-102">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="0a5f9-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a5f9-103">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a5f9-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a5f9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0a5f9-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a5f9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0a5f9-106">Attributes</span></span>  
  
|<span data-ttu-id="0a5f9-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0a5f9-107">Attribute</span></span>|<span data-ttu-id="0a5f9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a5f9-108">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="0a5f9-109">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-109">Optional enumeration.</span></span> <span data-ttu-id="0a5f9-110">Kimlik bilgilerini doğrulamak için kullanılan beş moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-110">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="0a5f9-111">Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="0a5f9-111">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="0a5f9-112">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-112">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="0a5f9-113">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-113">Optional string.</span></span> <span data-ttu-id="0a5f9-114">Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-114">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="0a5f9-115">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="0a5f9-115">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="0a5f9-116">Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="0a5f9-116">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="0a5f9-117">Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-117">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="0a5f9-118">Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-118">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="0a5f9-119">Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-119">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="0a5f9-120">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-120">Optional enumeration.</span></span> <span data-ttu-id="0a5f9-121">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-121">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="0a5f9-122">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="0a5f9-122">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="0a5f9-123">Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-123">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="0a5f9-124">Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-124">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="0a5f9-125">İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-125">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="0a5f9-126">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-126">Optional enumeration.</span></span> <span data-ttu-id="0a5f9-127">Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-127">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="0a5f9-128">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="0a5f9-128">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a5f9-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a5f9-129">Child Elements</span></span>  

 <span data-ttu-id="0a5f9-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a5f9-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0a5f9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0a5f9-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="0a5f9-132">Element</span></span>|<span data-ttu-id="0a5f9-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a5f9-133">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="0a5f9-134">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-134">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a5f9-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a5f9-135">Remarks</span></span>  

 <span data-ttu-id="0a5f9-136">İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-136">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="0a5f9-137">Çıkış kanalları için, her ileti tarafından belirtilen sertifika kullanılarak imzalanır [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0a5f9-137">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="0a5f9-138">Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir `customCertificateValidatorType` .</span><span class="sxs-lookup"><span data-stu-id="0a5f9-138">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="0a5f9-139">Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-139">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a5f9-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a5f9-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="0a5f9-141">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="0a5f9-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="0a5f9-142">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="0a5f9-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="0a5f9-143">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0a5f9-143">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="0a5f9-144">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0a5f9-144">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="0a5f9-145">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0a5f9-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
