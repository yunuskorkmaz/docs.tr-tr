---
title: <transport> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1e76d0962ea7b4714ef6ca1f9d4c4c3e23df5b6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934679"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="c9e22-102">\<\<NetNamedPipeBinding > aktarma ></span><span class="sxs-lookup"><span data-stu-id="c9e22-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="c9e22-103">Adlandırılmış bir kanal için taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9e22-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="c9e22-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9e22-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9e22-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c9e22-105">\<bindings></span></span>  
<span data-ttu-id="c9e22-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="c9e22-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="c9e22-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c9e22-107">\<binding></span></span>  
<span data-ttu-id="c9e22-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="c9e22-108">\<security></span></span>  
<span data-ttu-id="c9e22-109">\<Taşıma ></span><span class="sxs-lookup"><span data-stu-id="c9e22-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e22-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9e22-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9e22-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9e22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c9e22-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9e22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9e22-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c9e22-113">Attributes</span></span>  
  
|<span data-ttu-id="c9e22-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c9e22-114">Attribute</span></span>|<span data-ttu-id="c9e22-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9e22-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9e22-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="c9e22-116">protectionLevel</span></span>|<span data-ttu-id="c9e22-117">Adlandırılmış kanalın koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9e22-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="c9e22-118">İmzalama iletileri, üçüncü bir tarafın aktarılırken ileti üzerinde izinsiz değişiklik yaptığı riski azaltır.</span><span class="sxs-lookup"><span data-stu-id="c9e22-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="c9e22-119">Şifreleme, aktarım sırasında veri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e22-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="c9e22-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c9e22-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c9e22-121">Seçim Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="c9e22-121">-   None: No protection.</span></span><br /><span data-ttu-id="c9e22-122">İmzalayabilirsiniz İletiler imzalanır.</span><span class="sxs-lookup"><span data-stu-id="c9e22-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="c9e22-123">EncryptAndSign özelliğini İletiler şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="c9e22-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="c9e22-124">Varsayılan değer EncryptAndSign ' dır.</span><span class="sxs-lookup"><span data-stu-id="c9e22-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9e22-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9e22-125">Child Elements</span></span>  
 <span data-ttu-id="c9e22-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="c9e22-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9e22-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c9e22-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c9e22-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="c9e22-128">Element</span></span>|<span data-ttu-id="c9e22-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9e22-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9e22-130">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="c9e22-130">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="c9e22-131">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9e22-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9e22-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9e22-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="c9e22-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c9e22-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c9e22-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c9e22-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c9e22-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c9e22-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c9e22-136">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c9e22-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c9e22-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c9e22-137">\<binding></span></span>](../../../misc/binding.md)
