---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 05aa326c50823810caee5d6552af4d50424251dd
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274044"
---
# <a name="usernameauthentication"></a><span data-ttu-id="86948-101">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="86948-101">\<userNameAuthentication></span></span>
<span data-ttu-id="86948-102">Kullanıcı adı ve parolasına dayalı bir hizmetin kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86948-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="86948-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="86948-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="86948-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="86948-104">\<behaviors></span></span>  
<span data-ttu-id="86948-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="86948-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="86948-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="86948-106">\<behavior></span></span>  
<span data-ttu-id="86948-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="86948-107">\<serviceCredentials></span></span>  
<span data-ttu-id="86948-108">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="86948-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86948-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86948-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86948-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86948-110">Attributes and Elements</span></span>  
 <span data-ttu-id="86948-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86948-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86948-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86948-112">Attributes</span></span>  
  
|<span data-ttu-id="86948-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86948-113">Attribute</span></span>|<span data-ttu-id="86948-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86948-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="86948-115">A <xref:System.TimeSpan> bir belirteç önbelleğe alınma süresi en büyük uzunluğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="86948-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="86948-116">Varsayılan değer 00:15:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="86948-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="86948-117">Oturum açma belirteçlerinin önbelleğe yazılıp yazılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="86948-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="86948-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86948-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="86948-119">Kullanılacak özel kullanıcı adı parola Doğrulayıcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="86948-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="86948-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="86948-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="86948-121">Windows gruplarını güvenlik bağlamına dahil olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="86948-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="86948-122">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="86948-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="86948-123">Bu öznitelik ayarını `true` tam Grup genişletme içinde sonuçları gibi bir performans etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="86948-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="86948-124">Bu özellik kümesine `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcıya ait.</span><span class="sxs-lookup"><span data-stu-id="86948-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="86948-125">Oturum açma belirteçlerinin önbelleğe maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="86948-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="86948-126">Bu değer, sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86948-126">This value should be larger than zero.</span></span> <span data-ttu-id="86948-127">Varsayılan değer 128'dir.</span><span class="sxs-lookup"><span data-stu-id="86948-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="86948-128">Zaman `clientCredentialType` bağlama özniteliği `username`, kullanıcı adı Windows hesaplarına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="86948-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="86948-129">Bu öznitelik adını içeren bir dize kullanarak bu davranışı geçersiz kılabilirsiniz <xref:System.Web.Security.MembershipProvider> değer ilgili parola doğrulama mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="86948-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="86948-130">Kullanıcı adı şifrenin doğrulanacağı şekli belirtir.</span><span class="sxs-lookup"><span data-stu-id="86948-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="86948-131">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86948-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="86948-132">-   Windows</span><span class="sxs-lookup"><span data-stu-id="86948-132">-   Windows</span></span><br /><span data-ttu-id="86948-133">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="86948-133">-   MembershipProvider</span></span><br /><span data-ttu-id="86948-134">-Özel</span><span class="sxs-lookup"><span data-stu-id="86948-134">-   Custom</span></span><br /><br /> <span data-ttu-id="86948-135">Windows varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="86948-135">The default is Windows.</span></span> <span data-ttu-id="86948-136">Bu öznitelik türünde <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="86948-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86948-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86948-137">Child Elements</span></span>  
 <span data-ttu-id="86948-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="86948-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86948-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86948-139">Parent Elements</span></span>  
  
|<span data-ttu-id="86948-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="86948-140">Element</span></span>|<span data-ttu-id="86948-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86948-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86948-142">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="86948-142">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="86948-143">Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgisini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="86948-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86948-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86948-144">Remarks</span></span>  
 <span data-ttu-id="86948-145">Bir hizmet tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmışsa, bu öğenin öznitelikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="86948-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="86948-146">Bunlar `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, ve `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="86948-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="86948-147">Bir hizmet tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak için yapılandırılmışsa, oturum açma belirteçlerinin önbelleğe alınmasıyla ilgili ayarları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="86948-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="86948-148">Bunlar `cacheLogonTokenLifetime`, `cacheLogonTokens`, ve `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="86948-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86948-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86948-149">See also</span></span>
- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
