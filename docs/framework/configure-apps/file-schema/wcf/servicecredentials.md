---
description: 'Hakkında daha fazla bilgi edinin: <serviceCredentials>'
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: c6fd39226ca2235d8f8253a7d2f2e363522870e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682871"
---
# \<serviceCredentials>

<span data-ttu-id="bb77a-102">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="bb77a-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="bb77a-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb77a-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb77a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bb77a-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb77a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb77a-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bb77a-106">Attributes</span></span>  
  
|<span data-ttu-id="bb77a-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bb77a-107">Attribute</span></span>|<span data-ttu-id="bb77a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb77a-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="bb77a-109">Bu yapılandırma öğesinin türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bb77a-109">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb77a-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb77a-110">Child Elements</span></span>  
  
|<span data-ttu-id="bb77a-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb77a-111">Element</span></span>|<span data-ttu-id="bb77a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb77a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="bb77a-113">İstemci sertifikası bant dışı kullanılabilir olduğunda kullanılacak sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-113">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="bb77a-114">Bu öğe istemci sertifikası doğrulama ayarlarını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-114">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="bb77a-115">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="bb77a-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="bb77a-116">Bu hizmet için geçerli verilen belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-116">Specifies the current issued token for this service.</span></span> <span data-ttu-id="bb77a-117">Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="bb77a-117">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="bb77a-118">Eş düğüm için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-118">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="bb77a-119">Bu öğe türündedir <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="bb77a-119">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="bb77a-120">Güvenli konuşma için geçerli kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-120">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="bb77a-121">Bu öğe türündedir <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="bb77a-121">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="bb77a-122">Kendisini tanımlamak için bir hizmet tarafından kullanılan bir sertifikayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-122">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="bb77a-123">Bu öğe türündedir <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="bb77a-123">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="bb77a-124">Kullanıcı adı parola doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-124">Specifies the settings for username password validation.</span></span> <span data-ttu-id="bb77a-125">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserNameServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="bb77a-125">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="bb77a-126">Windows kimlik bilgisi doğrulama ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-126">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="bb77a-127">Bu öğe türündedir <xref:System.ServiceModel.Configuration.WindowsServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="bb77a-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb77a-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bb77a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="bb77a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb77a-129">Element</span></span>|<span data-ttu-id="bb77a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb77a-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bb77a-131">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb77a-131">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb77a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb77a-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="bb77a-133">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="bb77a-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
