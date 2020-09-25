---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 63368355027856118546bc70183b41864eddb0e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172885"
---
# \<serviceCredentials>

<span data-ttu-id="e4118-101">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="e4118-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4118-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4118-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4118-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e4118-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4118-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4118-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4118-105">Attributes</span></span>  
  
|<span data-ttu-id="e4118-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e4118-106">Attribute</span></span>|<span data-ttu-id="e4118-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4118-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e4118-108">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e4118-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4118-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4118-109">Child Elements</span></span>  
  
|<span data-ttu-id="e4118-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4118-110">Element</span></span>|<span data-ttu-id="e4118-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4118-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="e4118-112">İstemci sertifikası bant dışı kullanılabilir olduğunda kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="e4118-113">Bu öğe istemci sertifikası doğrulama ayarlarını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="e4118-114">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e4118-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="e4118-115">Bu hizmet için geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="e4118-116">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e4118-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="e4118-117">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="e4118-118">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="e4118-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="e4118-119">Güvenli konuşma için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="e4118-120">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e4118-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="e4118-121">Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="e4118-122">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e4118-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="e4118-123">Kullanıcı adı parola doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="e4118-124">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserNameServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e4118-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="e4118-125">Windows kimlik bilgisi doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="e4118-126">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e4118-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4118-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4118-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e4118-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4118-128">Element</span></span>|<span data-ttu-id="e4118-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4118-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e4118-130">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e4118-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4118-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4118-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="e4118-132">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="e4118-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
