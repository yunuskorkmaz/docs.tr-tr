---
title: <windowsAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ffddbae7effabcdafdc2638d588bbbf3e42d2c2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769700"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="baf36-102">\<ServiceCredentials >, \<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="baf36-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="baf36-103">Bir Windows hizmeti kimlik bilgisi ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="baf36-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="baf36-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="baf36-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="baf36-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="baf36-105">\<behaviors></span></span>  
<span data-ttu-id="baf36-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="baf36-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="baf36-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="baf36-107">\<behavior></span></span>  
<span data-ttu-id="baf36-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="baf36-108">\<serviceCredentials></span></span>  
<span data-ttu-id="baf36-109">\<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="baf36-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf36-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="baf36-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baf36-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="baf36-111">Attributes and Elements</span></span>  
 <span data-ttu-id="baf36-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="baf36-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baf36-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="baf36-113">Attributes</span></span>  
  
|<span data-ttu-id="baf36-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="baf36-114">Attribute</span></span>|<span data-ttu-id="baf36-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baf36-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="baf36-116">Sistemin Windows gruplarını güvenlik bağlamına dahil olup olmadığını belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="baf36-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="baf36-117">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="baf36-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="baf36-118">Bu öznitelik ayarını `true` tam Grup genişletme içinde sonuçları gibi bir performans etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="baf36-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="baf36-119">Bu öznitelik ayarlanan `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcıya ait.</span><span class="sxs-lookup"><span data-stu-id="baf36-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="baf36-120">Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="baf36-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="baf36-121">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="baf36-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="baf36-122">Zaman `clientCredentialType` bağlama özniteliği `Windows`, sistem anonim bir çağırıcıya izin vermeyen.</span><span class="sxs-lookup"><span data-stu-id="baf36-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="baf36-123">Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış anlamına gelir çağıranlar sisteme erişmek için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="baf36-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="baf36-124">Bu özniteliği kullanarak bu davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baf36-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="baf36-125">Bu ayarı dikkatli kullanın.</span><span class="sxs-lookup"><span data-stu-id="baf36-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baf36-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="baf36-126">Child Elements</span></span>  
 <span data-ttu-id="baf36-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="baf36-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="baf36-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="baf36-128">Parent Elements</span></span>  
  
|<span data-ttu-id="baf36-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="baf36-129">Element</span></span>|<span data-ttu-id="baf36-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="baf36-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baf36-131">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="baf36-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="baf36-132">Hizmet ve istemci kimlik doğrulama ile ilgili ayarlarda kullanılan kimlik bilgisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="baf36-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baf36-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="baf36-133">Remarks</span></span>  
 <span data-ttu-id="baf36-134">Windows kullanıcıları anonim erişim ayarlayarak izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanırsınız `allowAnonymousLogons` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="baf36-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="baf36-135">Ayrıca kullanıcıların ait olduğu grubu bilgileri ayarlayarak içinde AuthorizationContext eklenip eklenmeyeceğini belirtebilirsiniz `includeWindowsGroups` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="baf36-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="baf36-136">Bu ayarlanırsa `true` (varsayılan ayar), hizmet istemcinin ait olduğu Windows grupları belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baf36-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf36-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baf36-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
