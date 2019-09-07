---
title: <transport> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 6ea0b1e374659bbbbb2f47630c009f823ccd4de9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399329"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="92bbd-102">\<\<NetNamedPipeBinding > aktarma ></span><span class="sxs-lookup"><span data-stu-id="92bbd-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="92bbd-103">Adlandırılmış bir kanal için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="92bbd-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="92bbd-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="92bbd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="92bbd-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="92bbd-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="92bbd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="92bbd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="92bbd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="92bbd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="92bbd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="92bbd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="92bbd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="92bbd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="92bbd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**</span><span class="sxs-lookup"><span data-stu-id="92bbd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92bbd-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92bbd-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92bbd-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="92bbd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="92bbd-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92bbd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92bbd-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="92bbd-114">Attributes</span></span>  
  
|<span data-ttu-id="92bbd-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="92bbd-115">Attribute</span></span>|<span data-ttu-id="92bbd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92bbd-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92bbd-117">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="92bbd-117">protectionLevel</span></span>|<span data-ttu-id="92bbd-118">Adlandırılmış kanalın koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="92bbd-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="92bbd-119">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="92bbd-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="92bbd-120">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="92bbd-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="92bbd-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="92bbd-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92bbd-122">Seçim Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="92bbd-122">-   None: No protection.</span></span><br /><span data-ttu-id="92bbd-123">İmzalayabilirsiniz İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="92bbd-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="92bbd-124">EncryptAndSign özelliğini İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="92bbd-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="92bbd-125">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="92bbd-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92bbd-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="92bbd-126">Child Elements</span></span>  
 <span data-ttu-id="92bbd-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="92bbd-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92bbd-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="92bbd-128">Parent Elements</span></span>  
  
|<span data-ttu-id="92bbd-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="92bbd-129">Element</span></span>|<span data-ttu-id="92bbd-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92bbd-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92bbd-131">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="92bbd-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="92bbd-132">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="92bbd-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92bbd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92bbd-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="92bbd-134">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="92bbd-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="92bbd-135">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="92bbd-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="92bbd-136">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="92bbd-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="92bbd-137">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="92bbd-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="92bbd-138">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="92bbd-138">\<binding></span></span>](../../../misc/binding.md)
