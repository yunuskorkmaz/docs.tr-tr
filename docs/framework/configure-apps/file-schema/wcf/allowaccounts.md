---
description: 'Hakkında daha fazla bilgi edinin: <allowAccounts>'
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 5211d694e5318faf0cfc31b404764acb405bd096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749993"
---
# \<allowAccounts>

<span data-ttu-id="61ad7-102">Windows Communication Foundation (WCF) hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirten ve paylaşım hizmetine bağlantı erişimi verilen yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="61ad7-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="61ad7-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="61ad7-103">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61ad7-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="61ad7-104">Attributes and Elements</span></span>  

 <span data-ttu-id="61ad7-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61ad7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61ad7-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="61ad7-106">Attributes</span></span>  

 <span data-ttu-id="61ad7-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="61ad7-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="61ad7-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="61ad7-108">Child Elements</span></span>  
  
|<span data-ttu-id="61ad7-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="61ad7-109">Attribute</span></span>|<span data-ttu-id="61ad7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61ad7-110">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="61ad7-111">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı ekler ve paylaşım hizmetine bağlantı erişimi verilir</span><span class="sxs-lookup"><span data-stu-id="61ad7-111">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61ad7-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="61ad7-112">Parent Elements</span></span>  
  
|<span data-ttu-id="61ad7-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="61ad7-113">Element</span></span>|<span data-ttu-id="61ad7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61ad7-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61ad7-115">[\<net.pipe>](net-pipe.md) veya [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="61ad7-115">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="61ad7-116">Ağ kanalı veya TCP paylaşım hizmetleri için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="61ad7-116">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61ad7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61ad7-117">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
