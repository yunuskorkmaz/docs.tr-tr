---
description: 'Hakkında daha fazla bilgi <windowsAuthentication> edinin: <serviceCredentials>'
title: <windowsAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 94f5804ac22a8c3ee1b8fc646ece8521ff639aec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682416"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="13f0b-103">\<windowsAuthentication> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="13f0b-103">\<windowsAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="13f0b-104">Bir Windows hizmeti kimlik bilgisinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="13f0b-104">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="13f0b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="13f0b-105">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13f0b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="13f0b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="13f0b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13f0b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13f0b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13f0b-108">Attributes</span></span>  
  
|<span data-ttu-id="13f0b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="13f0b-109">Attribute</span></span>|<span data-ttu-id="13f0b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13f0b-110">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="13f0b-111">Sistemin güvenlik bağlamındaki Windows gruplarını içerip içermediğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="13f0b-111">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="13f0b-112">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="13f0b-112">The default is `true`.</span></span><br /><br /> <span data-ttu-id="13f0b-113">Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="13f0b-113">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="13f0b-114">`false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="13f0b-114">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="13f0b-115">Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="13f0b-115">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="13f0b-116">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="13f0b-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="13f0b-117">`clientCredentialType`Bir bağlamanın özniteliği olarak ayarlandığında `Windows` , sistem anonim arayanlara izin vermez.</span><span class="sxs-lookup"><span data-stu-id="13f0b-117">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="13f0b-118">Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış çağıranların sisteme erişimine izin verildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="13f0b-118">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="13f0b-119">Bu davranışı, bu özniteliği kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13f0b-119">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="13f0b-120">Bu ayarı, çok dikkatli bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="13f0b-120">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13f0b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="13f0b-121">Child Elements</span></span>  

 <span data-ttu-id="13f0b-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="13f0b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13f0b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="13f0b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="13f0b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="13f0b-124">Element</span></span>|<span data-ttu-id="13f0b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13f0b-125">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="13f0b-126">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="13f0b-126">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13f0b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13f0b-127">Remarks</span></span>  

 <span data-ttu-id="13f0b-128">Özniteliğini ayarlayarak anonim Windows kullanıcılarına erişime izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanın `allowAnonymousLogons` .</span><span class="sxs-lookup"><span data-stu-id="13f0b-128">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="13f0b-129">Ayrıca, özniteliğini ayarlayarak kullanıcıların AuthorizationContext 'e ait olduğu grup bilgilerinin eklenip eklenmeyeceğini belirtebilirsiniz `includeWindowsGroups` .</span><span class="sxs-lookup"><span data-stu-id="13f0b-129">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="13f0b-130">`true`(Varsayılan ayar) olarak ayarlandıysa, hizmet istemcinin ait olduğu Windows gruplarını belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="13f0b-130">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f0b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13f0b-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
