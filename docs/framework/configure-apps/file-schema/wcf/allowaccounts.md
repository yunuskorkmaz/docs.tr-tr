---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398413"
---
# \<allowAccounts>
<span data-ttu-id="9ae54-101">Windows Communication Foundation (WCF) hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirten ve paylaşım hizmetine bağlantı erişimi verilen yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9ae54-101">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="9ae54-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ae54-102">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ae54-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ae54-103">Attributes and Elements</span></span>  
 <span data-ttu-id="9ae54-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ae54-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ae54-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ae54-105">Attributes</span></span>  
 <span data-ttu-id="9ae54-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ae54-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ae54-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ae54-107">Child Elements</span></span>  
  
|<span data-ttu-id="9ae54-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ae54-108">Attribute</span></span>|<span data-ttu-id="9ae54-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ae54-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="9ae54-110">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı ekler ve paylaşım hizmetine bağlantı erişimi verilir</span><span class="sxs-lookup"><span data-stu-id="9ae54-110">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ae54-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ae54-111">Parent Elements</span></span>  
  
|<span data-ttu-id="9ae54-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ae54-112">Element</span></span>|<span data-ttu-id="9ae54-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ae54-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ae54-114">[\<net.pipe>](net-pipe.md)veya[\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="9ae54-114">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="9ae54-115">Ağ kanalı veya TCP paylaşım hizmetleri için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ae54-115">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ae54-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ae54-116">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
