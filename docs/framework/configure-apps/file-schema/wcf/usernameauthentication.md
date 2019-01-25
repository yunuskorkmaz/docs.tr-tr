---
title: '&lt;UserNameAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 1b8a85a3b2699aa88db24d1f7afee3de67dbf39b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656654"
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="a9b80-102">&lt;UserNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="a9b80-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="a9b80-103">Kullanıcı adı ve parolasına dayalı bir hizmetin kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="a9b80-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a9b80-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a9b80-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a9b80-105">\<behaviors></span></span>  
<span data-ttu-id="a9b80-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a9b80-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="a9b80-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a9b80-107">\<behavior></span></span>  
<span data-ttu-id="a9b80-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a9b80-108">\<serviceCredentials></span></span>  
<span data-ttu-id="a9b80-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="a9b80-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b80-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9b80-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9b80-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9b80-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a9b80-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9b80-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9b80-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9b80-113">Attributes</span></span>  
  
|<span data-ttu-id="a9b80-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a9b80-114">Attribute</span></span>|<span data-ttu-id="a9b80-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9b80-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="a9b80-116">A <xref:System.TimeSpan> bir belirteç önbelleğe alınma süresi en büyük uzunluğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="a9b80-117">Varsayılan değer 00:15:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="a9b80-118">Oturum açma belirteçlerinin önbelleğe yazılıp yazılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a9b80-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="a9b80-119">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="a9b80-120">Kullanılacak özel kullanıcı adı parola Doğrulayıcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a9b80-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="a9b80-121">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="a9b80-122">Windows gruplarını güvenlik bağlamına dahil olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="a9b80-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="a9b80-123">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="a9b80-124">Bu öznitelik ayarını `true` tam Grup genişletme içinde sonuçları gibi bir performans etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="a9b80-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="a9b80-125">Bu özellik kümesine `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcıya ait.</span><span class="sxs-lookup"><span data-stu-id="a9b80-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="a9b80-126">Oturum açma belirteçlerinin önbelleğe maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a9b80-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="a9b80-127">Bu değer, sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9b80-127">This value should be larger than zero.</span></span> <span data-ttu-id="a9b80-128">Varsayılan değer 128'dir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="a9b80-129">Zaman `clientCredentialType` bağlama özniteliği `username`, kullanıcı adı Windows hesaplarına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="a9b80-130">Bu öznitelik adını içeren bir dize kullanarak bu davranışı geçersiz kılabilirsiniz <xref:System.Web.Security.MembershipProvider> değer ilgili parola doğrulama mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9b80-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="a9b80-131">Kullanıcı adı şifrenin doğrulanacağı şekli belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="a9b80-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a9b80-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="a9b80-133">-   Windows</span><span class="sxs-lookup"><span data-stu-id="a9b80-133">-   Windows</span></span><br /><span data-ttu-id="a9b80-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="a9b80-134">-   MembershipProvider</span></span><br /><span data-ttu-id="a9b80-135">-Özel</span><span class="sxs-lookup"><span data-stu-id="a9b80-135">-   Custom</span></span><br /><br /> <span data-ttu-id="a9b80-136">Windows varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a9b80-136">The default is Windows.</span></span> <span data-ttu-id="a9b80-137">Bu öznitelik türünde <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="a9b80-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9b80-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9b80-138">Child Elements</span></span>  
 <span data-ttu-id="a9b80-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="a9b80-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9b80-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9b80-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a9b80-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9b80-141">Element</span></span>|<span data-ttu-id="a9b80-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9b80-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9b80-143">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="a9b80-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="a9b80-144">Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgisini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="a9b80-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9b80-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9b80-145">Remarks</span></span>  
 <span data-ttu-id="a9b80-146">Bir hizmet tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmışsa, bu öğenin öznitelikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="a9b80-147">Bunlar `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, ve `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="a9b80-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="a9b80-148">Bir hizmet tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak için yapılandırılmışsa, oturum açma belirteçlerinin önbelleğe alınmasıyla ilgili ayarları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="a9b80-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="a9b80-149">Bunlar `cacheLogonTokenLifetime`, `cacheLogonTokens`, ve `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="a9b80-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b80-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9b80-150">See also</span></span>
- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
