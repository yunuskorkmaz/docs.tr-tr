---
title: <windowsAuthentication> / <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399107"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="e001e-102">\<windowsAuthentication> / \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="e001e-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="e001e-103">Bir Windows hizmeti kimlik bilgisinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e001e-103">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="e001e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e001e-104">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e001e-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e001e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e001e-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e001e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e001e-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e001e-107">Attributes</span></span>  
  
|<span data-ttu-id="e001e-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e001e-108">Attribute</span></span>|<span data-ttu-id="e001e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e001e-109">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="e001e-110">Sistemin güvenlik bağlamındaki Windows gruplarını içerip içermediğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e001e-110">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="e001e-111">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="e001e-111">The default is `true`.</span></span><br /><br /> <span data-ttu-id="e001e-112">Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e001e-112">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="e001e-113">`false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa, bu özniteliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e001e-113">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="e001e-114">Anonim, kimliği doğrulanmamış çağıranlara izin verilip verilmeyeceğini belirten isteğe bağlı bir Boolean özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e001e-114">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="e001e-115">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="e001e-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="e001e-116">`clientCredentialType`Bir bağlamanın özniteliği olarak ayarlandığında `Windows` , sistem anonim arayanlara izin vermez.</span><span class="sxs-lookup"><span data-stu-id="e001e-116">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="e001e-117">Bu, yalnızca etki alanı veya çalışma grubu kimliği doğrulanmış çağıranların sisteme erişimine izin verildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e001e-117">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="e001e-118">Bu davranışı, bu özniteliği kullanarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e001e-118">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="e001e-119">Bu ayarı, çok dikkatli bir şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="e001e-119">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e001e-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e001e-120">Child Elements</span></span>  
 <span data-ttu-id="e001e-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="e001e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e001e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e001e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e001e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e001e-123">Element</span></span>|<span data-ttu-id="e001e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e001e-124">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="e001e-125">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="e001e-125">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e001e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e001e-126">Remarks</span></span>  
 <span data-ttu-id="e001e-127">Özniteliğini ayarlayarak anonim Windows kullanıcılarına erişime izin verilip verilmeyeceğini belirtmek için bu öğeyi kullanın `allowAnonymousLogons` .</span><span class="sxs-lookup"><span data-stu-id="e001e-127">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="e001e-128">Ayrıca, özniteliğini ayarlayarak kullanıcıların AuthorizationContext 'e ait olduğu grup bilgilerinin eklenip eklenmeyeceğini belirtebilirsiniz `includeWindowsGroups` .</span><span class="sxs-lookup"><span data-stu-id="e001e-128">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="e001e-129">`true`(Varsayılan ayar) olarak ayarlandıysa, hizmet istemcinin ait olduğu Windows gruplarını belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e001e-129">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e001e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e001e-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
