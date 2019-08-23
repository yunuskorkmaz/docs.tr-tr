---
title: <add> / <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 1ed0b5025ab969c45d7440f2a209426c5c87f549
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920283"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="73467-102">\<\<AllowAccounts > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="73467-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="73467-103">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı belirtir ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="73467-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="73467-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="73467-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73467-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73467-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73467-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73467-106">Attributes and Elements</span></span>  
 <span data-ttu-id="73467-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73467-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73467-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73467-108">Attributes</span></span>  
  
|<span data-ttu-id="73467-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73467-109">Attribute</span></span>|<span data-ttu-id="73467-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73467-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73467-111">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="73467-111">securityIdentifier</span></span>|<span data-ttu-id="73467-112">Bir kullanıcı hesabını tanımlamak için kullanılan benzersiz bir tanımlayıcıyı belirten dize.</span><span class="sxs-lookup"><span data-stu-id="73467-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="73467-113">Varsayılan değerler LocalSystem, Administrators, NS, LS ve IIS_USRS şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="73467-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73467-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73467-114">Child Elements</span></span>  
 <span data-ttu-id="73467-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="73467-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73467-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73467-116">Parent Elements</span></span>  
  
|<span data-ttu-id="73467-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="73467-117">Element</span></span>|<span data-ttu-id="73467-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73467-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73467-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="73467-119">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="73467-120">WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek `securityIdentifier` için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="73467-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="73467-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="73467-121">Example</span></span>  
 <span data-ttu-id="73467-122">Aşağıdaki yapılandırma örneği, bu koleksiyona Kullanıcı hesapları için beş varsayılan tanımlayıcı ekler.</span><span class="sxs-lookup"><span data-stu-id="73467-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="73467-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73467-123">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
