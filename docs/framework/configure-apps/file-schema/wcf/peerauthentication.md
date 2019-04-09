---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: b627105dc4aae49557b0a6684569719622e13f08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180602"
---
# <a name="peerauthentication"></a><span data-ttu-id="c4f99-101">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c4f99-101">\<peerAuthentication></span></span>
<span data-ttu-id="c4f99-102">Bir eş düğüm tarafından kullanılan bir eş sertifika kimlik doğrulaması ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-102">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="c4f99-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c4f99-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c4f99-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c4f99-104">\<behaviors></span></span>  
<span data-ttu-id="c4f99-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c4f99-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c4f99-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c4f99-106">\<behavior></span></span>  
<span data-ttu-id="c4f99-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c4f99-107">\<serviceCredentials></span></span>  
<span data-ttu-id="c4f99-108">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="c4f99-108">\<peer></span></span>  
<span data-ttu-id="c4f99-109">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c4f99-109">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f99-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4f99-110">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4f99-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4f99-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c4f99-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4f99-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4f99-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4f99-113">Attributes</span></span>  
  
|<span data-ttu-id="c4f99-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c4f99-114">Attribute</span></span>|<span data-ttu-id="c4f99-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4f99-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="c4f99-116">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c4f99-116">Optional enumeration.</span></span> <span data-ttu-id="c4f99-117">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-117">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="c4f99-118">Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="c4f99-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="c4f99-119">Varsa kümesine `Custom`, ardından bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4f99-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="c4f99-120">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="c4f99-120">Optional string.</span></span> <span data-ttu-id="c4f99-121">Bir tür ve özel bir tür doğrulamak için kullanılan bir derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c4f99-122">Bu öznitelik olduğunda ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="c4f99-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="c4f99-123">Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c4f99-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c4f99-124">Windows Communication Foundation (WCF) varsayılan eş eş sertifikayı güvenilir Kişiler deposuna karşı doğrular sertifika Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4f99-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="c4f99-125">Ayrıca, sertifika bir geçerli köke olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="c4f99-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="c4f99-126">Farklı bir davranış belirtin ve bu öznitelik için özel Doğrulayıcı noktası özel Doğrulayıcı sağlayıcısı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4f99-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="c4f99-127">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c4f99-127">Optional enumeration.</span></span> <span data-ttu-id="c4f99-128">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="c4f99-129">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="c4f99-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="c4f99-130">Eş sertifika tarafından iptal edildi, sistem doğrular iptal edilen sertifika listesine aranıyor.</span><span class="sxs-lookup"><span data-stu-id="c4f99-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="c4f99-131">Bu onay, çevrimiçi işaretleyerek ya da bir önbelleğe alınan iptal listesine karşı gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="c4f99-132">İptal denetimi bu öznitelik için NoCheck ayarlayarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c4f99-133">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="c4f99-133">Optional enumeration.</span></span> <span data-ttu-id="c4f99-134">WCF güvenlik sistemi tarafından eş sertifika nerede doğrulanır güvenilir depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="c4f99-135">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="c4f99-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4f99-136">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4f99-136">Child Elements</span></span>  
 <span data-ttu-id="c4f99-137">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4f99-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4f99-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4f99-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c4f99-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4f99-139">Element</span></span>|<span data-ttu-id="c4f99-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4f99-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4f99-141">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="c4f99-141">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="c4f99-142">Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4f99-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4f99-143">Remarks</span></span>  
 <span data-ttu-id="c4f99-144">`<authentication>` Karşılık gelen öğe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c4f99-144">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="c4f99-145">Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-145">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="c4f99-146">Yeni bir eş komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgisi eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="c4f99-146">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="c4f99-147">Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c4f99-147">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="c4f99-148">Ağ içinde bir eş bağlantı kurulsa hem eşleri karşılıklı kimlik doğrulaması, her iki ucunda anlamı doğrulayıcıları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c4f99-148">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f99-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4f99-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="c4f99-150">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="c4f99-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c4f99-151">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="c4f99-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="c4f99-152">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c4f99-152">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="c4f99-153">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="c4f99-153">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="c4f99-154">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c4f99-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
