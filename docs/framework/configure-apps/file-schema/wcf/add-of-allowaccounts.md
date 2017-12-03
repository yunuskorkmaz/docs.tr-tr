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
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="1acfc-102">&lt;allowAccounts&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="1acfc-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="1acfc-103">Bir kullanıcı hesabı işlemleri için barındıran belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="1acfc-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="1acfc-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="1acfc-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1acfc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1acfc-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1acfc-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1acfc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1acfc-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1acfc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1acfc-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1acfc-108">Attributes</span></span>  
  
|<span data-ttu-id="1acfc-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1acfc-109">Attribute</span></span>|<span data-ttu-id="1acfc-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1acfc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1acfc-111">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="1acfc-111">securityIdentifier</span></span>|<span data-ttu-id="1acfc-112">Bir kullanıcı hesabı tanımlamak için kullanılan benzersiz bir tanımlayıcı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="1acfc-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="1acfc-113">Varsayılan LocalSystem, Yöneticiler, NS, LS ve ııs_usrs değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="1acfc-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1acfc-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1acfc-114">Child Elements</span></span>  
 <span data-ttu-id="1acfc-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1acfc-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1acfc-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1acfc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1acfc-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1acfc-117">Element</span></span>|<span data-ttu-id="1acfc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1acfc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1acfc-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="1acfc-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="1acfc-120">İçeren yapılandırma öğelerinin koleksiyonu bir `securityIdentifier` kullanıcı hesapları için işlemleri barındıran belirtmek için özniteliği [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="1acfc-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1acfc-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1acfc-121">Example</span></span>  
 <span data-ttu-id="1acfc-122">Aşağıdaki yapılandırma örneğinde kullanıcı hesapları için beş varsayılan tanımlayıcıları bu koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="1acfc-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1acfc-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1acfc-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
