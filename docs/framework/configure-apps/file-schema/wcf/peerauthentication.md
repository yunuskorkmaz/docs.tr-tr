---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd18acaf76b2d5ccceb12b62398357b0b1655cb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="f6766-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="f6766-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="f6766-103">Eş düğüm tarafından kullanılan bir eş sertifika kimlik doğrulaması ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6766-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="f6766-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f6766-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6766-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="f6766-105">\<behaviors></span></span>  
<span data-ttu-id="f6766-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f6766-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f6766-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f6766-107">\<behavior></span></span>  
<span data-ttu-id="f6766-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f6766-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f6766-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="f6766-109">\<peer></span></span>  
<span data-ttu-id="f6766-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f6766-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6766-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6766-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6766-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6766-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f6766-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6766-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6766-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6766-114">Attributes</span></span>  
  
|<span data-ttu-id="f6766-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6766-115">Attribute</span></span>|<span data-ttu-id="f6766-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6766-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="f6766-117">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="f6766-117">Optional enumeration.</span></span> <span data-ttu-id="f6766-118">Kimlik bilgilerini doğrulamak için kullanılan üç modlarından birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6766-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f6766-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="f6766-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="f6766-120">Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6766-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="f6766-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="f6766-121">Optional string.</span></span> <span data-ttu-id="f6766-122">Bir türü ve bir özel tür doğrulamak için kullanılan derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6766-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f6766-123">Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f6766-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="f6766-124">Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="f6766-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="f6766-125">Varsayılan eş eş sertifikayı güvenilir kişiler deposunda karşı doğrular sertifika Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6766-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="f6766-126">Sertifika geçerli bir kök zincir olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="f6766-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="f6766-127">Farklı bir davranışı belirtmek ve bu öznitelik için özel Doğrulayıcı işaret edecek şekilde kullanmak için özel bir doğrulayıcı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6766-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="f6766-128">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="f6766-128">Optional enumeration.</span></span> <span data-ttu-id="f6766-129">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6766-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="f6766-130">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="f6766-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="f6766-131">Sistem eş sertifika tarafından iptal edildi olduğunu doğrular iptal edilen sertifika listesinde bakan.</span><span class="sxs-lookup"><span data-stu-id="f6766-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="f6766-132">Bu onay çevrimiçi denetleyerek ya da bir önbelleğe alınan iptal listesi karşı gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f6766-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="f6766-133">İptal denetimi NoCheck için bu öznitelik ayarlayarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="f6766-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f6766-134">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="f6766-134">Optional enumeration.</span></span> <span data-ttu-id="f6766-135">Burada eş sertifika doğrulanmış tarafından güvenilen depolama konumu belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] güvenlik sistemi.</span><span class="sxs-lookup"><span data-stu-id="f6766-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="f6766-136">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="f6766-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6766-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6766-137">Child Elements</span></span>  
 <span data-ttu-id="f6766-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="f6766-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6766-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6766-139">Parent Elements</span></span>  
  
|<span data-ttu-id="f6766-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6766-140">Element</span></span>|<span data-ttu-id="f6766-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6766-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6766-142">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="f6766-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="f6766-143">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6766-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6766-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6766-144">Remarks</span></span>  
 <span data-ttu-id="f6766-145">`<authentication>` Öğesi karşılık gelen <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f6766-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="f6766-146">Bu öğe kafes komşu komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6766-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="f6766-147">Yeni bir eş komşu bağlantısı kurmaya çalıştığında, yanıt vermeyen eşler arası kendi kimlik bilgisi geçirir.</span><span class="sxs-lookup"><span data-stu-id="f6766-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="f6766-148">Yanıtlayıcı Doğrulayıcı uzak taraf kimlik doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f6766-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="f6766-149">Mesh bir eş bağlantı olduğunda, hem eş karşılıklı kimlik doğrulaması, iki ucunda anlamı doğrulayıcıları çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f6766-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6766-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6766-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="f6766-151">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="f6766-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="f6766-152">Eşler arası ağ</span><span class="sxs-lookup"><span data-stu-id="f6766-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="f6766-153">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f6766-153">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="f6766-154">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="f6766-154">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="f6766-155">Eş kanalı uygulamalarını güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="f6766-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
