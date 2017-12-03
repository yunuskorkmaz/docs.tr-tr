---
title: '&lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8e2fa4fe72b7b4c2f421aefa566f89492c06457
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="5e6c2-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="5e6c2-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="5e6c2-103">Hizmet ve istemci kimlik doğrulama ile ilgili ayarları kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="5e6c2-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e6c2-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-105">\<behaviors></span></span>  
<span data-ttu-id="5e6c2-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5e6c2-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-107">\<behavior></span></span>  
<span data-ttu-id="5e6c2-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e6c2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e6c2-109">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">  
   <clientCertificate>  
   </clientCertificate>  
   <issuedTokenAuthentication>  
   </issuedTokenAuthentication>  
   <peer>  
   </peer>  
   <secureConversationAuthentication>  
   </secureConversationAuthentication>  
   <serviceCertificate>  
   </serviceCertificate>  
   <userNameAuthentication>  
   </userNameAuthentication>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</serviceCredentials>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e6c2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e6c2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e6c2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e6c2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e6c2-112">Attributes</span></span>  
  
|<span data-ttu-id="5e6c2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5e6c2-113">Attribute</span></span>|<span data-ttu-id="5e6c2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e6c2-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="5e6c2-115">Bu yapılandırma öğesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e6c2-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e6c2-116">Child Elements</span></span>  
  
|<span data-ttu-id="5e6c2-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e6c2-117">Element</span></span>|<span data-ttu-id="5e6c2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e6c2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e6c2-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="5e6c2-120">İstemci sertifikası kullanılabilir-bant olduğunda kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="5e6c2-121">Bu öğe ayrıca istemci sertifikasını doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="5e6c2-122">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="5e6c2-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="5e6c2-124">Bu hizmet için geçerli verilen belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="5e6c2-125">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="5e6c2-126">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="5e6c2-127">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="5e6c2-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="5e6c2-129">\<Servicecredential ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="5e6c2-130">Güvenli bir konuşma için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="5e6c2-131">Bu öğe türünde <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="5e6c2-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="5e6c2-133">Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifika belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="5e6c2-134">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="5e6c2-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="5e6c2-136">Kullanıcı adı parola doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="5e6c2-137">Bu öğe türünde <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="5e6c2-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="5e6c2-139">Windows kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="5e6c2-140">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e6c2-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e6c2-141">Parent Elements</span></span>  
  
|<span data-ttu-id="5e6c2-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e6c2-142">Element</span></span>|<span data-ttu-id="5e6c2-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e6c2-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e6c2-144">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5e6c2-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5e6c2-145">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e6c2-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e6c2-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="5e6c2-147">Güvenlik davranışları</span><span class="sxs-lookup"><span data-stu-id="5e6c2-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
