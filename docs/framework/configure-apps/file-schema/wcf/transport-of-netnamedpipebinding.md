---
title: <transport> / <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a6d3dd2c24e90bdcdc6520e62dcc1dbe7ce797f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788355"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="a69b8-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a69b8-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="a69b8-103">Adlandırılmış kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a69b8-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="a69b8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a69b8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a69b8-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a69b8-105">\<bindings></span></span>  
<span data-ttu-id="a69b8-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a69b8-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="a69b8-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a69b8-107">\<binding></span></span>  
<span data-ttu-id="a69b8-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a69b8-108">\<security></span></span>  
<span data-ttu-id="a69b8-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="a69b8-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69b8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a69b8-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a69b8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a69b8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a69b8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a69b8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a69b8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a69b8-113">Attributes</span></span>  
  
|<span data-ttu-id="a69b8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a69b8-114">Attribute</span></span>|<span data-ttu-id="a69b8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a69b8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a69b8-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a69b8-116">protectionLevel</span></span>|<span data-ttu-id="a69b8-117">Adlandırılmış kanal koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a69b8-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="a69b8-118">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="a69b8-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a69b8-119">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a69b8-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="a69b8-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a69b8-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a69b8-121">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="a69b8-121">-   None: No protection.</span></span><br /><span data-ttu-id="a69b8-122">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="a69b8-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a69b8-123">-   EncryptAndSign: İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="a69b8-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a69b8-124">EncryptAndSign varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a69b8-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a69b8-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a69b8-125">Child Elements</span></span>  
 <span data-ttu-id="a69b8-126">Yok.</span><span class="sxs-lookup"><span data-stu-id="a69b8-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a69b8-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a69b8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a69b8-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="a69b8-128">Element</span></span>|<span data-ttu-id="a69b8-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a69b8-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a69b8-130">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a69b8-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="a69b8-131">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a69b8-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a69b8-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a69b8-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="a69b8-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a69b8-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a69b8-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a69b8-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a69b8-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a69b8-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a69b8-136">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a69b8-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a69b8-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a69b8-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
