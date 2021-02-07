---
description: 'Hakkında daha fazla bilgi edinin: <windows> <clientCredentials> öğe'
title: <windows><clientCredentials>öğesinin
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: d693ad914dfa02ef12a7c8520ca84be3a9595e73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682429"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="fe842-103">\<windows>\<clientCredentials>öğesinin</span><span class="sxs-lookup"><span data-stu-id="fe842-103">\<windows> of \<clientCredentials> Element</span></span>

<span data-ttu-id="fe842-104">İstemciyi temsil etmek için kullanılacak bir Windows kimlik bilgisi ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe842-104">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="fe842-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe842-105">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe842-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe842-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fe842-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe842-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe842-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe842-108">Attributes</span></span>  
  
|<span data-ttu-id="fe842-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe842-109">Attribute</span></span>|<span data-ttu-id="fe842-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe842-110">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="fe842-111">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fe842-111">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="fe842-112">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="fe842-112">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="fe842-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fe842-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fe842-114">-Kimlik: sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="fe842-114">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="fe842-115">-Kimliğe bürünme: sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="fe842-115">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="fe842-116">-Temsili: sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="fe842-116">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="fe842-117">-Anonim: sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="fe842-117">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="fe842-118">-None: kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="fe842-118">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="fe842-119">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="fe842-119">The default is Identification.</span></span> <span data-ttu-id="fe842-120">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="fe842-120">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="fe842-121">`true`Kerberos kullanılamıyorsa kimlik DOĞRULAMANıN NTLM 'ye indirgenmesini sağlamak için bu özelliği ayarlama.</span><span class="sxs-lookup"><span data-stu-id="fe842-121">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="fe842-122">NTLM kullanılıyorsa, bu özelliğin `false` bir özel durum oluşturması için Windows Communication Foundation (WCF) oluşmasına neden olacak şekilde ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="fe842-122">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="fe842-123">Bu özelliği olarak ayarlamanın `false` , NTLM kimlik bilgilerinin tel üzerinden gönderilmesini engelleyemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fe842-123">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe842-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe842-124">Child Elements</span></span>  

 <span data-ttu-id="fe842-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe842-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe842-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe842-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fe842-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe842-127">Element</span></span>|<span data-ttu-id="fe842-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe842-128">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="fe842-129">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe842-129">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe842-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe842-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="fe842-131">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fe842-131">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="fe842-132">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="fe842-132">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="fe842-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="fe842-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
