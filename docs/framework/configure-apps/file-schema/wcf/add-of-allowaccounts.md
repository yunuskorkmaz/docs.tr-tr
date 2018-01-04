---
title: '&lt;allowAccounts&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 064c9d438832142e1f761d0d33db528dbe73ef2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="2b23f-102">&lt;allowAccounts&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="2b23f-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="2b23f-103">Bir kullanıcı hesabı işlemleri için barındıran belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="2b23f-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="2b23f-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="2b23f-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b23f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b23f-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b23f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b23f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2b23f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b23f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b23f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b23f-108">Attributes</span></span>  
  
|<span data-ttu-id="2b23f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2b23f-109">Attribute</span></span>|<span data-ttu-id="2b23f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b23f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b23f-111">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="2b23f-111">securityIdentifier</span></span>|<span data-ttu-id="2b23f-112">Bir kullanıcı hesabı tanımlamak için kullanılan benzersiz bir tanımlayıcı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b23f-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="2b23f-113">Varsayılan LocalSystem, Yöneticiler, NS, LS ve ııs_usrs değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="2b23f-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b23f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b23f-114">Child Elements</span></span>  
 <span data-ttu-id="2b23f-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="2b23f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b23f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b23f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="2b23f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b23f-117">Element</span></span>|<span data-ttu-id="2b23f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b23f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b23f-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="2b23f-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="2b23f-120">İçeren yapılandırma öğelerinin koleksiyonu bir `securityIdentifier` kullanıcı hesapları için işlemleri barındıran belirtmek için özniteliği [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="2b23f-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b23f-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b23f-121">Example</span></span>  
 <span data-ttu-id="2b23f-122">Aşağıdaki yapılandırma örneğinde kullanıcı hesapları için beş varsayılan tanımlayıcıları bu koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="2b23f-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b23f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b23f-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
