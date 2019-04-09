---
title: <transport> , <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a6d3dd2c24e90bdcdc6520e62dcc1dbe7ce797f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199836"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="f4eaa-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="f4eaa-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="f4eaa-103">Adlandırılmış kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="f4eaa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f4eaa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f4eaa-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f4eaa-105">\<bindings></span></span>  
<span data-ttu-id="f4eaa-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="f4eaa-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="f4eaa-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f4eaa-107">\<binding></span></span>  
<span data-ttu-id="f4eaa-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f4eaa-108">\<security></span></span>  
<span data-ttu-id="f4eaa-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="f4eaa-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4eaa-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4eaa-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4eaa-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4eaa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f4eaa-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4eaa-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4eaa-113">Attributes</span></span>  
  
|<span data-ttu-id="f4eaa-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f4eaa-114">Attribute</span></span>|<span data-ttu-id="f4eaa-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4eaa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4eaa-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="f4eaa-116">protectionLevel</span></span>|<span data-ttu-id="f4eaa-117">Adlandırılmış kanal koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="f4eaa-118">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="f4eaa-119">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="f4eaa-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f4eaa-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f4eaa-121">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-121">-   None: No protection.</span></span><br /><span data-ttu-id="f4eaa-122">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="f4eaa-123">-   EncryptAndSign: İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="f4eaa-124">EncryptAndSign varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4eaa-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4eaa-125">Child Elements</span></span>  
 <span data-ttu-id="f4eaa-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4eaa-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4eaa-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f4eaa-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="f4eaa-128">Element</span></span>|<span data-ttu-id="f4eaa-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4eaa-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4eaa-130">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="f4eaa-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="f4eaa-131">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4eaa-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4eaa-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="f4eaa-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f4eaa-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f4eaa-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f4eaa-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f4eaa-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f4eaa-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f4eaa-136">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4eaa-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f4eaa-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f4eaa-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
