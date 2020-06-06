---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736781"
---
# \<compositeDuplex>
<span data-ttu-id="54e6b-101">İstemci hizmetin istemciye geri ileti gönderebilmesi için bir uç nokta kullanıma sunması gerektiğinde kullanılan bağlama öğesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="54e6b-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="54e6b-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54e6b-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54e6b-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54e6b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="54e6b-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54e6b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54e6b-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54e6b-105">Attributes</span></span>  
  
|<span data-ttu-id="54e6b-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="54e6b-106">Attribute</span></span>|<span data-ttu-id="54e6b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e6b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54e6b-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="54e6b-108">clientBaseAddress</span></span>|<span data-ttu-id="54e6b-109">Çift yönlü modda arka kanalın adresini ayarlayan bir URI.</span><span class="sxs-lookup"><span data-stu-id="54e6b-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="54e6b-110">Hizmet, iletişim kurmak ve istemciyle bağlantı kurmak için bu adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="54e6b-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="54e6b-111">Bu öznitelik ayarlanmamışsa, "" varsayılan adresi `full qualified name+default port\TemporaryIndigoAddress\guid` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="54e6b-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="54e6b-112">Varsayılan değer: `null`.</span><span class="sxs-lookup"><span data-stu-id="54e6b-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54e6b-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54e6b-113">Child Elements</span></span>  
 <span data-ttu-id="54e6b-114">Yok</span><span class="sxs-lookup"><span data-stu-id="54e6b-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54e6b-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54e6b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="54e6b-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="54e6b-116">Element</span></span>|<span data-ttu-id="54e6b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e6b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="54e6b-118">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="54e6b-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54e6b-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54e6b-119">Remarks</span></span>  
 <span data-ttu-id="54e6b-120">Bu yapılandırma öğesi, çift yönlü iletişimleri yerel olarak (örneğin, HTTP) izin verilmeyen aktarımlarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54e6b-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="54e6b-121">Bunun aksine TCP, çift yönlü iletişimleri yerel olarak sağlar ve hizmetin istemciye geri ileti gönderebilmesi için bu bağlama öğesinin kullanılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="54e6b-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="54e6b-122">İstemci, iletişim kurmak ve bağlantı kurmak için hizmetin bir adresini kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54e6b-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="54e6b-123">Bu istemci adresi özniteliği tarafından sağlanır `clientBaseAddress` .</span><span class="sxs-lookup"><span data-stu-id="54e6b-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="54e6b-124">Windows Communication Foundation (WCF), Kullanıcı tarafından açıkça ayarlanmamışsa bir ClientBaseAddress 'in otomatik olarak üretiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="54e6b-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54e6b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="54e6b-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="54e6b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54e6b-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="54e6b-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="54e6b-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="54e6b-128">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="54e6b-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="54e6b-129">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="54e6b-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
