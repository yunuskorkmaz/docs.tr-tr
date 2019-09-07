---
title: <add> / <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 02654b8ab198a2b161b3044c1f3aa452761a6a4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398387"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="0848f-102">\<\<AllowAccounts > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="0848f-102">\<add> of \<allowAccounts></span></span>
<span data-ttu-id="0848f-103">WCF hizmetlerini barındıran işlemlere yönelik bir kullanıcı hesabı belirtir ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="0848f-103">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
<span data-ttu-id="0848f-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0848f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0848f-105">&nbsp;&nbsp;[ **\<System. serviceModel. Activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="0848f-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="0848f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<net. pipe >** ](net-pipe.md)</span><span class="sxs-lookup"><span data-stu-id="0848f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)</span></span>\
<span data-ttu-id="0848f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<allowAccounts >** ](allowaccounts.md)</span><span class="sxs-lookup"><span data-stu-id="0848f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)</span></span>\
<span data-ttu-id="0848f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="0848f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0848f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0848f-109">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0848f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0848f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0848f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0848f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0848f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0848f-112">Attributes</span></span>  
  
|<span data-ttu-id="0848f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0848f-113">Attribute</span></span>|<span data-ttu-id="0848f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0848f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0848f-115">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="0848f-115">securityIdentifier</span></span>|<span data-ttu-id="0848f-116">Bir kullanıcı hesabını tanımlamak için kullanılan benzersiz bir tanımlayıcıyı belirten dize.</span><span class="sxs-lookup"><span data-stu-id="0848f-116">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="0848f-117">Varsayılan değerler LocalSystem, Administrators, NS, LS ve IIS_USRS şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0848f-117">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0848f-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0848f-118">Child Elements</span></span>  
 <span data-ttu-id="0848f-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="0848f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0848f-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0848f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0848f-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="0848f-121">Element</span></span>|<span data-ttu-id="0848f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0848f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0848f-123">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="0848f-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="0848f-124">WCF hizmetlerini barındıran işlemlere yönelik kullanıcı hesaplarını belirtmek `securityIdentifier` için bir özniteliği içeren yapılandırma öğelerinin bir koleksiyonu ve paylaşım hizmetine bağlantı erişimi verilir.</span><span class="sxs-lookup"><span data-stu-id="0848f-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0848f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="0848f-125">Example</span></span>  
 <span data-ttu-id="0848f-126">Aşağıdaki yapılandırma örneği, bu koleksiyona Kullanıcı hesapları için beş varsayılan tanımlayıcı ekler.</span><span class="sxs-lookup"><span data-stu-id="0848f-126">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0848f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0848f-127">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
