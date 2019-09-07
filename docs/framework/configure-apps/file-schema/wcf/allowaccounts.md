---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398413"
---
# <a name="allowaccounts"></a><span data-ttu-id="9957a-101">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="9957a-101">\<allowAccounts></span></span>
<span data-ttu-id="9957a-102">Windows Communication Foundation (WCF) hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirten ve paylaşım hizmetine bağlantı erişimi verilen yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="9957a-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="9957a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9957a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9957a-104">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="9957a-104">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="9957a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<net. pipe >** ](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="9957a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="9957a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowAccounts >**</span><span class="sxs-lookup"><span data-stu-id="9957a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9957a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9957a-107">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9957a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9957a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9957a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9957a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9957a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9957a-110">Attributes</span></span>  
 <span data-ttu-id="9957a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="9957a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9957a-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9957a-112">Child Elements</span></span>  
  
|<span data-ttu-id="9957a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9957a-113">Attribute</span></span>|<span data-ttu-id="9957a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9957a-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="9957a-115">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="9957a-115">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="9957a-116">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı ekler ve paylaşım hizmetine bağlantı erişimi verilir</span><span class="sxs-lookup"><span data-stu-id="9957a-116">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9957a-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9957a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9957a-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="9957a-118">Element</span></span>|<span data-ttu-id="9957a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9957a-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9957a-120">net. pipe > veya [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="9957a-120">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="9957a-121">Ağ kanalı veya TCP paylaşım hizmetleri için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9957a-121">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9957a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9957a-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
