---
title: <transport> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735963"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="bbc21-102">\<netNamedPipeBinding > \<taşıma ></span><span class="sxs-lookup"><span data-stu-id="bbc21-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="bbc21-103">Adlandırılmış bir kanal için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bbc21-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="bbc21-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bbc21-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bbc21-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="bbc21-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bbc21-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bbc21-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bbc21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="bbc21-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="bbc21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="bbc21-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="bbc21-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="bbc21-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="bbc21-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<taşıma >**</span><span class="sxs-lookup"><span data-stu-id="bbc21-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbc21-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbc21-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbc21-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbc21-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bbc21-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbc21-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbc21-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbc21-114">Attributes</span></span>  
  
|<span data-ttu-id="bbc21-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bbc21-115">Attribute</span></span>|<span data-ttu-id="bbc21-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc21-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbc21-117">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="bbc21-117">protectionLevel</span></span>|<span data-ttu-id="bbc21-118">Adlandırılmış kanalın koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bbc21-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="bbc21-119">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="bbc21-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="bbc21-120">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbc21-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="bbc21-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bbc21-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bbc21-122">-None: koruma yok.</span><span class="sxs-lookup"><span data-stu-id="bbc21-122">-   None: No protection.</span></span><br /><span data-ttu-id="bbc21-123">-Sign: Iletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="bbc21-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="bbc21-124">-EncryptAndSign: Iletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="bbc21-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="bbc21-125">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="bbc21-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbc21-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbc21-126">Child Elements</span></span>  
 <span data-ttu-id="bbc21-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbc21-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbc21-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbc21-128">Parent Elements</span></span>  
  
|<span data-ttu-id="bbc21-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbc21-129">Element</span></span>|<span data-ttu-id="bbc21-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc21-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbc21-131">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="bbc21-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="bbc21-132">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bbc21-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbc21-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbc21-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="bbc21-134">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="bbc21-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="bbc21-135">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="bbc21-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bbc21-136">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bbc21-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bbc21-137">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bbc21-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bbc21-138">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="bbc21-138">\<binding></span></span>](bindings.md)
