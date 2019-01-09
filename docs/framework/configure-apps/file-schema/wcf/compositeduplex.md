---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 4b84b4f2816dc68b7dcee784d957189728e5a4b2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149057"
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="f2e65-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="f2e65-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="f2e65-103">İstemcinin hizmetin istemciye geri göndermek bir uç noktası kullanıma sunması gerektiğinde kullanılan bağlama öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2e65-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="f2e65-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f2e65-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f2e65-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f2e65-105">\<bindings></span></span>  
<span data-ttu-id="f2e65-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f2e65-106">\<customBinding></span></span>  
<span data-ttu-id="f2e65-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f2e65-107">\<binding></span></span>  
<span data-ttu-id="f2e65-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="f2e65-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e65-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2e65-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2e65-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2e65-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f2e65-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2e65-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2e65-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2e65-112">Attributes</span></span>  
  
|<span data-ttu-id="f2e65-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2e65-113">Attribute</span></span>|<span data-ttu-id="f2e65-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2e65-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2e65-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f2e65-115">clientBaseAddress</span></span>|<span data-ttu-id="f2e65-116">Çift yönlü modda geri kanal adresini ayarlar bir URI.</span><span class="sxs-lookup"><span data-stu-id="f2e65-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="f2e65-117">Hizmet bu adrese başvurun ve istemci ile bağlantı kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2e65-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="f2e65-118">Bu öznitelik ayarlanmazsa, varsayılan adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f2e65-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="f2e65-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f2e65-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2e65-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2e65-120">Child Elements</span></span>  
 <span data-ttu-id="f2e65-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f2e65-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2e65-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2e65-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f2e65-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2e65-123">Element</span></span>|<span data-ttu-id="f2e65-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2e65-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2e65-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f2e65-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f2e65-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2e65-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2e65-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2e65-127">Remarks</span></span>  
 <span data-ttu-id="f2e65-128">Bu yapılandırma öğesi, çift yönlü iletişim, izin vermeyen aktarımları ile Örneğin, HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2e65-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="f2e65-129">TCP, aksine, yerel olarak çift yönlü iletişimler sağlar ve hizmetin istemciye geri göndermek bu bağlama öğesi kullanımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="f2e65-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="f2e65-130">İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2e65-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="f2e65-131">Bu istemci adresi tarafından sağlanan `clientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f2e65-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="f2e65-132">Windows Communication Foundation (WCF) otomatik-bir ClientBaseAddress bir açıkça kullanıcı tarafından ayarlanmamışsa ürettiği unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f2e65-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2e65-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2e65-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f2e65-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2e65-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f2e65-135">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f2e65-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f2e65-136">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f2e65-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f2e65-137">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f2e65-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f2e65-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f2e65-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
