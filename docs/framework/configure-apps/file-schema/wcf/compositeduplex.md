---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a5209efddd489f8cb04b3266e6ba0bb033eeae6c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176025"
---
# \<compositeDuplex>

<span data-ttu-id="191c0-101">İstemci hizmetin istemciye geri ileti gönderebilmesi için bir uç nokta kullanıma sunması gerektiğinde kullanılan bağlama öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="191c0-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="191c0-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="191c0-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="191c0-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="191c0-103">Attributes and Elements</span></span>  

 <span data-ttu-id="191c0-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="191c0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="191c0-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="191c0-105">Attributes</span></span>  
  
|<span data-ttu-id="191c0-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="191c0-106">Attribute</span></span>|<span data-ttu-id="191c0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="191c0-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="191c0-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="191c0-108">clientBaseAddress</span></span>|<span data-ttu-id="191c0-109">Çift yönlü modda arka kanalın adresini ayarlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="191c0-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="191c0-110">Hizmet, iletişim kurmak ve istemciyle bağlantı kurmak için bu adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="191c0-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="191c0-111">Bu öznitelik ayarlanmamışsa, "" varsayılan adresi `full qualified name+default port\TemporaryIndigoAddress\guid` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="191c0-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="191c0-112">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="191c0-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="191c0-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="191c0-113">Child Elements</span></span>  

 <span data-ttu-id="191c0-114">Yok</span><span class="sxs-lookup"><span data-stu-id="191c0-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="191c0-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="191c0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="191c0-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="191c0-116">Element</span></span>|<span data-ttu-id="191c0-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="191c0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="191c0-118">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="191c0-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="191c0-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="191c0-119">Remarks</span></span>  

 <span data-ttu-id="191c0-120">Bu yapılandırma öğesi, çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="191c0-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="191c0-121">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="191c0-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="191c0-122">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="191c0-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="191c0-123">Bu istemci adresi özniteliği tarafından sağlanır `clientBaseAddress` .</span><span class="sxs-lookup"><span data-stu-id="191c0-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="191c0-124">Windows Communication Foundation (WCF), Kullanıcı tarafından açıkça ayarlanmamışsa bir ClientBaseAddress 'in otomatik olarak üretiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="191c0-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="191c0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="191c0-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="191c0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="191c0-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="191c0-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="191c0-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="191c0-128">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="191c0-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="191c0-129">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="191c0-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
