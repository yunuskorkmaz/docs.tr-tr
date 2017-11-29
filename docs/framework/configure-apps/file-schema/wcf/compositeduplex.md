---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9f82d4b6ac69e0edc0a2ad2cddfd89ee6ac72db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="0e5d4-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="0e5d4-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="0e5d4-103">İstemci hizmetinin istemciye ileti göndermek bir uç nokta kullanıma sunmak yükleyen kullanılan bağlama öğesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="0e5d4-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0e5d4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0e5d4-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="0e5d4-105">\<bindings></span></span>  
<span data-ttu-id="0e5d4-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0e5d4-106">\<customBinding></span></span>  
<span data-ttu-id="0e5d4-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0e5d4-107">\<binding></span></span>  
<span data-ttu-id="0e5d4-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="0e5d4-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e5d4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e5d4-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e5d4-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e5d4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0e5d4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e5d4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0e5d4-112">Attributes</span></span>  
  
|<span data-ttu-id="0e5d4-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0e5d4-113">Attribute</span></span>|<span data-ttu-id="0e5d4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e5d4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e5d4-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="0e5d4-115">clientBaseAddress</span></span>|<span data-ttu-id="0e5d4-116">Çift yönlü modunda arka kanal adresini ayarlar URI.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="0e5d4-117">Hizmeti bu adresi başvurun ve istemci ile bağlantı kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="0e5d4-118">Bu öznitelik ayarlanmazsa, varsayılan adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="0e5d4-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e5d4-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e5d4-120">Child Elements</span></span>  
 <span data-ttu-id="0e5d4-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e5d4-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0e5d4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0e5d4-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="0e5d4-123">Element</span></span>|<span data-ttu-id="0e5d4-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e5d4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e5d4-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="0e5d4-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0e5d4-126">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e5d4-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e5d4-127">Remarks</span></span>  
 <span data-ttu-id="0e5d4-128">Bu yapılandırma öğesi, çift yönlü iletişimi yerel olarak, izin verme aktarımları ile Örneğin, HTTP kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="0e5d4-129">TCP, bunun aksine, yerel olarak çift yönlü iletişimi sağlar ve bu bağlama öğesi iletileri bir istemciye geri gönderilecek hizmeti kullanımını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="0e5d4-130">İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="0e5d4-131">Bu istemci adresi tarafından sağlanan `clientBaseAddress` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="0e5d4-132">Windows Communication Foundation (WCF) otomatik-bir ClientBaseAddress bir kullanıcı tarafından açıkça ayarlanmamış ise oluşturur olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e5d4-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e5d4-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e5d4-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e5d4-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="0e5d4-135">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="0e5d4-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0e5d4-136">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="0e5d4-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="0e5d4-137">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0e5d4-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0e5d4-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0e5d4-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
