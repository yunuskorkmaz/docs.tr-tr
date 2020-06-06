---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c6183a8d27d56c7199b815ccb31b06f983a51b33
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398396"
---
# \<messageSenderAuthentication>
<span data-ttu-id="c5393-101">İleti gönderici tarafından kullanılan eş sertifika için kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5393-101">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="c5393-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5393-102">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5393-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5393-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c5393-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5393-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5393-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5393-105">Attributes</span></span>  
  
|<span data-ttu-id="c5393-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c5393-106">Attribute</span></span>|<span data-ttu-id="c5393-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5393-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="c5393-108">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c5393-108">Optional enumeration.</span></span> <span data-ttu-id="c5393-109">Kimlik bilgilerini doğrulamak için kullanılan beş moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5393-109">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="c5393-110">Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="c5393-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="c5393-111">Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c5393-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="c5393-112">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="c5393-112">Optional string.</span></span> <span data-ttu-id="c5393-113">Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5393-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c5393-114">Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .</span><span class="sxs-lookup"><span data-stu-id="c5393-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="c5393-115">Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="c5393-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c5393-116">Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5393-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="c5393-117">Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="c5393-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="c5393-118">Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5393-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="c5393-119">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c5393-119">Optional enumeration.</span></span> <span data-ttu-id="c5393-120">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5393-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="c5393-121">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="c5393-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="c5393-122">Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="c5393-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="c5393-123">Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5393-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="c5393-124">İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5393-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c5393-125">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c5393-125">Optional enumeration.</span></span> <span data-ttu-id="c5393-126">Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5393-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="c5393-127">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="c5393-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5393-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5393-128">Child Elements</span></span>  
 <span data-ttu-id="c5393-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5393-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5393-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5393-130">Parent Elements</span></span>  
  
|<span data-ttu-id="c5393-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5393-131">Element</span></span>|<span data-ttu-id="c5393-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5393-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="c5393-133">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5393-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5393-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5393-134">Remarks</span></span>  
 <span data-ttu-id="c5393-135">İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5393-135">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="c5393-136">Çıkış kanalları için, her ileti tarafından belirtilen sertifika kullanılarak imzalanır [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c5393-136">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="c5393-137">Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir `customCertificateValidatorType` .</span><span class="sxs-lookup"><span data-stu-id="c5393-137">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="c5393-138">Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="c5393-138">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5393-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5393-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="c5393-140">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c5393-140">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c5393-141">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="c5393-141">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="c5393-142">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c5393-142">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="c5393-143">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c5393-143">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="c5393-144">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c5393-144">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
