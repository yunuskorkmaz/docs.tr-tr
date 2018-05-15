---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: a8cc52fb2179bb5fc38635e4de0063a1dc1b1833
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="a00fa-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="a00fa-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="a00fa-103">Eş düğüm tarafından kullanılan bir eş sertifika kimlik doğrulaması ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="a00fa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a00fa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a00fa-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="a00fa-105">\<behaviors></span></span>  
<span data-ttu-id="a00fa-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a00fa-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a00fa-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a00fa-107">\<behavior></span></span>  
<span data-ttu-id="a00fa-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a00fa-108">\<serviceCredentials></span></span>  
<span data-ttu-id="a00fa-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="a00fa-109">\<peer></span></span>  
<span data-ttu-id="a00fa-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="a00fa-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00fa-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a00fa-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a00fa-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a00fa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a00fa-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a00fa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a00fa-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a00fa-114">Attributes</span></span>  
  
|<span data-ttu-id="a00fa-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a00fa-115">Attribute</span></span>|<span data-ttu-id="a00fa-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a00fa-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="a00fa-117">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="a00fa-117">Optional enumeration.</span></span> <span data-ttu-id="a00fa-118">Kimlik bilgilerini doğrulamak için kullanılan üç modlarından birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a00fa-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="a00fa-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="a00fa-120">Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a00fa-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="a00fa-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="a00fa-121">Optional string.</span></span> <span data-ttu-id="a00fa-122">Bir türü ve bir özel tür doğrulamak için kullanılan derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a00fa-123">Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a00fa-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="a00fa-124">Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="a00fa-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="a00fa-125">Windows Communication Foundation (WCF) varsayılan eş eş sertifikayı güvenilir kişiler deposunda karşı doğrular sertifika Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a00fa-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="a00fa-126">Sertifika geçerli bir kök zincir olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="a00fa-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="a00fa-127">Farklı bir davranışı belirtmek ve bu öznitelik için özel Doğrulayıcı işaret edecek şekilde kullanmak için özel bir doğrulayıcı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a00fa-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="a00fa-128">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="a00fa-128">Optional enumeration.</span></span> <span data-ttu-id="a00fa-129">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="a00fa-130">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="a00fa-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="a00fa-131">Sistem eş sertifika tarafından iptal edildi olduğunu doğrular iptal edilen sertifika listesinde bakan.</span><span class="sxs-lookup"><span data-stu-id="a00fa-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="a00fa-132">Bu onay çevrimiçi denetleyerek ya da bir önbelleğe alınan iptal listesi karşı gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="a00fa-133">İptal denetimi NoCheck için bu öznitelik ayarlayarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="a00fa-134">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="a00fa-134">Optional enumeration.</span></span> <span data-ttu-id="a00fa-135">Burada eş sertifika doğrulanmış tarafından güvenilen depolama konumu belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] güvenlik sistemi.</span><span class="sxs-lookup"><span data-stu-id="a00fa-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="a00fa-136">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="a00fa-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a00fa-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a00fa-137">Child Elements</span></span>  
 <span data-ttu-id="a00fa-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="a00fa-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a00fa-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a00fa-139">Parent Elements</span></span>  
  
|<span data-ttu-id="a00fa-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="a00fa-140">Element</span></span>|<span data-ttu-id="a00fa-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a00fa-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a00fa-142">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="a00fa-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="a00fa-143">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a00fa-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a00fa-144">Remarks</span></span>  
 <span data-ttu-id="a00fa-145">`<authentication>` Öğesi karşılık gelen <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a00fa-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="a00fa-146">Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="a00fa-147">Yeni bir eş komşu bağlantısı kurmaya çalıştığında, yanıt vermeyen eşler arası kendi kimlik bilgisi geçirir.</span><span class="sxs-lookup"><span data-stu-id="a00fa-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="a00fa-148">Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a00fa-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="a00fa-149">Mesh bir eş bağlantı olduğunda, hem eş karşılıklı kimlik doğrulaması, iki ucunda anlamı doğrulayıcıları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a00fa-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00fa-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a00fa-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="a00fa-151">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="a00fa-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="a00fa-152">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="a00fa-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="a00fa-153">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a00fa-153">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="a00fa-154">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="a00fa-154">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="a00fa-155">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a00fa-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
