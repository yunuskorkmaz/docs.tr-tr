---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e79b3e1aeecc52bf41ae759dc15ebf1c8211beb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926065"
---
# <a name="compositeduplex"></a><span data-ttu-id="08eed-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="08eed-101">\<compositeDuplex></span></span>
<span data-ttu-id="08eed-102">İstemci hizmetin istemciye geri ileti gönderebilmesi için bir uç nokta kullanıma sunması gerektiğinde kullanılan bağlama öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08eed-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="08eed-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="08eed-103">\<system.serviceModel></span></span>  
<span data-ttu-id="08eed-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="08eed-104">\<bindings></span></span>  
<span data-ttu-id="08eed-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="08eed-105">\<customBinding></span></span>  
<span data-ttu-id="08eed-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="08eed-106">\<binding></span></span>  
<span data-ttu-id="08eed-107">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="08eed-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08eed-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08eed-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08eed-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="08eed-109">Attributes and Elements</span></span>  
 <span data-ttu-id="08eed-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08eed-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08eed-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="08eed-111">Attributes</span></span>  
  
|<span data-ttu-id="08eed-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="08eed-112">Attribute</span></span>|<span data-ttu-id="08eed-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08eed-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08eed-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="08eed-114">clientBaseAddress</span></span>|<span data-ttu-id="08eed-115">Çift yönlü modda arka kanalın adresini ayarlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="08eed-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="08eed-116">Hizmet, iletişim kurmak ve istemciyle bağlantı kurmak için bu adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="08eed-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="08eed-117">Bu öznitelik ayarlanmamışsa, "`full qualified name+default port\TemporaryIndigoAddress\guid`" varsayılan adresi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="08eed-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="08eed-118">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="08eed-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08eed-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="08eed-119">Child Elements</span></span>  
 <span data-ttu-id="08eed-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="08eed-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08eed-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="08eed-121">Parent Elements</span></span>  
  
|<span data-ttu-id="08eed-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="08eed-122">Element</span></span>|<span data-ttu-id="08eed-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08eed-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08eed-124">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="08eed-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="08eed-125">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08eed-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08eed-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08eed-126">Remarks</span></span>  
 <span data-ttu-id="08eed-127">Bu yapılandırma öğesi, çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08eed-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="08eed-128">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="08eed-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="08eed-129">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08eed-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="08eed-130">Bu istemci adresi `clientBaseAddress` özniteliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="08eed-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="08eed-131">Windows Communication Foundation (WCF), Kullanıcı tarafından açıkça ayarlanmamışsa bir ClientBaseAddress 'in otomatik olarak üretiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="08eed-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08eed-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="08eed-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="08eed-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08eed-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="08eed-134">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="08eed-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="08eed-135">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="08eed-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="08eed-136">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="08eed-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="08eed-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="08eed-137">\<customBinding></span></span>](custombinding.md)
