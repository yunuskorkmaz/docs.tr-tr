---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: f9def3004b116afdc629de136cdfe0b0eb6e75c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102628"
---
# <a name="allowaccounts"></a><span data-ttu-id="7442e-101">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="7442e-101">\<allowAccounts></span></span>
<span data-ttu-id="7442e-102">Kullanıcı işlemleri için Windows Communication Foundation (WCF) hizmetlerini barındıran hesapları ve Paylaşım Hizmeti bağlantı erişim izni verilen belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="7442e-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="7442e-103">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="7442e-103">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7442e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7442e-104">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7442e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7442e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7442e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7442e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7442e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7442e-107">Attributes</span></span>  
 <span data-ttu-id="7442e-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="7442e-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7442e-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7442e-109">Child Elements</span></span>  
  
|<span data-ttu-id="7442e-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7442e-110">Attribute</span></span>|<span data-ttu-id="7442e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7442e-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="7442e-112">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="7442e-112">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="7442e-113">WCF hizmetleri barındırır ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemleri için bir kullanıcı hesabı ekler</span><span class="sxs-lookup"><span data-stu-id="7442e-113">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7442e-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7442e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7442e-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="7442e-115">Element</span></span>|<span data-ttu-id="7442e-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7442e-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7442e-117">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) veya [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="7442e-117">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="7442e-118">Net kanal veya paylaşım hizmetlerinin TCP için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7442e-118">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7442e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7442e-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
