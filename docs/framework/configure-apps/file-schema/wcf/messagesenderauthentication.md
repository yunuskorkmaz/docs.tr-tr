---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c1d3662b2ceda83eb32abe99244e926332214698
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931317"
---
# <a name="messagesenderauthentication"></a><span data-ttu-id="a4ba7-101">\<Iletienderauthentication ></span><span class="sxs-lookup"><span data-stu-id="a4ba7-101">\<messageSenderAuthentication></span></span>
<span data-ttu-id="a4ba7-102">İleti gönderici tarafından kullanılan eş sertifika için kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-102">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="a4ba7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a4ba7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4ba7-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a4ba7-104">\<behaviors></span></span>  
<span data-ttu-id="a4ba7-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a4ba7-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a4ba7-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="a4ba7-106">\<behavior></span></span>  
<span data-ttu-id="a4ba7-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a4ba7-107">\<serviceCredentials></span></span>  
<span data-ttu-id="a4ba7-108">\<eş ></span><span class="sxs-lookup"><span data-stu-id="a4ba7-108">\<peer></span></span>  
<span data-ttu-id="a4ba7-109">\<Iletienderauthentication ></span><span class="sxs-lookup"><span data-stu-id="a4ba7-109">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ba7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4ba7-110">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4ba7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4ba7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a4ba7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4ba7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a4ba7-113">Attributes</span></span>  
  
|<span data-ttu-id="a4ba7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a4ba7-114">Attribute</span></span>|<span data-ttu-id="a4ba7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4ba7-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="a4ba7-116">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-116">Optional enumeration.</span></span> <span data-ttu-id="a4ba7-117">Kimlik bilgilerini doğrulamak için kullanılan beş moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-117">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="a4ba7-118">Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="a4ba7-119">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="a4ba7-120">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-120">Optional string.</span></span> <span data-ttu-id="a4ba7-121">Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a4ba7-122">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="a4ba7-123">Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="a4ba7-124">Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="a4ba7-125">Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="a4ba7-126">Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="a4ba7-127">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-127">Optional enumeration.</span></span> <span data-ttu-id="a4ba7-128">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="a4ba7-129">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="a4ba7-130">Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="a4ba7-131">Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="a4ba7-132">İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="a4ba7-133">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-133">Optional enumeration.</span></span> <span data-ttu-id="a4ba7-134">Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="a4ba7-135">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4ba7-136">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4ba7-136">Child Elements</span></span>  
 <span data-ttu-id="a4ba7-137">Yok.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4ba7-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a4ba7-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a4ba7-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="a4ba7-139">Element</span></span>|<span data-ttu-id="a4ba7-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4ba7-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4ba7-141">\<eş ></span><span class="sxs-lookup"><span data-stu-id="a4ba7-141">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="a4ba7-142">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4ba7-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4ba7-143">Remarks</span></span>  
 <span data-ttu-id="a4ba7-144">İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-144">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="a4ba7-145">Çıkış kanalları için her ileti, [ \<sertifika >](certificate-element.md)tarafından belirtilen sertifika kullanılarak imzalanır.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-145">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="a4ba7-146">Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin `customCertificateValidatorType` özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-146">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="a4ba7-147">Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-147">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ba7-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4ba7-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="a4ba7-149">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="a4ba7-149">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a4ba7-150">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="a4ba7-150">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="a4ba7-151">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a4ba7-151">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="a4ba7-152">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a4ba7-152">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="a4ba7-153">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a4ba7-153">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
