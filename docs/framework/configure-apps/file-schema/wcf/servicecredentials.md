---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b5d257b3082717ba94b9a4517ed5ccd4bd325c06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936306"
---
# <a name="servicecredentials"></a><span data-ttu-id="eee62-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="eee62-101">\<serviceCredentials></span></span>
<span data-ttu-id="eee62-102">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="eee62-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eee62-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="eee62-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="eee62-104">\<behaviors></span></span>  
<span data-ttu-id="eee62-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="eee62-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="eee62-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="eee62-106">\<behavior></span></span>  
<span data-ttu-id="eee62-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="eee62-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee62-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eee62-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eee62-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eee62-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eee62-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eee62-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eee62-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eee62-111">Attributes</span></span>  
  
|<span data-ttu-id="eee62-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="eee62-112">Attribute</span></span>|<span data-ttu-id="eee62-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eee62-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="eee62-114">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="eee62-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eee62-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eee62-115">Child Elements</span></span>  
  
|<span data-ttu-id="eee62-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="eee62-116">Element</span></span>|<span data-ttu-id="eee62-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eee62-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee62-118">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="eee62-118">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="eee62-119">İstemci sertifikası bant dışı kullanılabilir olduğunda kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="eee62-120">Bu öğe istemci sertifikası doğrulama ayarlarını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="eee62-121">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="eee62-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="eee62-122">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="eee62-122">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="eee62-123">Bu hizmet için geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="eee62-124">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="eee62-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="eee62-125">\<eş ></span><span class="sxs-lookup"><span data-stu-id="eee62-125">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="eee62-126">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="eee62-127">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="eee62-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="eee62-128">\<Securekonuşma kimlik doğrulaması ></span><span class="sxs-lookup"><span data-stu-id="eee62-128">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="eee62-129">Güvenli konuşma için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="eee62-130">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="eee62-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="eee62-131">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="eee62-131">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="eee62-132">Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="eee62-133">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="eee62-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="eee62-134">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="eee62-134">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="eee62-135">Kullanıcı adı parola doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="eee62-136">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="eee62-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="eee62-137">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="eee62-137">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="eee62-138">Windows kimlik bilgisi doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="eee62-139">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="eee62-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eee62-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eee62-140">Parent Elements</span></span>  
  
|<span data-ttu-id="eee62-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="eee62-141">Element</span></span>|<span data-ttu-id="eee62-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eee62-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee62-143">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="eee62-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="eee62-144">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="eee62-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eee62-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eee62-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="eee62-146">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="eee62-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
