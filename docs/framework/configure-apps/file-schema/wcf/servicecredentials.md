---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399634"
---
# <a name="servicecredentials"></a><span data-ttu-id="dbc17-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="dbc17-101">\<serviceCredentials></span></span>
<span data-ttu-id="dbc17-102">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
<span data-ttu-id="dbc17-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dbc17-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dbc17-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dbc17-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dbc17-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dbc17-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="dbc17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dbc17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="dbc17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dbc17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="dbc17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCredentials >**</span><span class="sxs-lookup"><span data-stu-id="dbc17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc17-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbc17-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbc17-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbc17-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dbc17-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbc17-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbc17-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbc17-112">Attributes</span></span>  
  
|<span data-ttu-id="dbc17-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dbc17-113">Attribute</span></span>|<span data-ttu-id="dbc17-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbc17-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="dbc17-115">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dbc17-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbc17-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbc17-116">Child Elements</span></span>  
  
|<span data-ttu-id="dbc17-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbc17-117">Element</span></span>|<span data-ttu-id="dbc17-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbc17-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbc17-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="dbc17-119">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="dbc17-120">İstemci sertifikası bant dışı kullanılabilir olduğunda kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="dbc17-121">Bu öğe istemci sertifikası doğrulama ayarlarını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="dbc17-122">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="dbc17-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="dbc17-123">\<IssuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="dbc17-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="dbc17-124">Bu hizmet için geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="dbc17-125">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="dbc17-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="dbc17-126">\<eş ></span><span class="sxs-lookup"><span data-stu-id="dbc17-126">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="dbc17-127">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="dbc17-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="dbc17-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="dbc17-129">\<Securekonuşma kimlik doğrulaması ></span><span class="sxs-lookup"><span data-stu-id="dbc17-129">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="dbc17-130">Güvenli konuşma için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="dbc17-131">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="dbc17-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="dbc17-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="dbc17-132">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="dbc17-133">Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="dbc17-134">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="dbc17-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="dbc17-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="dbc17-135">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="dbc17-136">Kullanıcı adı parola doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="dbc17-137">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="dbc17-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="dbc17-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="dbc17-138">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="dbc17-139">Windows kimlik bilgisi doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="dbc17-140">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="dbc17-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbc17-141">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbc17-141">Parent Elements</span></span>  
  
|<span data-ttu-id="dbc17-142">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbc17-142">Element</span></span>|<span data-ttu-id="dbc17-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbc17-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbc17-144">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="dbc17-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dbc17-145">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbc17-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbc17-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbc17-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="dbc17-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="dbc17-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
