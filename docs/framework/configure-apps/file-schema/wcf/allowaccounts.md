---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: bbfe0d5d531cf61c01f95d0e82ce0f894031d6f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="8ff7e-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="8ff7e-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="8ff7e-103">Yapılandırma öğesi kullanıcı işlemleri için Windows Communication Foundation (WCF) hizmetlerini barındıran hesapları ve Paylaşım Hizmeti bağlantı erişim izni belirten bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8ff7e-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="8ff7e-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="8ff7e-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff7e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ff7e-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ff7e-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ff7e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8ff7e-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ff7e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ff7e-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ff7e-108">Attributes</span></span>  
 <span data-ttu-id="8ff7e-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ff7e-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ff7e-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ff7e-110">Child Elements</span></span>  
  
|<span data-ttu-id="8ff7e-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ff7e-111">Attribute</span></span>|<span data-ttu-id="8ff7e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ff7e-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="8ff7e-113">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="8ff7e-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="8ff7e-114">Bu ana bilgisayar işlemleri için bir kullanıcı hesabı ekler [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir</span><span class="sxs-lookup"><span data-stu-id="8ff7e-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ff7e-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ff7e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8ff7e-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ff7e-116">Element</span></span>|<span data-ttu-id="8ff7e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ff7e-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ff7e-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) veya [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="8ff7e-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="8ff7e-119">Net kanal veya paylaşım hizmetlerinin TCP için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ff7e-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ff7e-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ff7e-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
