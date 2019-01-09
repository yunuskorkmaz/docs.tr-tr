---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 61310d530cfec2862fb64155777cd0e88132f748
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145945"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="8dacb-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="8dacb-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="8dacb-103">Kullanıcı işlemleri için Windows Communication Foundation (WCF) hizmetlerini barındıran hesapları ve Paylaşım Hizmeti bağlantı erişim izni verilen belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8dacb-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="8dacb-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="8dacb-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dacb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dacb-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dacb-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dacb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8dacb-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8dacb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dacb-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8dacb-108">Attributes</span></span>  
 <span data-ttu-id="8dacb-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="8dacb-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8dacb-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dacb-110">Child Elements</span></span>  
  
|<span data-ttu-id="8dacb-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8dacb-111">Attribute</span></span>|<span data-ttu-id="8dacb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dacb-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8dacb-113">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="8dacb-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="8dacb-114">WCF hizmetleri barındırır ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemleri için bir kullanıcı hesabı ekler</span><span class="sxs-lookup"><span data-stu-id="8dacb-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dacb-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8dacb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8dacb-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="8dacb-116">Element</span></span>|<span data-ttu-id="8dacb-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8dacb-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8dacb-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) veya [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="8dacb-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="8dacb-119">Net kanal veya paylaşım hizmetlerinin TCP için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8dacb-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dacb-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8dacb-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
