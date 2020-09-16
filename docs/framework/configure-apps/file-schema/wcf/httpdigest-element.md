---
title: <httpDigest> Öğesi
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 0ffaba218d31a77407c598f8b7fa0260daa4e39c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556908"
---
# <a name="httpdigest-element"></a><span data-ttu-id="9ab81-102">\<httpDigest> Öğesi</span><span class="sxs-lookup"><span data-stu-id="9ab81-102">\<httpDigest> Element</span></span>
<span data-ttu-id="9ab81-103">İstemcinin bir hizmette kimlik doğrulaması yapılırken kullanılan Özet türü kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="9ab81-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ab81-104">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ab81-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ab81-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9ab81-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ab81-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ab81-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ab81-107">Attributes</span></span>  
  
|<span data-ttu-id="9ab81-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ab81-108">Attribute</span></span>|<span data-ttu-id="9ab81-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ab81-109">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="9ab81-110">İstemcinin sunucuya iletişim kurduğu kimliğe bürünme tercihini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9ab81-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="9ab81-111">İstemcinin seçtiği kimliğe bürünme modu, sunucuda zorlanmaz.</span><span class="sxs-lookup"><span data-stu-id="9ab81-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="9ab81-112">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9ab81-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="9ab81-113">-Kimlik: sunucu istemcinin kimliğini ve ayrıcalıklarını alabilir, ancak istemcinin kimliğine bürünebilir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="9ab81-114">-Kimliğe bürünme: sunucu, yerel sistemde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="9ab81-115">-Temsili: sunucu, uzak sistemlerde istemcinin güvenlik bağlamını taklit edebilir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="9ab81-116">-Anonim: sunucu, istemciyi taklit edemez veya tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="9ab81-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="9ab81-117">-None: kimliğe bürünme düzeyi atanmadı.</span><span class="sxs-lookup"><span data-stu-id="9ab81-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="9ab81-118">Varsayılan değer kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-118">The default is Identification.</span></span> <span data-ttu-id="9ab81-119">Bu öznitelik türü <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="9ab81-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ab81-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ab81-120">Child Elements</span></span>  
 <span data-ttu-id="9ab81-121">Yok</span><span class="sxs-lookup"><span data-stu-id="9ab81-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ab81-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ab81-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9ab81-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ab81-123">Element</span></span>|<span data-ttu-id="9ab81-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ab81-124">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="9ab81-125">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-125">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ab81-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ab81-126">Remarks</span></span>  
 <span data-ttu-id="9ab81-127">Özet, bir algoritma ve bir giriş kümesi kullanılarak belirlenen bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="9ab81-127">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="9ab81-128">Kimlik doğrulayıcı ve kimlik doğrulaması, bir algoritmaya karşı kabul ediyorum ve girdi olarak kullanılan verileri değiş tokuş ediyor.</span><span class="sxs-lookup"><span data-stu-id="9ab81-128">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="9ab81-129">İstemci karmayı hesaplayabilir ve hizmete gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-129">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="9ab81-130">Hizmet ayrıca karmayı hesaplar ve değerleri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="9ab81-130">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="9ab81-131">Bir eşleşme istemciyi doğrular.</span><span class="sxs-lookup"><span data-stu-id="9ab81-131">A match validates the client.</span></span>  
  
 <span data-ttu-id="9ab81-132">Bu özelliğin Windows ve Internet Information Services (IIS) üzerinde Active Directory etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ab81-132">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="9ab81-133">Daha fazla bilgi için bkz. [ııs 6,0 'de Özet kimlik doğrulaması](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="9ab81-133">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab81-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ab81-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="9ab81-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="9ab81-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9ab81-136">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9ab81-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="9ab81-137">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="9ab81-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9ab81-138">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="9ab81-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
