---
title: <windowsAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399107"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="70e87-102">\<\<ServiceCredentials > > WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="70e87-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="70e87-103">Bir Windows hizmeti kimlik bilgisinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="70e87-103">Specifies the settings of a Windows service credential.</span></span>  
  
<span data-ttu-id="70e87-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="70e87-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70e87-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="70e87-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="70e87-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="70e87-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="70e87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="70e87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="70e87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="70e87-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="70e87-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="70e87-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="70e87-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="70e87-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70e87-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70e87-111">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e87-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="70e87-112">Attributes and Elements</span></span>  
 <span data-ttu-id="70e87-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="70e87-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e87-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="70e87-114">Attributes</span></span>  
  
|<span data-ttu-id="70e87-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="70e87-115">Attribute</span></span>|<span data-ttu-id="70e87-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70e87-116">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="70e87-117">Sistemin güvenlik bağlamındaki Windows gruplarını içerip içermediğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70e87-117">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="70e87-118">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="70e87-118">The default is `true`.</span></span><br /><br /> <span data-ttu-id="70e87-119">Bu özniteliğin olarak `true` ayarlanması, tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="70e87-119">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="70e87-120">Bir kullanıcının ait olduğu `false` grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="70e87-120">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="70e87-121">Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70e87-121">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="70e87-122">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="70e87-122">The default is `false`.</span></span><br /><br /> <span data-ttu-id="70e87-123">Bir bağlamanın `Windows`özniteliği olarak ayarlandığında, sistem anonim arayanlara izin vermez. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="70e87-123">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="70e87-124">Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış çağıranların sisteme erişimine izin verildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="70e87-124">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="70e87-125">Bu davranışı, bu özniteliği kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70e87-125">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="70e87-126">Bu ayarı, çok dikkatli bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="70e87-126">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70e87-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="70e87-127">Child Elements</span></span>  
 <span data-ttu-id="70e87-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="70e87-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70e87-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="70e87-129">Parent Elements</span></span>  
  
|<span data-ttu-id="70e87-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="70e87-130">Element</span></span>|<span data-ttu-id="70e87-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70e87-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70e87-132">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="70e87-132">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="70e87-133">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="70e87-133">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70e87-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70e87-134">Remarks</span></span>  
 <span data-ttu-id="70e87-135">`allowAnonymousLogons` Özniteliğini ayarlayarak anonim Windows kullanıcılarına erişime izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="70e87-135">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="70e87-136">Ayrıca, `includeWindowsGroups` özniteliğini ayarlayarak kullanıcıların AuthorizationContext 'e ait olduğu grup bilgilerinin eklenip eklenmeyeceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70e87-136">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="70e87-137">(Varsayılan ayar) olarak `true` ayarlandıysa, hizmet istemcinin ait olduğu Windows gruplarını belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="70e87-137">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70e87-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70e87-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
