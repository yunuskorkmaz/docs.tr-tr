---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e00cc6f3214dc9a040a9b6170271b1f4188d1631
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601629"
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="1d114-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="1d114-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="1d114-103">İstemcinin hizmetin istemciye geri göndermek bir uç noktası kullanıma sunması gerektiğinde kullanılan bağlama öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d114-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="1d114-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d114-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1d114-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="1d114-105">\<bindings></span></span>  
<span data-ttu-id="1d114-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1d114-106">\<customBinding></span></span>  
<span data-ttu-id="1d114-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1d114-107">\<binding></span></span>  
<span data-ttu-id="1d114-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="1d114-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d114-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d114-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d114-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d114-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d114-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d114-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d114-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d114-112">Attributes</span></span>  
  
|<span data-ttu-id="1d114-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1d114-113">Attribute</span></span>|<span data-ttu-id="1d114-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d114-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d114-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="1d114-115">clientBaseAddress</span></span>|<span data-ttu-id="1d114-116">Çift yönlü modda geri kanal adresini ayarlar bir URI.</span><span class="sxs-lookup"><span data-stu-id="1d114-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="1d114-117">Hizmet bu adrese başvurun ve istemci ile bağlantı kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1d114-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="1d114-118">Bu öznitelik ayarlanmazsa, varsayılan adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1d114-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="1d114-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="1d114-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d114-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d114-120">Child Elements</span></span>  
 <span data-ttu-id="1d114-121">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="1d114-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d114-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d114-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1d114-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d114-123">Element</span></span>|<span data-ttu-id="1d114-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d114-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d114-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1d114-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1d114-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1d114-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d114-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d114-127">Remarks</span></span>  
 <span data-ttu-id="1d114-128">Bu yapılandırma öğesi, çift yönlü iletişim, izin vermeyen aktarımları ile Örneğin, HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d114-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="1d114-129">TCP, aksine, yerel olarak çift yönlü iletişimler sağlar ve hizmetin istemciye geri göndermek bu bağlama öğesi kullanımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="1d114-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="1d114-130">İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d114-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="1d114-131">Bu istemci adresi tarafından sağlanan `clientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1d114-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="1d114-132">Windows Communication Foundation (WCF) otomatik-bir ClientBaseAddress bir açıkça kullanıcı tarafından ayarlanmamışsa ürettiği unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1d114-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d114-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d114-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="1d114-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d114-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1d114-135">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1d114-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1d114-136">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="1d114-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1d114-137">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1d114-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1d114-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1d114-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
