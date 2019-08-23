---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 7facf3eb54637445d1ae20297effc92605c81a61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933998"
---
# <a name="peerauthentication"></a><span data-ttu-id="b0103-101">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b0103-101">\<peerAuthentication></span></span>
<span data-ttu-id="b0103-102">Eş düğüm tarafından kullanılan bir eş sertifika için kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0103-102">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="b0103-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b0103-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b0103-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="b0103-104">\<behaviors></span></span>  
<span data-ttu-id="b0103-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b0103-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="b0103-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="b0103-106">\<behavior></span></span>  
<span data-ttu-id="b0103-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b0103-107">\<serviceCredentials></span></span>  
<span data-ttu-id="b0103-108">\<eş ></span><span class="sxs-lookup"><span data-stu-id="b0103-108">\<peer></span></span>  
<span data-ttu-id="b0103-109">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b0103-109">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0103-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0103-110">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0103-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0103-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b0103-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0103-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0103-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0103-113">Attributes</span></span>  
  
|<span data-ttu-id="b0103-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b0103-114">Attribute</span></span>|<span data-ttu-id="b0103-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0103-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="b0103-116">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b0103-116">Optional enumeration.</span></span> <span data-ttu-id="b0103-117">Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0103-117">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="b0103-118">Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="b0103-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="b0103-119">Olarak `Custom`ayarlanırsa, bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0103-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="b0103-120">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="b0103-120">Optional string.</span></span> <span data-ttu-id="b0103-121">Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0103-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="b0103-122">Bu öznitelik `certificateValidationMode` , olarak `Custom`ayarlandığında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0103-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="b0103-123">Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="b0103-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="b0103-124">Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0103-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="b0103-125">Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="b0103-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="b0103-126">Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0103-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="b0103-127">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b0103-127">Optional enumeration.</span></span> <span data-ttu-id="b0103-128">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0103-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="b0103-129">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="b0103-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="b0103-130">Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="b0103-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="b0103-131">Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0103-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="b0103-132">İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0103-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="b0103-133">İsteğe bağlı sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="b0103-133">Optional enumeration.</span></span> <span data-ttu-id="b0103-134">Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0103-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="b0103-135">Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="b0103-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0103-136">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0103-136">Child Elements</span></span>  
 <span data-ttu-id="b0103-137">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0103-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0103-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b0103-138">Parent Elements</span></span>  
  
|<span data-ttu-id="b0103-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0103-139">Element</span></span>|<span data-ttu-id="b0103-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0103-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0103-141">\<eş ></span><span class="sxs-lookup"><span data-stu-id="b0103-141">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="b0103-142">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0103-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0103-143">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0103-143">Remarks</span></span>  
 <span data-ttu-id="b0103-144">`<authentication>` Öğesi <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> sınıfına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b0103-144">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="b0103-145">Bu öğe, ağ içinde komşu-komşu kimlik doğrulaması sırasında çağrılan bir doğrulayıcısı belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0103-145">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="b0103-146">Yeni bir eş bir komşu bağlantı kurmaya çalıştığında, kendi kimlik bilgilerini yanıt veren eşe geçirir.</span><span class="sxs-lookup"><span data-stu-id="b0103-146">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="b0103-147">Yanıtlayanın Doğrulayıcısı, uzak tarafın kimlik bilgilerini doğrulamak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b0103-147">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="b0103-148">Kafeste bir eş bağlantı oluşturulduğunda her iki eş de karşılıklı olarak doğrulanır, her iki uçta da doğrulayıcılar çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b0103-148">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0103-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0103-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="b0103-150">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="b0103-150">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b0103-151">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="b0103-151">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="b0103-152">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b0103-152">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="b0103-153">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b0103-153">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="b0103-154">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b0103-154">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
