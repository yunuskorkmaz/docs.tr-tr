---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c62f29c53d807cab397ff09c6163d924a71ea319
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926607"
---
# <a name="allowaccounts"></a><span data-ttu-id="6d6cb-101">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="6d6cb-101">\<allowAccounts></span></span>
<span data-ttu-id="6d6cb-102">Windows Communication Foundation (WCF) hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirten ve paylaşım hizmetine bağlantı erişimi verilen yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="6d6cb-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="6d6cb-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="6d6cb-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d6cb-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d6cb-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d6cb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6d6cb-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d6cb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d6cb-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6d6cb-107">Attributes</span></span>  
 <span data-ttu-id="6d6cb-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d6cb-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6d6cb-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d6cb-109">Child Elements</span></span>  
  
|<span data-ttu-id="6d6cb-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6d6cb-110">Attribute</span></span>|<span data-ttu-id="6d6cb-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d6cb-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="6d6cb-112">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="6d6cb-112">\<add></span></span>](add-of-allowaccounts.md)|<span data-ttu-id="6d6cb-113">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı ekler ve paylaşım hizmetine bağlantı erişimi verilir</span><span class="sxs-lookup"><span data-stu-id="6d6cb-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d6cb-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6d6cb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6d6cb-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d6cb-115">Element</span></span>|<span data-ttu-id="6d6cb-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d6cb-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d6cb-117">net. pipe > veya [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="6d6cb-117">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="6d6cb-118">Ağ kanalı veya TCP paylaşım hizmetleri için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d6cb-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d6cb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d6cb-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
