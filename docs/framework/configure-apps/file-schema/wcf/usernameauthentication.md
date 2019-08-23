---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 399158632d5c17a35ded02691ba35a231e6cdc6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940540"
---
# <a name="usernameauthentication"></a><span data-ttu-id="bbbeb-101">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bbbeb-101">\<userNameAuthentication></span></span>
<span data-ttu-id="bbbeb-102">Hizmetin kimlik bilgilerini Kullanıcı adı ve parolaya göre belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-102">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="bbbeb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bbbeb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bbbeb-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="bbbeb-104">\<behaviors></span></span>  
<span data-ttu-id="bbbeb-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bbbeb-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="bbbeb-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="bbbeb-106">\<behavior></span></span>  
<span data-ttu-id="bbbeb-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bbbeb-107">\<serviceCredentials></span></span>  
<span data-ttu-id="bbbeb-108">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="bbbeb-108">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbeb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbbeb-109">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbbeb-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbbeb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bbbeb-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbbeb-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbbeb-112">Attributes</span></span>  
  
|<span data-ttu-id="bbbeb-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bbbeb-113">Attribute</span></span>|<span data-ttu-id="bbbeb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbbeb-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="bbbeb-115">Bir <xref:System.TimeSpan> belirtecin önbelleğe alındığı sürenin en uzun uzunluğunu belirten bir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-115">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="bbbeb-116">Varsayılan değer 00:15:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-116">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="bbbeb-117">Oturum açma belirteçlerinin önbelleğe alınıp alınmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-117">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="bbbeb-118">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-118">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="bbbeb-119">Kullanılacak özel Kullanıcı adı parola Doğrulayıcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-119">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="bbbeb-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-120">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="bbbeb-121">Windows gruplarının güvenlik bağlamına dahil edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-121">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="bbbeb-122">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-122">The default is `true`.</span></span><br /><br /> <span data-ttu-id="bbbeb-123">Bu özniteliğin olarak `true` ayarlanması, tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-123">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="bbbeb-124">Bir kullanıcının ait olduğu `false` grupların listesini oluşturmanız gerekmiyorsa bu özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-124">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="bbbeb-125">Önbelleğe eklenecek en fazla oturum açma belirteçleri sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-125">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="bbbeb-126">Bu değer sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-126">This value should be larger than zero.</span></span> <span data-ttu-id="bbbeb-127">Varsayılan değer 128 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-127">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="bbbeb-128">Bir bağlamanın `username`özniteliği olarak ayarlandığında, Kullanıcı adı Windows hesaplarına eşlenir. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="bbbeb-128">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="bbbeb-129">İlgili parola doğrulama mekanizmasını sağlayan <xref:System.Web.Security.MembershipProvider> değerin adını içeren bir dize olan bu özniteliği kullanarak bu davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-129">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="bbbeb-130">Kullanıcı adı parolasının doğrulanma şeklini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-130">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="bbbeb-131">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bbbeb-131">Valid values are:</span></span><br /><br /> <span data-ttu-id="bbbeb-132">-Windows</span><span class="sxs-lookup"><span data-stu-id="bbbeb-132">-   Windows</span></span><br /><span data-ttu-id="bbbeb-133">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="bbbeb-133">-   MembershipProvider</span></span><br /><span data-ttu-id="bbbeb-134">-Özel</span><span class="sxs-lookup"><span data-stu-id="bbbeb-134">-   Custom</span></span><br /><br /> <span data-ttu-id="bbbeb-135">Varsayılan olarak Windows.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-135">The default is Windows.</span></span> <span data-ttu-id="bbbeb-136">Bu öznitelik türü <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-136">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbbeb-137">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbbeb-137">Child Elements</span></span>  
 <span data-ttu-id="bbbeb-138">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbbeb-139">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbbeb-139">Parent Elements</span></span>  
  
|<span data-ttu-id="bbbeb-140">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbbeb-140">Element</span></span>|<span data-ttu-id="bbbeb-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbbeb-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbbeb-142">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="bbbeb-142">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="bbbeb-143">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-143">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbbeb-144">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbbeb-144">Remarks</span></span>  
 <span data-ttu-id="bbbeb-145">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmamışsa, bu öğenin öznitelikleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-145">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="bbbeb-146">Bunlar, `customUserNamePasswordValidatorType`, ve `membershipProviderName` `includeWindowsGroups` içerir`userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-146">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="bbbeb-147">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak üzere yapılandırılmamışsa, oturum açma belirteçlerini önbelleğe alma ile ilgili ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-147">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="bbbeb-148">Bunlar, ve `cacheLogonTokenLifetime` `cacheLogonTokens`içerir. `maxCacheLogonTokens`</span><span class="sxs-lookup"><span data-stu-id="bbbeb-148">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbeb-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbbeb-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
