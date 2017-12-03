---
title: '&lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20d411fbe052940fd8fc752e74d012f28ffa441b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="14d91-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="14d91-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="14d91-103">Kullanıcı hesapları için işlemleri barındıran belirtin yapılandırma öğelerinin koleksiyonunu içeren [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="14d91-103">Contains a collection of configuration elements that specify user accounts for processes that host [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="14d91-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="14d91-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d91-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14d91-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14d91-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="14d91-106">Attributes and Elements</span></span>  
 <span data-ttu-id="14d91-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14d91-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14d91-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="14d91-108">Attributes</span></span>  
 <span data-ttu-id="14d91-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="14d91-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14d91-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="14d91-110">Child Elements</span></span>  
  
|<span data-ttu-id="14d91-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="14d91-111">Attribute</span></span>|<span data-ttu-id="14d91-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14d91-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="14d91-113">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="14d91-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="14d91-114">Bu ana bilgisayar işlemleri için bir kullanıcı hesabı ekler [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir</span><span class="sxs-lookup"><span data-stu-id="14d91-114">Adds a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14d91-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="14d91-115">Parent Elements</span></span>  
  
|<span data-ttu-id="14d91-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="14d91-116">Element</span></span>|<span data-ttu-id="14d91-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14d91-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14d91-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) veya [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="14d91-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="14d91-119">Net kanal veya paylaşım hizmetlerinin TCP için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="14d91-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14d91-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14d91-120">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
