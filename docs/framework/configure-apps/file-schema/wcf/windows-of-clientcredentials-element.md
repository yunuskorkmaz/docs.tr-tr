---
title: <windows><clientCredentials>öğesinin
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399125"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="65c1c-102">\<windows>\<clientCredentials>öğesinin</span><span class="sxs-lookup"><span data-stu-id="65c1c-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="65c1c-103">İstemciyi temsil etmek için kullanılacak bir Windows kimlik bilgisi ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="65c1c-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="65c1c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65c1c-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65c1c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="65c1c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="65c1c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65c1c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65c1c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="65c1c-107">Attributes</span></span>  
  
|<span data-ttu-id="65c1c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="65c1c-108">Attribute</span></span>|<span data-ttu-id="65c1c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65c1c-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="65c1c-110">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="65c1c-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="65c1c-111">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="65c1c-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="65c1c-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="65c1c-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="65c1c-113">-Kimlik: sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="65c1c-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="65c1c-114">-Kimliğe bürünme: sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="65c1c-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="65c1c-115">-Temsili: sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="65c1c-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="65c1c-116">-Anonim: sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="65c1c-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="65c1c-117">-None: kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="65c1c-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="65c1c-118">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="65c1c-118">The default is Identification.</span></span> <span data-ttu-id="65c1c-119">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="65c1c-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="65c1c-120">`true`Kerberos kullanılamıyorsa kimlik DOĞRULAMANıN NTLM 'ye indirgenmesini sağlamak için bu özelliği ayarlama.</span><span class="sxs-lookup"><span data-stu-id="65c1c-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="65c1c-121">NTLM kullanılıyorsa, bu özelliğin `false` bir özel durum oluşturması için Windows Communication Foundation (WCF) oluşmasına neden olacak şekilde ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="65c1c-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="65c1c-122">Bu özelliği olarak ayarlamanın `false` , NTLM kimlik bilgilerinin tel üzerinden gönderilmesini engelleyemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="65c1c-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65c1c-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="65c1c-123">Child Elements</span></span>  
 <span data-ttu-id="65c1c-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="65c1c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65c1c-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="65c1c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="65c1c-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="65c1c-126">Element</span></span>|<span data-ttu-id="65c1c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65c1c-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="65c1c-128">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="65c1c-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65c1c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65c1c-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="65c1c-130">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="65c1c-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="65c1c-131">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="65c1c-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="65c1c-132">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="65c1c-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
