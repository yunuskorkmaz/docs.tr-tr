---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: d9f8fdf272962916cd08aede484e9bbde55b96a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227086"
---
# <a name="servicecredentials"></a><span data-ttu-id="c78ee-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c78ee-101">\<serviceCredentials></span></span>
<span data-ttu-id="c78ee-102">Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="c78ee-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c78ee-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c78ee-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c78ee-104">\<behaviors></span></span>  
<span data-ttu-id="c78ee-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c78ee-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c78ee-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c78ee-106">\<behavior></span></span>  
<span data-ttu-id="c78ee-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c78ee-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c78ee-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c78ee-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c78ee-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78ee-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c78ee-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c78ee-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c78ee-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c78ee-111">Attributes</span></span>  
  
|<span data-ttu-id="c78ee-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c78ee-112">Attribute</span></span>|<span data-ttu-id="c78ee-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c78ee-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c78ee-114">Bu yapılandırma öğesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c78ee-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c78ee-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78ee-115">Child Elements</span></span>  
  
|<span data-ttu-id="c78ee-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="c78ee-116">Element</span></span>|<span data-ttu-id="c78ee-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c78ee-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c78ee-118">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="c78ee-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="c78ee-119">İstemci sertifikası yok-bant olduğunda kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="c78ee-120">Bu öğe ayrıca istemci sertifika doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="c78ee-121">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c78ee-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="c78ee-122">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c78ee-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="c78ee-123">Bu hizmet için geçerli verilen belirteç belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="c78ee-124">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c78ee-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="c78ee-125">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="c78ee-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="c78ee-126">Bir eşdüzey düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="c78ee-127">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="c78ee-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="c78ee-128">\<Servicecredential ></span><span class="sxs-lookup"><span data-stu-id="c78ee-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="c78ee-129">Geçerli bir güvenli konuşma kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="c78ee-130">Bu öğe türünde <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c78ee-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="c78ee-131">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c78ee-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="c78ee-132">Kendisini tanımlamak için bir hizmet tarafından kullanılan sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="c78ee-133">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c78ee-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="c78ee-134">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c78ee-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="c78ee-135">Kullanıcı adı parola doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="c78ee-136">Bu öğe türünde <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c78ee-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="c78ee-137">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c78ee-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="c78ee-138">Windows kimlik doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="c78ee-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c78ee-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c78ee-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c78ee-140">Parent Elements</span></span>  
  
|<span data-ttu-id="c78ee-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="c78ee-141">Element</span></span>|<span data-ttu-id="c78ee-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c78ee-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c78ee-143">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c78ee-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c78ee-144">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c78ee-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c78ee-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c78ee-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="c78ee-146">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="c78ee-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
