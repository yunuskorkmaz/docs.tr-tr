---
title: <httpDigest> Öğesi
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2ceefdd7fab82025e89ad08d8423d57524c2e4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925559"
---
# <a name="httpdigest-element"></a><span data-ttu-id="32fc5-102">\<httpDigest > öğesi</span><span class="sxs-lookup"><span data-stu-id="32fc5-102">\<httpDigest> Element</span></span>
<span data-ttu-id="32fc5-103">İstemcinin bir hizmette kimlik doğrulaması yapılırken kullanılan Özet türü kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="32fc5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="32fc5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="32fc5-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="32fc5-105">\<behaviors></span></span>  
<span data-ttu-id="32fc5-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="32fc5-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="32fc5-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="32fc5-107">\<behavior></span></span>  
<span data-ttu-id="32fc5-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="32fc5-108">\<clientCredentials></span></span>  
<span data-ttu-id="32fc5-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="32fc5-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32fc5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32fc5-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32fc5-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32fc5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="32fc5-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32fc5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32fc5-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32fc5-113">Attributes</span></span>  
  
|<span data-ttu-id="32fc5-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="32fc5-114">Attribute</span></span>|<span data-ttu-id="32fc5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32fc5-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="32fc5-116">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="32fc5-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="32fc5-117">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="32fc5-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="32fc5-118">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="32fc5-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="32fc5-119">İsi Sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="32fc5-120">Ation Sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="32fc5-121">Verilmesini Sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="32fc5-122">Deðeri Sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="32fc5-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="32fc5-123">Seçim Kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="32fc5-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="32fc5-124">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-124">The default is Identification.</span></span> <span data-ttu-id="32fc5-125">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="32fc5-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32fc5-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32fc5-126">Child Elements</span></span>  
 <span data-ttu-id="32fc5-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="32fc5-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32fc5-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32fc5-128">Parent Elements</span></span>  
  
|<span data-ttu-id="32fc5-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="32fc5-129">Element</span></span>|<span data-ttu-id="32fc5-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32fc5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32fc5-131">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="32fc5-131">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="32fc5-132">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32fc5-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32fc5-133">Remarks</span></span>  
 <span data-ttu-id="32fc5-134">Özet, bir algoritma ve bir giriş kümesi kullanılarak belirlenen bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="32fc5-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="32fc5-135">Kimlik doğrulayıcı ve kimlik doğrulaması, bir algoritmaya karşı kabul ediyorum ve girdi olarak kullanılan verileri değiş tokuş ediyor.</span><span class="sxs-lookup"><span data-stu-id="32fc5-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="32fc5-136">İstemci karmayı hesaplayabilir ve hizmete gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="32fc5-137">Hizmet ayrıca karmayı hesaplar ve değerleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="32fc5-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="32fc5-138">Bir eşleşme istemciyi doğrular.</span><span class="sxs-lookup"><span data-stu-id="32fc5-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="32fc5-139">Bu özelliğin Windows ve Internet Information Services (IIS) üzerinde Active Directory etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="32fc5-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="32fc5-140">Daha fazla bilgi için bkz. [ııs 6,0 'de Özet kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="32fc5-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fc5-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32fc5-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="32fc5-142">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="32fc5-142">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="32fc5-143">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="32fc5-143">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="32fc5-144">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="32fc5-144">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="32fc5-145">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="32fc5-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
