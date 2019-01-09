---
title: '&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1624b93344e50b0406d314e285ce94786ba6dadc
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148987"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="ed335-102">&lt;netNamedPipeBinding&gt; &lt;taşıma&gt;</span><span class="sxs-lookup"><span data-stu-id="ed335-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="ed335-103">Adlandırılmış kanal taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed335-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="ed335-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ed335-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ed335-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ed335-105">\<bindings></span></span>  
<span data-ttu-id="ed335-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="ed335-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="ed335-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ed335-107">\<binding></span></span>  
<span data-ttu-id="ed335-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ed335-108">\<security></span></span>  
<span data-ttu-id="ed335-109">\<taşıma ></span><span class="sxs-lookup"><span data-stu-id="ed335-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed335-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed335-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed335-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed335-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ed335-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed335-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed335-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed335-113">Attributes</span></span>  
  
|<span data-ttu-id="ed335-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ed335-114">Attribute</span></span>|<span data-ttu-id="ed335-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed335-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ed335-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="ed335-116">protectionLevel</span></span>|<span data-ttu-id="ed335-117">Adlandırılmış kanal koruma düzeyini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed335-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="ed335-118">İleti imzalama, bir üçüncü taraf aktarılırken iletinin oynama riskini azaltır.</span><span class="sxs-lookup"><span data-stu-id="ed335-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="ed335-119">Şifreleme, aktarım sırasında verileri düzeyinde gizlilik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed335-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="ed335-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ed335-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ed335-121">-Yok: Koruma yok.</span><span class="sxs-lookup"><span data-stu-id="ed335-121">-   None: No protection.</span></span><br /><span data-ttu-id="ed335-122">-Oturum: İmzalı iletiler.</span><span class="sxs-lookup"><span data-stu-id="ed335-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="ed335-123">-EncryptAndSign: İletileri şifrelenir ve imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="ed335-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="ed335-124">EncryptAndSign varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="ed335-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed335-125">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed335-125">Child Elements</span></span>  
 <span data-ttu-id="ed335-126">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="ed335-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed335-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed335-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ed335-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed335-128">Element</span></span>|<span data-ttu-id="ed335-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed335-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed335-130">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="ed335-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="ed335-131">Bir bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed335-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed335-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ed335-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="ed335-133">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ed335-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ed335-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="ed335-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ed335-135">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ed335-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ed335-136">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ed335-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="ed335-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ed335-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
