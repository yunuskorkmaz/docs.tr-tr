---
description: 'Daha fazla bilgi edinin: <httpDigest> öğesi'
title: <httpDigest> Öğesi
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2b11edcaab88ff3a2b437b1e886997e08b8c9fee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749668"
---
# <a name="httpdigest-element"></a><span data-ttu-id="6c75a-103">\<httpDigest> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6c75a-103">\<httpDigest> Element</span></span>

<span data-ttu-id="6c75a-104">İstemcinin bir hizmette kimlik doğrulaması yapılırken kullanılan Özet türü kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-104">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="6c75a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c75a-105">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c75a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c75a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6c75a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c75a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c75a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6c75a-108">Attributes</span></span>  
  
|<span data-ttu-id="6c75a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6c75a-109">Attribute</span></span>|<span data-ttu-id="6c75a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c75a-110">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="6c75a-111">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6c75a-111">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="6c75a-112">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="6c75a-112">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="6c75a-113">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6c75a-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6c75a-114">-Kimlik: sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-114">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="6c75a-115">-Kimliğe bürünme: sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-115">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="6c75a-116">-Temsili: sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-116">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="6c75a-117">-Anonim: sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="6c75a-117">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="6c75a-118">-None: kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="6c75a-118">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="6c75a-119">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-119">The default is Identification.</span></span> <span data-ttu-id="6c75a-120">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="6c75a-120">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c75a-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c75a-121">Child Elements</span></span>  

 <span data-ttu-id="6c75a-122">Yok</span><span class="sxs-lookup"><span data-stu-id="6c75a-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c75a-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6c75a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6c75a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6c75a-124">Element</span></span>|<span data-ttu-id="6c75a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c75a-125">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="6c75a-126">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-126">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c75a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c75a-127">Remarks</span></span>  

 <span data-ttu-id="6c75a-128">Özet, bir algoritma ve bir giriş kümesi kullanılarak belirlenen bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="6c75a-128">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="6c75a-129">Kimlik doğrulayıcı ve kimlik doğrulaması, bir algoritmaya karşı kabul ediyorum ve girdi olarak kullanılan verileri değiş tokuş ediyor.</span><span class="sxs-lookup"><span data-stu-id="6c75a-129">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="6c75a-130">İstemci karmayı hesaplayabilir ve hizmete gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-130">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="6c75a-131">Hizmet ayrıca karmayı hesaplar ve değerleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="6c75a-131">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="6c75a-132">Bir eşleşme istemciyi doğrular.</span><span class="sxs-lookup"><span data-stu-id="6c75a-132">A match validates the client.</span></span>  
  
 <span data-ttu-id="6c75a-133">Bu özelliğin Windows ve Internet Information Services (IIS) üzerinde Active Directory etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c75a-133">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="6c75a-134">Daha fazla bilgi için bkz. [ııs 6,0 'de Özet kimlik doğrulaması](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="6c75a-134">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c75a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c75a-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="6c75a-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="6c75a-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6c75a-137">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6c75a-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="6c75a-138">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="6c75a-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6c75a-139">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6c75a-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
