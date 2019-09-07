---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400505"
---
# <a name="clientcredentials"></a><span data-ttu-id="a8913-101">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a8913-101">\<clientCredentials></span></span>
<span data-ttu-id="a8913-102">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8913-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
<span data-ttu-id="a8913-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8913-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8913-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a8913-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a8913-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a8913-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a8913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a8913-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a8913-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a8913-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a8913-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientCredentials >**</span><span class="sxs-lookup"><span data-stu-id="a8913-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8913-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8913-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8913-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8913-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a8913-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8913-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8913-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8913-112">Attributes</span></span>  
  
|<span data-ttu-id="a8913-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8913-113">Attribute</span></span>|<span data-ttu-id="a8913-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8913-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="a8913-115">Etkileşimli bir kullanıcının çalışma zamanında istemci kimlik bilgilerini seçmeye dahil edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a8913-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="a8913-116">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a8913-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="a8913-117">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a8913-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8913-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8913-118">Child Elements</span></span>  
  
|<span data-ttu-id="a8913-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8913-119">Element</span></span>|<span data-ttu-id="a8913-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8913-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8913-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="a8913-121">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="a8913-122">Hizmetin istemcinin kimliğini doğrulamak için kullanılan sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8913-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="a8913-123">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a8913-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a8913-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="a8913-124">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="a8913-125">İstemci kimliğini hizmette doğrulamak için kullanılan bir Özet belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8913-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="a8913-126">Bu öğe türündedir <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a8913-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="a8913-127">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="a8913-127">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="a8913-128">İstemcinin kimliğini bir güvenli belirteç hizmeti 'ne (STS) doğrulamak için kullanılan özel bir belirteç türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8913-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="a8913-129">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a8913-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="a8913-130">\<eş ></span><span class="sxs-lookup"><span data-stu-id="a8913-130">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="a8913-131">Geçerli bir eş kimlik bilgisi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8913-131">Specifies a current peer credential.</span></span> <span data-ttu-id="a8913-132">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="a8913-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="a8913-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="a8913-133">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a8913-134">İstemciye hizmetin kimliğini doğrulamak için kullanılan sertifikayı belirtir ve sertifika seçeneklerini ayarlamak için bir yapı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8913-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="a8913-135">Bu sertifika, hizmetten istemciye bant dışı verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a8913-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="a8913-136">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a8913-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a8913-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="a8913-137">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="a8913-138">Windows kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8913-138">Specifies a Windows credential.</span></span> <span data-ttu-id="a8913-139">Varsayılan değer, geçerli iş parçacığının kimlik bilgileridir.</span><span class="sxs-lookup"><span data-stu-id="a8913-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="a8913-140">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a8913-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8913-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a8913-141">Parent Elements</span></span>  
  
|<span data-ttu-id="a8913-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8913-142">Element</span></span>|<span data-ttu-id="a8913-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8913-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8913-144">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="a8913-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a8913-145">Bir uç nokta davranışı belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8913-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8913-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8913-146">Remarks</span></span>  
 <span data-ttu-id="a8913-147">İstemci kimlik bilgileri, karşılıklı kimlik doğrulamanın gerekli olduğu durumlarda istemcinin kimliğini doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8913-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="a8913-148">Bu yapılandırma bölümü, istemcinin hizmet sertifikası ile iletileri güvenli hale getirmek zorunda olduğu senaryolara yönelik hizmet sertifikalarını belirtmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8913-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8913-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8913-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="a8913-150">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="a8913-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a8913-151">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a8913-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
