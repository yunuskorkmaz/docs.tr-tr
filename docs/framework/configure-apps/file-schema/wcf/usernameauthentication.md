---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399183"
---
# <a name="usernameauthentication"></a><span data-ttu-id="c394b-101">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c394b-101">\<userNameAuthentication></span></span>
<span data-ttu-id="c394b-102">Hizmetin kimlik bilgilerini Kullanıcı adı ve parolaya göre belirtir.</span><span class="sxs-lookup"><span data-stu-id="c394b-102">Specifies a service's credentials based on user name and password.</span></span>  
  
<span data-ttu-id="c394b-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c394b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c394b-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c394b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c394b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c394b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c394b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c394b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c394b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c394b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c394b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c394b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="c394b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userNameAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="c394b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c394b-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c394b-110">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c394b-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c394b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c394b-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c394b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c394b-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c394b-113">Attributes</span></span>  
  
|<span data-ttu-id="c394b-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c394b-114">Attribute</span></span>|<span data-ttu-id="c394b-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c394b-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="c394b-116">Bir <xref:System.TimeSpan> belirtecin önbelleğe alındığı sürenin en uzun uzunluğunu belirten bir.</span><span class="sxs-lookup"><span data-stu-id="c394b-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="c394b-117">Varsayılan değer 00:15:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c394b-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="c394b-118">Oturum açma belirteçlerinin önbelleğe alınıp alınmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c394b-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="c394b-119">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c394b-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="c394b-120">Kullanılacak özel Kullanıcı adı parola Doğrulayıcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c394b-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="c394b-121">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="c394b-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="c394b-122">Windows gruplarının güvenlik bağlamına dahil edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c394b-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="c394b-123">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c394b-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="c394b-124">Bu özniteliğin olarak `true` ayarlanması, tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c394b-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="c394b-125">Bir kullanıcının ait olduğu `false` grupların listesini oluşturmanız gerekmiyorsa bu özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c394b-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="c394b-126">Önbelleğe eklenecek en fazla oturum açma belirteçleri sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c394b-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="c394b-127">Bu değer sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c394b-127">This value should be larger than zero.</span></span> <span data-ttu-id="c394b-128">Varsayılan değer 128 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c394b-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="c394b-129">Bir bağlamanın `username`özniteliği olarak ayarlandığında, Kullanıcı adı Windows hesaplarına eşlenir. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="c394b-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="c394b-130">İlgili parola doğrulama mekanizmasını sağlayan <xref:System.Web.Security.MembershipProvider> değerin adını içeren bir dize olan bu özniteliği kullanarak bu davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c394b-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="c394b-131">Kullanıcı adı parolasının doğrulanma şeklini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c394b-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="c394b-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c394b-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="c394b-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="c394b-133">-   Windows</span></span><br /><span data-ttu-id="c394b-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="c394b-134">-   MembershipProvider</span></span><br /><span data-ttu-id="c394b-135">-Özel</span><span class="sxs-lookup"><span data-stu-id="c394b-135">-   Custom</span></span><br /><br /> <span data-ttu-id="c394b-136">Varsayılan olarak Windows.</span><span class="sxs-lookup"><span data-stu-id="c394b-136">The default is Windows.</span></span> <span data-ttu-id="c394b-137">Bu öznitelik türü <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="c394b-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c394b-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c394b-138">Child Elements</span></span>  
 <span data-ttu-id="c394b-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="c394b-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c394b-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c394b-140">Parent Elements</span></span>  
  
|<span data-ttu-id="c394b-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="c394b-141">Element</span></span>|<span data-ttu-id="c394b-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c394b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c394b-143">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c394b-143">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="c394b-144">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c394b-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c394b-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c394b-145">Remarks</span></span>  
 <span data-ttu-id="c394b-146">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmamışsa, bu öğenin öznitelikleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c394b-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="c394b-147">Bunlar, `customUserNamePasswordValidatorType`, ve `membershipProviderName` `includeWindowsGroups` içerir`userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="c394b-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="c394b-148">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak üzere yapılandırılmamışsa, oturum açma belirteçlerini önbelleğe alma ile ilgili ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="c394b-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="c394b-149">Bunlar, ve `cacheLogonTokenLifetime` `cacheLogonTokens`içerir. `maxCacheLogonTokens`</span><span class="sxs-lookup"><span data-stu-id="c394b-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c394b-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c394b-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
