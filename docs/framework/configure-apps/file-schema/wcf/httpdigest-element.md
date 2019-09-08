---
title: <httpDigest> Öğesi
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 121df39c7e4ce4de5c1f0ef87921f6269d7cc1c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785833"
---
# <a name="httpdigest-element"></a><span data-ttu-id="5295a-102">\<httpDigest > öğesi</span><span class="sxs-lookup"><span data-stu-id="5295a-102">\<httpDigest> Element</span></span>
<span data-ttu-id="5295a-103">İstemcinin bir hizmette kimlik doğrulaması yapılırken kullanılan Özet türü kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5295a-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="5295a-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5295a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5295a-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5295a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5295a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5295a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5295a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5295a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="5295a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5295a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="5295a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5295a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="5295a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**</span><span class="sxs-lookup"><span data-stu-id="5295a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5295a-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5295a-111">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5295a-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5295a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5295a-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5295a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5295a-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5295a-114">Attributes</span></span>  
  
|<span data-ttu-id="5295a-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5295a-115">Attribute</span></span>|<span data-ttu-id="5295a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5295a-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="5295a-117">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5295a-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="5295a-118">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="5295a-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="5295a-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5295a-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5295a-120">İsi Sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="5295a-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="5295a-121">Ation Sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="5295a-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="5295a-122">Verilmesini Sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="5295a-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="5295a-123">Deðeri Sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="5295a-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="5295a-124">Seçim Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="5295a-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="5295a-125">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="5295a-125">The default is Identification.</span></span> <span data-ttu-id="5295a-126">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="5295a-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5295a-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5295a-127">Child Elements</span></span>  
 <span data-ttu-id="5295a-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="5295a-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5295a-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5295a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="5295a-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="5295a-130">Element</span></span>|<span data-ttu-id="5295a-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5295a-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5295a-132">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5295a-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="5295a-133">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5295a-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5295a-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5295a-134">Remarks</span></span>  
 <span data-ttu-id="5295a-135">Özet, bir algoritma ve bir giriş kümesi kullanılarak belirlenen bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="5295a-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="5295a-136">Kimlik doğrulayıcı ve kimlik doğrulaması, bir algoritmaya karşı kabul ediyorum ve girdi olarak kullanılan verileri değiş tokuş ediyor.</span><span class="sxs-lookup"><span data-stu-id="5295a-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="5295a-137">İstemci karmayı hesaplayabilir ve hizmete gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="5295a-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="5295a-138">Hizmet ayrıca karmayı hesaplar ve değerleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="5295a-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="5295a-139">Bir eşleşme istemciyi doğrular.</span><span class="sxs-lookup"><span data-stu-id="5295a-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="5295a-140">Bu özelliğin Windows ve Internet Information Services (IIS) üzerinde Active Directory etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5295a-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="5295a-141">Daha fazla bilgi için bkz. [ııs 6,0 'de Özet kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="5295a-141">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5295a-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5295a-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="5295a-143">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="5295a-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5295a-144">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5295a-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5295a-145">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="5295a-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5295a-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5295a-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
