---
title: <windows><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399125"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="ee54c-102">\<\<ClientCredentials > öğesinin Windows ></span><span class="sxs-lookup"><span data-stu-id="ee54c-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="ee54c-103">İstemciyi temsil etmek için kullanılacak bir Windows kimlik bilgisi ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee54c-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
<span data-ttu-id="ee54c-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ee54c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ee54c-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ee54c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ee54c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ee54c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ee54c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ee54c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="ee54c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ee54c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="ee54c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ee54c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="ee54c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Windows >**</span><span class="sxs-lookup"><span data-stu-id="ee54c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee54c-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee54c-111">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee54c-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee54c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ee54c-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ee54c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee54c-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ee54c-114">Attributes</span></span>  
  
|<span data-ttu-id="ee54c-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ee54c-115">Attribute</span></span>|<span data-ttu-id="ee54c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee54c-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="ee54c-117">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ee54c-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="ee54c-118">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="ee54c-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="ee54c-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ee54c-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ee54c-120">İsi Sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="ee54c-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="ee54c-121">Ation Sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="ee54c-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="ee54c-122">Verilmesini Sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="ee54c-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="ee54c-123">Deðeri Sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="ee54c-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="ee54c-124">Seçim Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="ee54c-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="ee54c-125">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="ee54c-125">The default is Identification.</span></span> <span data-ttu-id="ee54c-126">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="ee54c-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="ee54c-127">Kerberos kullanılamıyorsa kimlik doğrulamanın `true` NTLM 'ye indirgenmesini sağlamak için bu özelliği ayarlama.</span><span class="sxs-lookup"><span data-stu-id="ee54c-127">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="ee54c-128">NTLM kullanılıyorsa, bu `false` özelliğin bir özel durum oluşturması için Windows Communication Foundation (WCF) oluşmasına neden olacak şekilde ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="ee54c-128">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="ee54c-129">Bu özelliği olarak `false` ayarlamanın, NTLM kimlik bilgilerinin tel üzerinden gönderilmesini engelleyemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ee54c-129">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee54c-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee54c-130">Child Elements</span></span>  
 <span data-ttu-id="ee54c-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="ee54c-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee54c-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ee54c-132">Parent Elements</span></span>  
  
|<span data-ttu-id="ee54c-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="ee54c-133">Element</span></span>|<span data-ttu-id="ee54c-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee54c-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee54c-135">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ee54c-135">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="ee54c-136">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee54c-136">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee54c-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee54c-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="ee54c-138">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ee54c-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ee54c-139">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="ee54c-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ee54c-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ee54c-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
