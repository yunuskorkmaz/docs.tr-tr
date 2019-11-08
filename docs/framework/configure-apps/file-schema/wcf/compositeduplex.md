---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736781"
---
# <a name="compositeduplex"></a><span data-ttu-id="efba7-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="efba7-101">\<compositeDuplex></span></span>
<span data-ttu-id="efba7-102">İstemci hizmetin istemciye geri ileti gönderebilmesi için bir uç nokta kullanıma sunması gerektiğinde kullanılan bağlama öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="efba7-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="efba7-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="efba7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="efba7-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="efba7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="efba7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="efba7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="efba7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="efba7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="efba7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="efba7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="efba7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="efba7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efba7-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="efba7-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efba7-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="efba7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="efba7-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="efba7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efba7-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efba7-112">Attributes</span></span>  
  
|<span data-ttu-id="efba7-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="efba7-113">Attribute</span></span>|<span data-ttu-id="efba7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efba7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efba7-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="efba7-115">clientBaseAddress</span></span>|<span data-ttu-id="efba7-116">Çift yönlü modda arka kanalın adresini ayarlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="efba7-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="efba7-117">Hizmet, iletişim kurmak ve istemciyle bağlantı kurmak için bu adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="efba7-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="efba7-118">Bu öznitelik ayarlanmamışsa, "`full qualified name+default port\TemporaryIndigoAddress\guid`" varsayılan adresi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="efba7-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="efba7-119">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="efba7-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efba7-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="efba7-120">Child Elements</span></span>  
 <span data-ttu-id="efba7-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="efba7-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efba7-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="efba7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="efba7-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="efba7-123">Element</span></span>|<span data-ttu-id="efba7-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="efba7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efba7-125">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="efba7-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="efba7-126">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="efba7-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="efba7-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="efba7-127">Remarks</span></span>  
 <span data-ttu-id="efba7-128">Bu yapılandırma öğesi, çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efba7-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="efba7-129">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="efba7-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="efba7-130">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efba7-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="efba7-131">Bu istemci adresi `clientBaseAddress` özniteliği tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="efba7-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="efba7-132">Windows Communication Foundation (WCF), Kullanıcı tarafından açıkça ayarlanmamışsa bir ClientBaseAddress 'in otomatik olarak üretiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="efba7-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efba7-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="efba7-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="efba7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efba7-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="efba7-135">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="efba7-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="efba7-136">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="efba7-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="efba7-137">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="efba7-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="efba7-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="efba7-138">\<customBinding></span></span>](custombinding.md)
