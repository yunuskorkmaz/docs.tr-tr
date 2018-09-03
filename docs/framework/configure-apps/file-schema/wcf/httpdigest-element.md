---
title: '&lt;httpDigest&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 4f3edb4a525429bfc55c4e4cfaffbfc5726dcef8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43477964"
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="4815d-102">&lt;httpDigest&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="4815d-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="4815d-103">Bir Özet belirtir bir hizmeti istemcisi kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="4815d-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="4815d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4815d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4815d-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="4815d-105">\<behaviors></span></span>  
<span data-ttu-id="4815d-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4815d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4815d-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="4815d-107">\<behavior></span></span>  
<span data-ttu-id="4815d-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="4815d-108">\<clientCredentials></span></span>  
<span data-ttu-id="4815d-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="4815d-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4815d-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4815d-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4815d-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4815d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4815d-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4815d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4815d-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4815d-113">Attributes</span></span>  
  
|<span data-ttu-id="4815d-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4815d-114">Attribute</span></span>|<span data-ttu-id="4815d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4815d-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="4815d-116">Sunucuya istemcinin iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4815d-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="4815d-117">İstemcinin kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="4815d-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="4815d-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4815d-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4815d-119">-Kimlik: Sunucu kimliğini ve istemci ayrıcalıkları elde edebilirsiniz, ancak istemci kimliğine bürünülemedi.</span><span class="sxs-lookup"><span data-stu-id="4815d-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="4815d-120">-Kimliğe bürünme: Sunucu istemcinin güvenlik bağlamı yerel sistemde kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="4815d-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="4815d-121">-Temsilci: Sunucu uzak sistemlerdeki güvenlik bağlamı istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="4815d-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="4815d-122">-Anonim: Sunucusu özelliklerini veya istemci kimliği.</span><span class="sxs-lookup"><span data-stu-id="4815d-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="4815d-123">-Yok: Bir kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="4815d-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="4815d-124">Varsayılan kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="4815d-124">The default is Identification.</span></span> <span data-ttu-id="4815d-125">Bu öznitelik türünde <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="4815d-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4815d-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4815d-126">Child Elements</span></span>  
 <span data-ttu-id="4815d-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="4815d-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4815d-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4815d-128">Parent Elements</span></span>  
  
|<span data-ttu-id="4815d-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="4815d-129">Element</span></span>|<span data-ttu-id="4815d-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4815d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4815d-131">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="4815d-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="4815d-132">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4815d-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4815d-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4815d-133">Remarks</span></span>  
 <span data-ttu-id="4815d-134">Bir Özet bir algoritma ve girişleri kümesi kullanılarak tanımlandığı karmasıdır.</span><span class="sxs-lookup"><span data-stu-id="4815d-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="4815d-135">Authenticator'ı ve kimliği doğrulanmış bir algoritma kabul edin ve girdi olarak kullanılan veri değişimi.</span><span class="sxs-lookup"><span data-stu-id="4815d-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="4815d-136">İstemci, karmayı hesaplar ve hizmetine gönderir.</span><span class="sxs-lookup"><span data-stu-id="4815d-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="4815d-137">Hizmet ayrıca karmayı hesaplar ve değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="4815d-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="4815d-138">Bir eşleşme istemci doğrular.</span><span class="sxs-lookup"><span data-stu-id="4815d-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="4815d-139">Bu özellik, Windows ve Internet Information Services (IIS) üzerinde Active Directory ile etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4815d-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="4815d-140">Daha fazla bilgi için [Özet kimlik doğrulaması IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="4815d-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4815d-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4815d-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="4815d-142">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="4815d-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="4815d-143">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4815d-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="4815d-144">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="4815d-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="4815d-145">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4815d-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
