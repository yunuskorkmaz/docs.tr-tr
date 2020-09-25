---
title: <add> / <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: cd0ef5cc5f0f809bdafa23bd312e7e30fcdccc21
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181615"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="c3d27-102">\<add> / \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="c3d27-102">\<add> of \<baseAddresses></span></span>

<span data-ttu-id="c3d27-103">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3d27-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c3d27-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c3d27-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="c3d27-105">Tür</span><span class="sxs-lookup"><span data-stu-id="c3d27-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3d27-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3d27-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c3d27-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3d27-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3d27-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c3d27-108">Attributes</span></span>  
  
|<span data-ttu-id="c3d27-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c3d27-109">Attribute</span></span>|<span data-ttu-id="c3d27-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3d27-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="c3d27-111">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c3d27-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3d27-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3d27-112">Child Elements</span></span>  

 <span data-ttu-id="c3d27-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="c3d27-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3d27-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c3d27-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c3d27-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="c3d27-115">Element</span></span>|<span data-ttu-id="c3d27-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3d27-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="c3d27-117">`baseAddress`Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c3d27-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3d27-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3d27-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="c3d27-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="c3d27-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
