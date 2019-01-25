---
title: '&lt;allowAccounts&gt;'
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: c1c4630e6191dbbe02688a4e4a9db9e18b8d36d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508424"
---
# <a name="ltallowaccountsgt"></a><span data-ttu-id="f1210-102">&lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="f1210-102">&lt;allowAccounts&gt;</span></span>
<span data-ttu-id="f1210-103">Kullanıcı işlemleri için Windows Communication Foundation (WCF) hizmetlerini barındıran hesapları ve Paylaşım Hizmeti bağlantı erişim izni verilen belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f1210-103">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="f1210-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="f1210-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1210-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1210-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1210-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1210-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f1210-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1210-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1210-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f1210-108">Attributes</span></span>  
 <span data-ttu-id="f1210-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="f1210-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f1210-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1210-110">Child Elements</span></span>  
  
|<span data-ttu-id="f1210-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f1210-111">Attribute</span></span>|<span data-ttu-id="f1210-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1210-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="f1210-113">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="f1210-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowaccounts.md)|<span data-ttu-id="f1210-114">WCF hizmetleri barındırır ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemleri için bir kullanıcı hesabı ekler</span><span class="sxs-lookup"><span data-stu-id="f1210-114">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1210-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f1210-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f1210-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f1210-116">Element</span></span>|<span data-ttu-id="f1210-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1210-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1210-118">[\<NET.pipe >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) veya [ \<net.tcp >](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="f1210-118">[\<net.pipe>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-pipe.md) or [\<net.tcp>](../../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)</span></span>|<span data-ttu-id="f1210-119">Net kanal veya paylaşım hizmetlerinin TCP için yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1210-119">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1210-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1210-120">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
