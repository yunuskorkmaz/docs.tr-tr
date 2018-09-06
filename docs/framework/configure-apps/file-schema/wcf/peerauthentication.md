---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: bb83d2badad609394a66246fc14c19a6602399e0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799193"
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="1880f-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="1880f-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="1880f-103">Bir eş düğüm tarafından kullanılan bir eş sertifika kimlik doğrulaması ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1880f-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="1880f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1880f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1880f-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1880f-105">\<behaviors></span></span>  
<span data-ttu-id="1880f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1880f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1880f-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1880f-107">\<behavior></span></span>  
<span data-ttu-id="1880f-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1880f-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1880f-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="1880f-109">\<peer></span></span>  
<span data-ttu-id="1880f-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="1880f-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1880f-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1880f-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1880f-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1880f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1880f-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1880f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1880f-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1880f-114">Attributes</span></span>  
  
|<span data-ttu-id="1880f-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1880f-115">Attribute</span></span>|<span data-ttu-id="1880f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1880f-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="1880f-117">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1880f-117">Optional enumeration.</span></span> <span data-ttu-id="1880f-118">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1880f-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="1880f-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="1880f-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="1880f-120">Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1880f-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="1880f-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="1880f-121">Optional string.</span></span> <span data-ttu-id="1880f-122">Bir tür ve özel bir tür doğrulamak için kullanılan bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="1880f-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="1880f-123">Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="1880f-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="1880f-124">Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="1880f-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="1880f-125">Windows Communication Foundation (WCF) varsayılan eş eş sertifikayı güvenilir Kişiler deposuna karşı doğrular sertifika Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1880f-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="1880f-126">Ayrıca, sertifika bir geçerli köke olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="1880f-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="1880f-127">Farklı bir davranış belirtin ve bu öznitelik için özel Doğrulayıcı noktası özel Doğrulayıcı sağlayıcısı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1880f-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="1880f-128">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1880f-128">Optional enumeration.</span></span> <span data-ttu-id="1880f-129">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1880f-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="1880f-130">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="1880f-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="1880f-131">Eş sertifika tarafından iptal edildi, sistem doğrular iptal edilen sertifika listesine aranıyor.</span><span class="sxs-lookup"><span data-stu-id="1880f-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="1880f-132">Bu onay, çevrimiçi işaretleyerek ya da bir önbelleğe alınan iptal listesine karşı gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1880f-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="1880f-133">İptal denetimi bu öznitelik için NoCheck ayarlayarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="1880f-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="1880f-134">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1880f-134">Optional enumeration.</span></span> <span data-ttu-id="1880f-135">WCF güvenlik sistemi tarafından eş sertifika nerede doğrulanır güvenilir depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1880f-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="1880f-136">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="1880f-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1880f-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1880f-137">Child Elements</span></span>  
 <span data-ttu-id="1880f-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="1880f-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1880f-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1880f-139">Parent Elements</span></span>  
  
|<span data-ttu-id="1880f-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="1880f-140">Element</span></span>|<span data-ttu-id="1880f-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1880f-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1880f-142">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="1880f-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="1880f-143">Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1880f-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1880f-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1880f-144">Remarks</span></span>  
 <span data-ttu-id="1880f-145">`<authentication>` Karşılık gelen öğe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1880f-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="1880f-146">Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="1880f-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="1880f-147">Yeni bir eş komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgisi eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="1880f-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="1880f-148">Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1880f-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="1880f-149">Ağ içinde bir eş bağlantı kurulsa hem eşleri karşılıklı kimlik doğrulaması, her iki ucunda anlamı doğrulayıcıları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1880f-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1880f-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1880f-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="1880f-151">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="1880f-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="1880f-152">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="1880f-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="1880f-153">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="1880f-153">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="1880f-154">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="1880f-154">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="1880f-155">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1880f-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
