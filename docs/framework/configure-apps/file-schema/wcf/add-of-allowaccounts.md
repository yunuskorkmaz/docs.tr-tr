---
description: 'Hakkında daha fazla bilgi <add> edinin: <allowAccounts>'
title: <add> / <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 275631c4467a888966e89a2f664b186f989ae101
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782227"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="fed5c-103">\<add> / \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="fed5c-103">\<add> of \<allowAccounts></span></span>

<span data-ttu-id="fed5c-104">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı belirtir ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="fed5c-104">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="fed5c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fed5c-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fed5c-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fed5c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fed5c-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fed5c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fed5c-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fed5c-108">Attributes</span></span>  
  
|<span data-ttu-id="fed5c-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fed5c-109">Attribute</span></span>|<span data-ttu-id="fed5c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fed5c-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fed5c-111">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="fed5c-111">securityIdentifier</span></span>|<span data-ttu-id="fed5c-112">Bir kullanıcı hesabını tanımlamak için kullanılan benzersiz bir tanımlayıcıyı belirten dize.</span><span class="sxs-lookup"><span data-stu-id="fed5c-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="fed5c-113">Varsayılan değerler LocalSystem, Administrators, NS, LS ve IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="fed5c-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fed5c-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fed5c-114">Child Elements</span></span>  

 <span data-ttu-id="fed5c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="fed5c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fed5c-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fed5c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fed5c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="fed5c-117">Element</span></span>|<span data-ttu-id="fed5c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fed5c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="fed5c-119">`securityIdentifier`WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="fed5c-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fed5c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="fed5c-120">Example</span></span>  

 <span data-ttu-id="fed5c-121">Aşağıdaki yapılandırma örneği, bu koleksiyona Kullanıcı hesapları için beş varsayılan tanımlayıcı ekler.</span><span class="sxs-lookup"><span data-stu-id="fed5c-121">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fed5c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fed5c-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
