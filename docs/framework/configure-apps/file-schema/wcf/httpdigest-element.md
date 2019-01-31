---
title: <httpDigest> Öğesi
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: c930efbc2cd7a6dc12795d5ac1c26ea92fc36599
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259013"
---
# <a name="httpdigest-element"></a><span data-ttu-id="f7521-102">\<httpDigest > öğesi</span><span class="sxs-lookup"><span data-stu-id="f7521-102">\<httpDigest> Element</span></span>
<span data-ttu-id="f7521-103">Bir Özet belirtir bir hizmeti istemcisi kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="f7521-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="f7521-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f7521-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f7521-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f7521-105">\<behaviors></span></span>  
<span data-ttu-id="f7521-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f7521-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f7521-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="f7521-107">\<behavior></span></span>  
<span data-ttu-id="f7521-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f7521-108">\<clientCredentials></span></span>  
<span data-ttu-id="f7521-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="f7521-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7521-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7521-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7521-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7521-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f7521-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7521-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7521-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f7521-113">Attributes</span></span>  
  
|<span data-ttu-id="f7521-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f7521-114">Attribute</span></span>|<span data-ttu-id="f7521-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7521-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="f7521-116">Sunucuya istemcinin iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7521-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="f7521-117">İstemcinin kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="f7521-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="f7521-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f7521-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f7521-119">-Kimliği: Sunucunun kimliğini ve istemci ayrıcalıkları elde edebilirsiniz, ancak istemci kimliğine bürünülemedi.</span><span class="sxs-lookup"><span data-stu-id="f7521-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="f7521-120">-Kimliğe bürünme: Sunucu, istemci güvenlik bağlamı yerel sistemde bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="f7521-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="f7521-121">-Temsilci: Sunucu, uzak sistemlere istemcinin güvenlik bağlamında bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="f7521-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="f7521-122">-Anonim: Sunucu bürünerek veya istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="f7521-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="f7521-123">-Yok: Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="f7521-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="f7521-124">Varsayılan kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="f7521-124">The default is Identification.</span></span> <span data-ttu-id="f7521-125">Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="f7521-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7521-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7521-126">Child Elements</span></span>  
 <span data-ttu-id="f7521-127">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f7521-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7521-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f7521-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f7521-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="f7521-129">Element</span></span>|<span data-ttu-id="f7521-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7521-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7521-131">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f7521-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="f7521-132">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7521-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7521-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7521-133">Remarks</span></span>  
 <span data-ttu-id="f7521-134">Bir Özet bir algoritma ve girişleri kümesi kullanılarak tanımlandığı karmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f7521-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="f7521-135">Authenticator'ı ve kimliği doğrulanmış bir algoritma kabul edin ve girdi olarak kullanılan veri değişimi.</span><span class="sxs-lookup"><span data-stu-id="f7521-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="f7521-136">İstemci, karmayı hesaplar ve hizmetine gönderir.</span><span class="sxs-lookup"><span data-stu-id="f7521-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="f7521-137">Hizmet ayrıca karmayı hesaplar ve değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="f7521-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="f7521-138">Bir eşleşme istemci doğrular.</span><span class="sxs-lookup"><span data-stu-id="f7521-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="f7521-139">Bu özellik, Windows ve Internet Information Services (IIS) üzerinde Active Directory ile etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f7521-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="f7521-140">Daha fazla bilgi için [Özet kimlik doğrulaması IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="f7521-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7521-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7521-141">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="f7521-142">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="f7521-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f7521-143">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f7521-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="f7521-144">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="f7521-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f7521-145">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f7521-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
