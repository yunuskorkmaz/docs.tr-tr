---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 097112a8b54467843554047882e55b62d7813c0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352883"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="68b8d-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="68b8d-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="68b8d-103">Yapılandırma öğesi kullanıcı işlemleri için Windows Communication Foundation (WCF) hizmetlerini barındıran hesapları ve Paylaşım Hizmeti bağlantı erişim izni belirten bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="68b8d-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="68b8d-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="68b8d-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b8d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68b8d-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68b8d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b8d-106">Attributes and Elements</span></span>  
 <span data-ttu-id="68b8d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="68b8d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68b8d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="68b8d-108">Attributes</span></span>  
 <span data-ttu-id="68b8d-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="68b8d-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="68b8d-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b8d-110">Child Elements</span></span>  
  
|<span data-ttu-id="68b8d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="68b8d-111">Attribute</span></span>|<span data-ttu-id="68b8d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68b8d-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="68b8d-113">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="68b8d-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="68b8d-114">WCF hizmetlerini barındırmak ve Paylaşım Hizmeti bağlantı erişim izni işlemleri için bir kullanıcı hesabı ekler</span><span class="sxs-lookup"><span data-stu-id="68b8d-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="68b8d-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="68b8d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="68b8d-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="68b8d-116">Element</span></span>|<span data-ttu-id="68b8d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68b8d-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68b8d-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) veya [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="68b8d-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="68b8d-119">Net kanal veya paylaşım hizmetlerinin TCP için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="68b8d-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68b8d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68b8d-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
