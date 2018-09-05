---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 8a3beb42d1064e6c6629014369628248b4cd5c8d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553803"
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="0bb30-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="0bb30-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="0bb30-103">İletiyi gönderen tarafından kullanılan eş sertifika kimlik doğrulaması ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="0bb30-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0bb30-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0bb30-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="0bb30-105">\<behaviors></span></span>  
<span data-ttu-id="0bb30-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0bb30-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0bb30-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="0bb30-107">\<behavior></span></span>  
<span data-ttu-id="0bb30-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="0bb30-108">\<serviceCredentials></span></span>  
<span data-ttu-id="0bb30-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="0bb30-109">\<peer></span></span>  
<span data-ttu-id="0bb30-110">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="0bb30-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb30-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bb30-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bb30-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bb30-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0bb30-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bb30-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bb30-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0bb30-114">Attributes</span></span>  
  
|<span data-ttu-id="0bb30-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0bb30-115">Attribute</span></span>|<span data-ttu-id="0bb30-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bb30-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="0bb30-117">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0bb30-117">Optional enumeration.</span></span> <span data-ttu-id="0bb30-118">Kimlik bilgilerini doğrulamak için kullanılan beş moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="0bb30-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="0bb30-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="0bb30-120">Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb30-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="0bb30-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="0bb30-121">Optional string.</span></span> <span data-ttu-id="0bb30-122">Bir tür ve özel bir tür doğrulamak için kullanılan bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="0bb30-123">Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="0bb30-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="0bb30-124">Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="0bb30-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="0bb30-125">Windows Communication Foundation (WCF) varsayılan eş eş sertifikayı güvenilir Kişiler deposuna karşı doğrular sertifika Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bb30-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="0bb30-126">Ayrıca, sertifika bir geçerli köke olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="0bb30-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="0bb30-127">Farklı bir davranış belirtin ve bu öznitelik için özel Doğrulayıcı noktası özel Doğrulayıcı sağlayıcısı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bb30-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="0bb30-128">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0bb30-128">Optional enumeration.</span></span> <span data-ttu-id="0bb30-129">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="0bb30-130">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="0bb30-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="0bb30-131">Eş sertifika tarafından iptal edildi, sistem doğrular iptal edilen sertifika listesine aranıyor.</span><span class="sxs-lookup"><span data-stu-id="0bb30-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="0bb30-132">Bu onay, çevrimiçi işaretleyerek ya da bir önbelleğe alınan iptal listesine karşı gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="0bb30-133">İptal denetimi bu öznitelik için NoCheck ayarlayarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="0bb30-134">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0bb30-134">Optional enumeration.</span></span> <span data-ttu-id="0bb30-135">WCF güvenlik sistemi tarafından eş sertifika nerede doğrulanır güvenilir depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="0bb30-136">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="0bb30-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bb30-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bb30-137">Child Elements</span></span>  
 <span data-ttu-id="0bb30-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bb30-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bb30-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bb30-139">Parent Elements</span></span>  
  
|<span data-ttu-id="0bb30-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="0bb30-140">Element</span></span>|<span data-ttu-id="0bb30-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bb30-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bb30-142">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="0bb30-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="0bb30-143">Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0bb30-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bb30-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bb30-144">Remarks</span></span>  
 <span data-ttu-id="0bb30-145">İleti kimlik doğrulaması seçilirse, bu öğe yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb30-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="0bb30-146">Çıkış kanallar için her ileti tarafından sağlanan sertifikayı kullanarak imzalanmış [ \<sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="0bb30-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="0bb30-147">Tüm iletileri tarafından belirtilen Doğrulayıcı kullanarak ileti kimlik bilgileri karşı uygulamaya teslim önce iade `customCertificateValidatorType` bu öğenin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0bb30-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="0bb30-148">Doğrulayıcı kabul edin veya kimlik bilgilerini reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bb30-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb30-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bb30-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="0bb30-150">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="0bb30-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="0bb30-151">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="0bb30-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="0bb30-152">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="0bb30-152">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="0bb30-153">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="0bb30-153">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="0bb30-154">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="0bb30-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
