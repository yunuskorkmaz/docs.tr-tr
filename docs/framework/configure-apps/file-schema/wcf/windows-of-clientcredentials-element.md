---
title: <windows><clientCredentials> öğesinin
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940302"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="61cba-102">\<\<ClientCredentials > öğesinin Windows ></span><span class="sxs-lookup"><span data-stu-id="61cba-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="61cba-103">İstemciyi temsil etmek için kullanılacak bir Windows kimlik bilgisi ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="61cba-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="61cba-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="61cba-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="61cba-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="61cba-105">\<behaviors></span></span>  
<span data-ttu-id="61cba-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="61cba-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="61cba-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="61cba-107">\<behavior></span></span>  
<span data-ttu-id="61cba-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="61cba-108">\<clientCredentials></span></span>  
<span data-ttu-id="61cba-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="61cba-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61cba-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61cba-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61cba-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="61cba-111">Attributes and Elements</span></span>  
 <span data-ttu-id="61cba-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61cba-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61cba-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61cba-113">Attributes</span></span>  
  
|<span data-ttu-id="61cba-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="61cba-114">Attribute</span></span>|<span data-ttu-id="61cba-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61cba-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="61cba-116">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="61cba-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="61cba-117">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="61cba-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="61cba-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="61cba-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="61cba-119">İsi Sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="61cba-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="61cba-120">Ation Sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="61cba-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="61cba-121">Verilmesini Sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="61cba-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="61cba-122">Deðeri Sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="61cba-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="61cba-123">Seçim Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="61cba-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="61cba-124">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="61cba-124">The default is Identification.</span></span> <span data-ttu-id="61cba-125">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="61cba-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="61cba-126">Kerberos kullanılamıyorsa kimlik doğrulamanın `true` NTLM 'ye indirgenmesini sağlamak için bu özelliği ayarlama.</span><span class="sxs-lookup"><span data-stu-id="61cba-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="61cba-127">NTLM kullanılıyorsa, bu `false` özelliğin bir özel durum oluşturması için Windows Communication Foundation (WCF) oluşmasına neden olacak şekilde ayarlanması.</span><span class="sxs-lookup"><span data-stu-id="61cba-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="61cba-128">Bu özelliği olarak `false` ayarlamanın, NTLM kimlik bilgilerinin tel üzerinden gönderilmesini engelleyemeyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="61cba-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61cba-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="61cba-129">Child Elements</span></span>  
 <span data-ttu-id="61cba-130">Yok.</span><span class="sxs-lookup"><span data-stu-id="61cba-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61cba-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="61cba-131">Parent Elements</span></span>  
  
|<span data-ttu-id="61cba-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="61cba-132">Element</span></span>|<span data-ttu-id="61cba-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61cba-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61cba-134">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="61cba-134">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="61cba-135">Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="61cba-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61cba-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61cba-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="61cba-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="61cba-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="61cba-138">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="61cba-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="61cba-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="61cba-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
