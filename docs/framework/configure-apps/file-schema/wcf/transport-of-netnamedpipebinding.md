---
title: <transport> , <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 9bcaae68051be2976b97989657efe53cf7a2718a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263465"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="18f8a-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="18f8a-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="18f8a-103">Adlandırılmış kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="18f8a-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="18f8a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18f8a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="18f8a-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="18f8a-105">\<bindings></span></span>  
<span data-ttu-id="18f8a-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="18f8a-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="18f8a-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="18f8a-107">\<binding></span></span>  
<span data-ttu-id="18f8a-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="18f8a-108">\<security></span></span>  
<span data-ttu-id="18f8a-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="18f8a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f8a-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18f8a-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18f8a-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="18f8a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="18f8a-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18f8a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18f8a-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="18f8a-113">Attributes</span></span>  
  
|<span data-ttu-id="18f8a-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="18f8a-114">Attribute</span></span>|<span data-ttu-id="18f8a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f8a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="18f8a-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="18f8a-116">protectionLevel</span></span>|<span data-ttu-id="18f8a-117">Adlandırılmış kanal koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="18f8a-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="18f8a-118">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="18f8a-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="18f8a-119">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="18f8a-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="18f8a-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="18f8a-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="18f8a-121">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="18f8a-121">-   None: No protection.</span></span><br /><span data-ttu-id="18f8a-122">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="18f8a-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="18f8a-123">-   EncryptAndSign: İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="18f8a-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="18f8a-124">EncryptAndSign varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="18f8a-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18f8a-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="18f8a-125">Child Elements</span></span>  
 <span data-ttu-id="18f8a-126">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="18f8a-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18f8a-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="18f8a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="18f8a-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="18f8a-128">Element</span></span>|<span data-ttu-id="18f8a-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18f8a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18f8a-130">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="18f8a-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="18f8a-131">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="18f8a-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18f8a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18f8a-132">See also</span></span>
- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="18f8a-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="18f8a-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="18f8a-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="18f8a-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="18f8a-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="18f8a-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="18f8a-136">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="18f8a-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="18f8a-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="18f8a-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
