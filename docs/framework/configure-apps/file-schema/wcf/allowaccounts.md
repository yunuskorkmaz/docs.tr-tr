---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 3432d33c0cd65af03d2b1ac1302ca2c8ff3e0f43
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201648"
---
# \<allowAccounts>

<span data-ttu-id="ea7cd-101">Windows Communication Foundation (WCF) hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirten ve paylaşım hizmetine bağlantı erişimi verilen yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="ea7cd-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="ea7cd-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea7cd-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea7cd-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea7cd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ea7cd-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea7cd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea7cd-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea7cd-105">Attributes</span></span>  

 <span data-ttu-id="ea7cd-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="ea7cd-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea7cd-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea7cd-107">Child Elements</span></span>  
  
|<span data-ttu-id="ea7cd-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea7cd-108">Attribute</span></span>|<span data-ttu-id="ea7cd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea7cd-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="ea7cd-110">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı ekler ve paylaşım hizmetine bağlantı erişimi verilir</span><span class="sxs-lookup"><span data-stu-id="ea7cd-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea7cd-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea7cd-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ea7cd-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea7cd-112">Element</span></span>|<span data-ttu-id="ea7cd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea7cd-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea7cd-114">[\<net.pipe>](net-pipe.md) veya [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="ea7cd-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="ea7cd-115">Ağ kanalı veya TCP paylaşım hizmetleri için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea7cd-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea7cd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea7cd-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
