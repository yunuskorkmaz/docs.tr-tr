---
description: 'Hakkında daha fazla bilgi edinin: <compositeDuplex>'
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 0a9ec47027618a5f4fb30b627ccb9ad04c547f48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782188"
---
# \<compositeDuplex>

<span data-ttu-id="0f972-102">İstemci hizmetin istemciye geri ileti gönderebilmesi için bir uç nokta kullanıma sunması gerektiğinde kullanılan bağlama öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f972-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="0f972-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f972-103">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f972-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f972-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0f972-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f972-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f972-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f972-106">Attributes</span></span>  
  
|<span data-ttu-id="0f972-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0f972-107">Attribute</span></span>|<span data-ttu-id="0f972-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f972-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f972-109">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="0f972-109">clientBaseAddress</span></span>|<span data-ttu-id="0f972-110">Çift yönlü modda arka kanalın adresini ayarlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="0f972-110">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="0f972-111">Hizmet, iletişim kurmak ve istemciyle bağlantı kurmak için bu adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f972-111">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="0f972-112">Bu öznitelik ayarlanmamışsa, "" varsayılan adresi `full qualified name+default port\TemporaryIndigoAddress\guid` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0f972-112">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="0f972-113">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="0f972-113">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f972-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f972-114">Child Elements</span></span>  

 <span data-ttu-id="0f972-115">Yok</span><span class="sxs-lookup"><span data-stu-id="0f972-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f972-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f972-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0f972-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f972-117">Element</span></span>|<span data-ttu-id="0f972-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f972-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="0f972-119">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f972-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f972-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f972-120">Remarks</span></span>  

 <span data-ttu-id="0f972-121">Bu yapılandırma öğesi, çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f972-121">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="0f972-122">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0f972-122">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="0f972-123">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f972-123">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="0f972-124">Bu istemci adresi özniteliği tarafından sağlanır `clientBaseAddress` .</span><span class="sxs-lookup"><span data-stu-id="0f972-124">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="0f972-125">Windows Communication Foundation (WCF), Kullanıcı tarafından açıkça ayarlanmamışsa bir ClientBaseAddress 'in otomatik olarak üretiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0f972-125">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f972-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f972-126">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="0f972-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f972-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0f972-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0f972-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0f972-129">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="0f972-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0f972-130">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="0f972-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
