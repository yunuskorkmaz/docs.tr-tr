---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 734deddc2924814b081ce80b8504fb77e78c095c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="de4ff-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="de4ff-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="de4ff-103">Eş sertifikanın bir ileti gönderen tarafından kullanılan kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="de4ff-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de4ff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de4ff-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="de4ff-105">\<behaviors></span></span>  
<span data-ttu-id="de4ff-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="de4ff-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="de4ff-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="de4ff-107">\<behavior></span></span>  
<span data-ttu-id="de4ff-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="de4ff-108">\<serviceCredentials></span></span>  
<span data-ttu-id="de4ff-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="de4ff-109">\<peer></span></span>  
<span data-ttu-id="de4ff-110">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="de4ff-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4ff-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de4ff-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de4ff-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="de4ff-112">Attributes and Elements</span></span>  
 <span data-ttu-id="de4ff-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de4ff-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de4ff-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="de4ff-114">Attributes</span></span>  
  
|<span data-ttu-id="de4ff-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="de4ff-115">Attribute</span></span>|<span data-ttu-id="de4ff-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de4ff-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="de4ff-117">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="de4ff-117">Optional enumeration.</span></span> <span data-ttu-id="de4ff-118">Kimlik bilgilerini doğrulamak için kullanılan beş modlarından birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="de4ff-119">Bu öznitelik türünde <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="de4ff-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="de4ff-120">Varsa kümesine `Custom`, sonra bir `customCertificateValidator` de sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de4ff-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="de4ff-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="de4ff-121">Optional string.</span></span> <span data-ttu-id="de4ff-122">Bir türü ve bir özel tür doğrulamak için kullanılan derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="de4ff-123">Bu öznitelik ne zaman ayarlanmalıdır `certificateValidationMode` ayarlanır `Custom`.</span><span class="sxs-lookup"><span data-stu-id="de4ff-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="de4ff-124">Bu öznitelik türünde <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="de4ff-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="de4ff-125">Varsayılan eş eş sertifikayı güvenilir kişiler deposunda karşı doğrular sertifika Doğrulayıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="de4ff-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="de4ff-126">Sertifika geçerli bir kök zincir olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="de4ff-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="de4ff-127">Farklı bir davranışı belirtmek ve bu öznitelik için özel Doğrulayıcı işaret edecek şekilde kullanmak için özel bir doğrulayıcı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de4ff-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="de4ff-128">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="de4ff-128">Optional enumeration.</span></span> <span data-ttu-id="de4ff-129">Sertifika iptal modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="de4ff-130">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="de4ff-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="de4ff-131">Sistem eş sertifika tarafından iptal edildi olduğunu doğrular iptal edilen sertifika listesinde bakan.</span><span class="sxs-lookup"><span data-stu-id="de4ff-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="de4ff-132">Bu onay çevrimiçi denetleyerek ya da bir önbelleğe alınan iptal listesi karşı gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="de4ff-133">İptal denetimi NoCheck için bu öznitelik ayarlayarak kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="de4ff-134">İsteğe bağlı numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="de4ff-134">Optional enumeration.</span></span> <span data-ttu-id="de4ff-135">Burada eş sertifika doğrulanmış tarafından güvenilen depolama konumu belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] güvenlik sistemi.</span><span class="sxs-lookup"><span data-stu-id="de4ff-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="de4ff-136">Bu öznitelik türünde <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="de4ff-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de4ff-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="de4ff-137">Child Elements</span></span>  
 <span data-ttu-id="de4ff-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="de4ff-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de4ff-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="de4ff-139">Parent Elements</span></span>  
  
|<span data-ttu-id="de4ff-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="de4ff-140">Element</span></span>|<span data-ttu-id="de4ff-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de4ff-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de4ff-142">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="de4ff-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="de4ff-143">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de4ff-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de4ff-144">Remarks</span></span>  
 <span data-ttu-id="de4ff-145">Bu öğe, ileti kimlik doğrulaması seçilirse yapılandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="de4ff-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="de4ff-146">Çıktı kanallar için her ileti tarafından sağlanan sertifika kullanılarak imzalanmıştır [ \<sertifika >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="de4ff-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="de4ff-147">Tüm iletiler, uygulamaya teslim önce tarafından belirtilen Doğrulayıcı kullanarak ileti kimlik bilgileri karşı denetlenir `customCertificateValidatorType` bu öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="de4ff-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="de4ff-148">Doğrulayıcı kabul edin veya kimlik bilgisi reddedin.</span><span class="sxs-lookup"><span data-stu-id="de4ff-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de4ff-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de4ff-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="de4ff-150">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="de4ff-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="de4ff-151">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="de4ff-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="de4ff-152">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="de4ff-152">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="de4ff-153">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="de4ff-153">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="de4ff-154">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="de4ff-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
