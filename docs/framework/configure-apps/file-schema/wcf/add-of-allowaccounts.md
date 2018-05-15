---
title: '&lt;allowAccounts&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 20e1052a0517bb170cf796dd40d58c298185a958
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="95d42-102">&lt;allowAccounts&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="95d42-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="95d42-103">Bir kullanıcı hesabı işlemleri için barındıran belirtir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="95d42-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="95d42-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="95d42-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d42-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95d42-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95d42-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="95d42-106">Attributes and Elements</span></span>  
 <span data-ttu-id="95d42-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="95d42-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95d42-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="95d42-108">Attributes</span></span>  
  
|<span data-ttu-id="95d42-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="95d42-109">Attribute</span></span>|<span data-ttu-id="95d42-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95d42-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95d42-111">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="95d42-111">securityIdentifier</span></span>|<span data-ttu-id="95d42-112">Bir kullanıcı hesabı tanımlamak için kullanılan benzersiz bir tanımlayıcı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="95d42-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="95d42-113">Varsayılan LocalSystem, Yöneticiler, NS, LS ve ııs_usrs değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="95d42-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95d42-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="95d42-114">Child Elements</span></span>  
 <span data-ttu-id="95d42-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="95d42-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95d42-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="95d42-116">Parent Elements</span></span>  
  
|<span data-ttu-id="95d42-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="95d42-117">Element</span></span>|<span data-ttu-id="95d42-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95d42-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d42-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="95d42-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="95d42-120">İçeren yapılandırma öğelerinin koleksiyonu bir `securityIdentifier` kullanıcı hesapları için işlemleri barındıran belirtmek için özniteliği [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri ve Paylaşım Hizmeti bağlantı erişim verilir.</span><span class="sxs-lookup"><span data-stu-id="95d42-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95d42-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="95d42-121">Example</span></span>  
 <span data-ttu-id="95d42-122">Aşağıdaki yapılandırma örneğinde kullanıcı hesapları için beş varsayılan tanımlayıcıları bu koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="95d42-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95d42-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95d42-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
