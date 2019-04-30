---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: ebe976df9af0c316e95a1e089412e57a575a6df1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673387"
---
# <a name="clientcredentials"></a><span data-ttu-id="f70be-101">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f70be-101">\<clientCredentials></span></span>
<span data-ttu-id="f70be-102">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f70be-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="f70be-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f70be-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f70be-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f70be-104">\<behaviors></span></span>  
<span data-ttu-id="f70be-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f70be-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="f70be-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f70be-106">\<behavior></span></span>  
<span data-ttu-id="f70be-107">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f70be-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f70be-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f70be-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f70be-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f70be-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f70be-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f70be-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f70be-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f70be-111">Attributes</span></span>  
  
|<span data-ttu-id="f70be-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f70be-112">Attribute</span></span>|<span data-ttu-id="f70be-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f70be-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="f70be-114">Etkileşimli bir kullanıcı çalışma zamanında istemci kimlik bilgilerini seçimine dahil olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f70be-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="f70be-115">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f70be-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="f70be-116">Bu yapılandırma öğesi türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f70be-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f70be-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f70be-117">Child Elements</span></span>  
  
|<span data-ttu-id="f70be-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f70be-118">Element</span></span>|<span data-ttu-id="f70be-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f70be-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f70be-120">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="f70be-120">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="f70be-121">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan sertifikanın belirtir.</span><span class="sxs-lookup"><span data-stu-id="f70be-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="f70be-122">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f70be-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="f70be-123">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="f70be-123">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="f70be-124">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan bir Özet belirtir.</span><span class="sxs-lookup"><span data-stu-id="f70be-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="f70be-125">Bu öğe türünde <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f70be-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="f70be-126">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="f70be-126">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="f70be-127">İçin bir güvenli belirteç hizmeti (STS) istemci kimlik doğrulaması için kullanılan özel bir simge türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f70be-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="f70be-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f70be-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="f70be-129">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="f70be-129">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="f70be-130">Geçerli bir eş kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f70be-130">Specifies a current peer credential.</span></span> <span data-ttu-id="f70be-131">Bu öğe türünde <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="f70be-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="f70be-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="f70be-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="f70be-133">Hizmete istemcinin kimliğini doğrulamak için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f70be-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="f70be-134">Bu sertifika, sağlanan-bant hizmetinden istemciye olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f70be-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="f70be-135">Bu öğe türünde <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f70be-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="f70be-136">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="f70be-136">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="f70be-137">Windows kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f70be-137">Specifies a Windows credential.</span></span> <span data-ttu-id="f70be-138">Kimlik bilgisi geçerli iş parçacığının varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f70be-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="f70be-139">Bu öğe türünde <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f70be-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f70be-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f70be-140">Parent Elements</span></span>  
  
|<span data-ttu-id="f70be-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="f70be-141">Element</span></span>|<span data-ttu-id="f70be-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f70be-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f70be-143">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f70be-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f70be-144">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f70be-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f70be-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f70be-145">Remarks</span></span>  
 <span data-ttu-id="f70be-146">İstemci kimlik bilgileri, hizmetleri karşılıklı kimlik doğrulaması gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f70be-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="f70be-147">Bu yapılandırma bölümü de senaryolar için hizmet sertifikaları belirtmek için istemci Hizmet sertifikası ile bir hizmeti iletileri burada güvenlik altına almanız gerekir kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f70be-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70be-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f70be-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="f70be-149">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="f70be-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f70be-150">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f70be-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
