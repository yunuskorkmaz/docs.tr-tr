---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159854"
---
# <a name="compositeduplex"></a><span data-ttu-id="a68dd-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="a68dd-101">\<compositeDuplex></span></span>
<span data-ttu-id="a68dd-102">İstemcinin hizmetin istemciye geri göndermek bir uç noktası kullanıma sunması gerektiğinde kullanılan bağlama öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a68dd-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="a68dd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a68dd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a68dd-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a68dd-104">\<bindings></span></span>  
<span data-ttu-id="a68dd-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a68dd-105">\<customBinding></span></span>  
<span data-ttu-id="a68dd-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a68dd-106">\<binding></span></span>  
<span data-ttu-id="a68dd-107">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="a68dd-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a68dd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a68dd-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a68dd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a68dd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a68dd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a68dd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a68dd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a68dd-111">Attributes</span></span>  
  
|<span data-ttu-id="a68dd-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a68dd-112">Attribute</span></span>|<span data-ttu-id="a68dd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a68dd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a68dd-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="a68dd-114">clientBaseAddress</span></span>|<span data-ttu-id="a68dd-115">Çift yönlü modda geri kanal adresini ayarlar bir URI.</span><span class="sxs-lookup"><span data-stu-id="a68dd-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="a68dd-116">Hizmet bu adrese başvurun ve istemci ile bağlantı kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a68dd-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="a68dd-117">Bu öznitelik ayarlanmazsa, varsayılan adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a68dd-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="a68dd-118">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a68dd-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a68dd-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a68dd-119">Child Elements</span></span>  
 <span data-ttu-id="a68dd-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="a68dd-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a68dd-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a68dd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a68dd-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a68dd-122">Element</span></span>|<span data-ttu-id="a68dd-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a68dd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a68dd-124">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a68dd-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a68dd-125">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a68dd-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a68dd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a68dd-126">Remarks</span></span>  
 <span data-ttu-id="a68dd-127">Bu yapılandırma öğesi, çift yönlü iletişim, izin vermeyen aktarımları ile Örneğin, HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a68dd-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="a68dd-128">TCP, aksine, yerel olarak çift yönlü iletişimler sağlar ve hizmetin istemciye geri göndermek bu bağlama öğesi kullanımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a68dd-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="a68dd-129">İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma sunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a68dd-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="a68dd-130">Bu istemci adresi tarafından sağlanan `clientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a68dd-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="a68dd-131">Windows Communication Foundation (WCF) otomatik-bir ClientBaseAddress bir açıkça kullanıcı tarafından ayarlanmamışsa ürettiği unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a68dd-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a68dd-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="a68dd-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a68dd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a68dd-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a68dd-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a68dd-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a68dd-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a68dd-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a68dd-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a68dd-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a68dd-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a68dd-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
