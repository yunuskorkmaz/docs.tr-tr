---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: ebe976df9af0c316e95a1e089412e57a575a6df1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157241"
---
# <a name="clientcredentials"></a><span data-ttu-id="d09ac-101">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d09ac-101">\<clientCredentials></span></span>
<span data-ttu-id="d09ac-102">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="d09ac-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d09ac-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d09ac-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d09ac-104">\<behaviors></span></span>  
<span data-ttu-id="d09ac-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d09ac-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="d09ac-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d09ac-106">\<behavior></span></span>  
<span data-ttu-id="d09ac-107">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d09ac-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09ac-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d09ac-108">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d09ac-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d09ac-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d09ac-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d09ac-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d09ac-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d09ac-111">Attributes</span></span>  
  
|<span data-ttu-id="d09ac-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d09ac-112">Attribute</span></span>|<span data-ttu-id="d09ac-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d09ac-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="d09ac-114">Etkileşimli bir kullanıcı çalışma zamanında istemci kimlik bilgilerini seçimine dahil olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d09ac-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="d09ac-115">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="d09ac-116">Bu yapılandırma öğesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d09ac-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d09ac-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d09ac-117">Child Elements</span></span>  
  
|<span data-ttu-id="d09ac-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d09ac-118">Element</span></span>|<span data-ttu-id="d09ac-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d09ac-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d09ac-120">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="d09ac-120">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="d09ac-121">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan sertifikanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="d09ac-122">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d09ac-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="d09ac-123">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="d09ac-123">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="d09ac-124">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan bir Özet belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="d09ac-125">Bu öğe türünde <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d09ac-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="d09ac-126">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="d09ac-126">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="d09ac-127">İçin bir güvenli belirteç hizmeti (STS) istemci kimlik doğrulaması için kullanılan özel bir simge türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="d09ac-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d09ac-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="d09ac-129">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="d09ac-129">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="d09ac-130">Geçerli bir eş kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-130">Specifies a current peer credential.</span></span> <span data-ttu-id="d09ac-131">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="d09ac-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="d09ac-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="d09ac-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="d09ac-133">Hizmete istemcinin kimliğini doğrulamak için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d09ac-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="d09ac-134">Bu sertifika, sağlanan-bant hizmetinden istemciye olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="d09ac-135">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d09ac-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="d09ac-136">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="d09ac-136">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="d09ac-137">Windows kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-137">Specifies a Windows credential.</span></span> <span data-ttu-id="d09ac-138">Kimlik bilgisi geçerli iş parçacığının varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d09ac-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="d09ac-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d09ac-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d09ac-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d09ac-140">Parent Elements</span></span>  
  
|<span data-ttu-id="d09ac-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="d09ac-141">Element</span></span>|<span data-ttu-id="d09ac-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d09ac-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d09ac-143">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d09ac-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d09ac-144">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d09ac-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d09ac-145">Remarks</span></span>  
 <span data-ttu-id="d09ac-146">İstemci kimlik bilgileri, hizmetleri karşılıklı kimlik doğrulaması gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d09ac-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="d09ac-147">Bu yapılandırma bölümü de senaryolar için hizmet sertifikaları belirtmek için istemci Hizmet sertifikası ile bir hizmeti iletileri burada güvenlik altına almanız gerekir kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d09ac-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09ac-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d09ac-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="d09ac-149">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="d09ac-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d09ac-150">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d09ac-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
