---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: bb83d2badad609394a66246fc14c19a6602399e0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569144"
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="6c156-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="6c156-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="6c156-103">Bir eş düğüm tarafından kullanılan bir eş sertifika kimlik doğrulaması ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c156-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="6c156-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6c156-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c156-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6c156-105">\<behaviors></span></span>  
<span data-ttu-id="6c156-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6c156-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6c156-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="6c156-107">\<behavior></span></span>  
<span data-ttu-id="6c156-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6c156-108">\<serviceCredentials></span></span>  
<span data-ttu-id="6c156-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="6c156-109">\<peer></span></span>  
<span data-ttu-id="6c156-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="6c156-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c156-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c156-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c156-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c156-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6c156-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c156-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c156-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c156-114">Attributes</span></span>  
  
|<span data-ttu-id="6c156-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c156-115">Attribute</span></span>|<span data-ttu-id="6c156-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c156-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="6c156-117">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="6c156-117">Optional enumeration.</span></span> <span data-ttu-id="6c156-118">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c156-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="6c156-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="6c156-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="6c156-120">Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c156-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="6c156-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="6c156-121">Optional string.</span></span> <span data-ttu-id="6c156-122">Bir tür ve özel bir tür doğrulamak için kullanılan bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c156-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="6c156-123">Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="6c156-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="6c156-124">Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="6c156-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="6c156-125">Windows Communication Foundation (WCF) varsayılan eş eş sertifikayı güvenilir Kişiler deposuna karşı doğrular sertifika Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c156-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="6c156-126">Ayrıca, sertifika bir geçerli köke olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="6c156-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="6c156-127">Farklı bir davranış belirtin ve bu öznitelik için özel Doğrulayıcı noktası özel Doğrulayıcı sağlayıcısı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c156-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="6c156-128">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="6c156-128">Optional enumeration.</span></span> <span data-ttu-id="6c156-129">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c156-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="6c156-130">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="6c156-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="6c156-131">Eş sertifika tarafından iptal edildi, sistem doğrular iptal edilen sertifika listesine aranıyor.</span><span class="sxs-lookup"><span data-stu-id="6c156-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="6c156-132">Bu onay, çevrimiçi işaretleyerek ya da bir önbelleğe alınan iptal listesine karşı gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6c156-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="6c156-133">İptal denetimi bu öznitelik için NoCheck ayarlayarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c156-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="6c156-134">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="6c156-134">Optional enumeration.</span></span> <span data-ttu-id="6c156-135">WCF güvenlik sistemi tarafından eş sertifika nerede doğrulanır güvenilir depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c156-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="6c156-136">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="6c156-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c156-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c156-137">Child Elements</span></span>  
 <span data-ttu-id="6c156-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="6c156-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c156-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c156-139">Parent Elements</span></span>  
  
|<span data-ttu-id="6c156-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c156-140">Element</span></span>|<span data-ttu-id="6c156-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c156-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c156-142">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="6c156-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="6c156-143">Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c156-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c156-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c156-144">Remarks</span></span>  
 <span data-ttu-id="6c156-145">`<authentication>` Karşılık gelen öğe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c156-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="6c156-146">Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c156-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="6c156-147">Yeni bir eş komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgisi eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="6c156-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="6c156-148">Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6c156-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="6c156-149">Ağ içinde bir eş bağlantı kurulsa hem eşleri karşılıklı kimlik doğrulaması, her iki ucunda anlamı doğrulayıcıları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6c156-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c156-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c156-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="6c156-151">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="6c156-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="6c156-152">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="6c156-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="6c156-153">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="6c156-153">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="6c156-154">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="6c156-154">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="6c156-155">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6c156-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
