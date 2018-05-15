---
title: '&lt;clientCredentials&gt; Öğesi &lt;pencereleri&gt;'
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 9badcfafff4bc09a16b0b9a565a9ea5c01e26bb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="2323f-102">&lt;clientCredentials&gt; Öğesi &lt;pencereleri&gt;</span><span class="sxs-lookup"><span data-stu-id="2323f-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="2323f-103">İstemci temsil etmek için kullanılacak bir Windows kimlik bilgileri ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2323f-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="2323f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2323f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2323f-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="2323f-105">\<behaviors></span></span>  
<span data-ttu-id="2323f-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2323f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="2323f-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="2323f-107">\<behavior></span></span>  
<span data-ttu-id="2323f-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2323f-108">\<clientCredentials></span></span>  
<span data-ttu-id="2323f-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="2323f-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2323f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2323f-110">Syntax</span></span>  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2323f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2323f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2323f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2323f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2323f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2323f-113">Attributes</span></span>  
  
|<span data-ttu-id="2323f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2323f-114">Attribute</span></span>|<span data-ttu-id="2323f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2323f-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="2323f-116">İstemci iletişim kuruyorsa kimliğe bürünme tercih sunucuya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2323f-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="2323f-117">İstemcinin kimliğe bürünme modu sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="2323f-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="2323f-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2323f-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2323f-119">-Kimliği: Sunucunun kimliğini ve istemci ayrıcalıkların alabilir, ancak istemci alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="2323f-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="2323f-120">-Kimliğe bürünme: Sunucu istemcinin güvenlik bağlamı yerel sistemde kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="2323f-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="2323f-121">-Temsilci: Sunucu istemcinin güvenlik bağlamı uzak sistemlere kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="2323f-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="2323f-122">-Anonim: Sunucusu taklit veya istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="2323f-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="2323f-123">-Hiçbiri: Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="2323f-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="2323f-124">Varsayılan kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="2323f-124">The default is Identification.</span></span> <span data-ttu-id="2323f-125">Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="2323f-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="2323f-126">Bu özelliği ayarlamak `true` Kerberos kullanılabilir değilse, NTLM olarak düşürmek için kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="2323f-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="2323f-127">Bu özelliği ayarlamak `false` NTLM kullanılırsa, bir özel durum için bir en iyi çaba yapmak için Windows Communication Foundation (WCF) neden olur.</span><span class="sxs-lookup"><span data-stu-id="2323f-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="2323f-128">Bu özelliği ayarlamak Not `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyebilir değil.</span><span class="sxs-lookup"><span data-stu-id="2323f-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2323f-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2323f-129">Child Elements</span></span>  
 <span data-ttu-id="2323f-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="2323f-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2323f-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2323f-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2323f-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="2323f-132">Element</span></span>|<span data-ttu-id="2323f-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2323f-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2323f-134">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2323f-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="2323f-135">Hizmeti için istemci kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2323f-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2323f-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2323f-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="2323f-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2323f-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="2323f-138">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="2323f-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="2323f-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="2323f-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
