---
title: '&lt;clientCredentials&gt; Öğesi &lt;pencereleri&gt;'
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 780d73b747feae5495ad08cb2324e7d8f8de0d7d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147479"
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="cc70a-102">&lt;clientCredentials&gt; Öğesi &lt;pencereleri&gt;</span><span class="sxs-lookup"><span data-stu-id="cc70a-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="cc70a-103">İstemciyi temsil etmek için kullanılacak Windows kimlik bilgisi ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="cc70a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc70a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc70a-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="cc70a-105">\<behaviors></span></span>  
<span data-ttu-id="cc70a-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cc70a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="cc70a-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="cc70a-107">\<behavior></span></span>  
<span data-ttu-id="cc70a-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cc70a-108">\<clientCredentials></span></span>  
<span data-ttu-id="cc70a-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="cc70a-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc70a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc70a-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc70a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc70a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cc70a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc70a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc70a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cc70a-113">Attributes</span></span>  
  
|<span data-ttu-id="cc70a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cc70a-114">Attribute</span></span>|<span data-ttu-id="cc70a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc70a-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="cc70a-116">Sunucuya istemcinin iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cc70a-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="cc70a-117">İstemcinin kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="cc70a-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="cc70a-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cc70a-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cc70a-119">-Kimliği: Sunucunun kimliğini ve istemci ayrıcalıkları elde edebilirsiniz, ancak istemci kimliğine bürünülemedi.</span><span class="sxs-lookup"><span data-stu-id="cc70a-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="cc70a-120">-Kimliğe bürünme: Sunucu, istemci güvenlik bağlamı yerel sistemde bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="cc70a-121">-Temsilci: Sunucu, uzak sistemlere istemcinin güvenlik bağlamında bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="cc70a-122">-Anonim: Sunucu bürünerek veya istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="cc70a-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="cc70a-123">-Yok: Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="cc70a-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="cc70a-124">Varsayılan kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-124">The default is Identification.</span></span> <span data-ttu-id="cc70a-125">Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="cc70a-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="cc70a-126">Bu özelliği ayarlamak `true` Kerberos kullanılamıyorsa için NTLM kimlik doğrulamasının sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc70a-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="cc70a-127">Bu özelliği ayarlamak `false` bir NTLM kullanılırsa, bir özel durum için mümkün olan en iyi hale getirmek için Windows Communication Foundation (WCF) neden olur.</span><span class="sxs-lookup"><span data-stu-id="cc70a-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="cc70a-128">Unutmayın, bu özelliği ayarlamak `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc70a-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc70a-129">Child Elements</span></span>  
 <span data-ttu-id="cc70a-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="cc70a-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc70a-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cc70a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="cc70a-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="cc70a-132">Element</span></span>|<span data-ttu-id="cc70a-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc70a-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc70a-134">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="cc70a-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="cc70a-135">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cc70a-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc70a-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc70a-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="cc70a-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cc70a-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="cc70a-138">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="cc70a-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="cc70a-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="cc70a-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
