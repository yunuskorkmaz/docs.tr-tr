---
title: <windowsAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 81793b0d58a95166bc23f98d46ce94a5f1e1d018
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940286"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="73ccf-102">\<\<ServiceCredentials > > WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="73ccf-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="73ccf-103">Bir Windows hizmeti kimlik bilgisinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="73ccf-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="73ccf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="73ccf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73ccf-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="73ccf-105">\<behaviors></span></span>  
<span data-ttu-id="73ccf-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="73ccf-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="73ccf-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="73ccf-107">\<behavior></span></span>  
<span data-ttu-id="73ccf-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="73ccf-108">\<serviceCredentials></span></span>  
<span data-ttu-id="73ccf-109">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="73ccf-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ccf-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73ccf-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73ccf-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73ccf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="73ccf-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73ccf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73ccf-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73ccf-113">Attributes</span></span>  
  
|<span data-ttu-id="73ccf-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73ccf-114">Attribute</span></span>|<span data-ttu-id="73ccf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73ccf-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="73ccf-116">Sistemin güvenlik bağlamındaki Windows gruplarını içerip içermediğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="73ccf-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="73ccf-117">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="73ccf-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="73ccf-118">Bu özniteliğin olarak `true` ayarlanması, tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73ccf-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="73ccf-119">Bir kullanıcının ait olduğu `false` grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="73ccf-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="73ccf-120">Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="73ccf-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="73ccf-121">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="73ccf-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="73ccf-122">Bir bağlamanın `Windows`özniteliği olarak ayarlandığında, sistem anonim arayanlara izin vermez. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="73ccf-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="73ccf-123">Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış çağıranların sisteme erişimine izin verildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="73ccf-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="73ccf-124">Bu davranışı, bu özniteliği kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ccf-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="73ccf-125">Bu ayarı, çok dikkatli bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="73ccf-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73ccf-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73ccf-126">Child Elements</span></span>  
 <span data-ttu-id="73ccf-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="73ccf-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73ccf-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73ccf-128">Parent Elements</span></span>  
  
|<span data-ttu-id="73ccf-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="73ccf-129">Element</span></span>|<span data-ttu-id="73ccf-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73ccf-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73ccf-131">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="73ccf-131">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="73ccf-132">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="73ccf-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73ccf-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73ccf-133">Remarks</span></span>  
 <span data-ttu-id="73ccf-134">`allowAnonymousLogons` Özniteliğini ayarlayarak anonim Windows kullanıcılarına erişime izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="73ccf-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="73ccf-135">Ayrıca, `includeWindowsGroups` özniteliğini ayarlayarak kullanıcıların AuthorizationContext 'e ait olduğu grup bilgilerinin eklenip eklenmeyeceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ccf-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="73ccf-136">(Varsayılan ayar) olarak `true` ayarlandıysa, hizmet istemcinin ait olduğu Windows gruplarını belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="73ccf-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ccf-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73ccf-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
